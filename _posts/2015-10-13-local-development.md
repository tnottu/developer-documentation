---
date: 2015-10-13T14:26:53.000Z
layout: page
title: Local development
category: development
order: 3
published: true
---


## Start fresh project
You can start fresh project by cloning our WordPress template to your machine.

```bash
$ git clone https://github.com/Seravo/wordpress ~/Projects/new-wordpress-site
$ cd ~Projects/new-wordpress-site
$ vagrant up
```

### Alternative: start from repo on server

If you haven't already done so, initialise your repository on the server by logging in via ssh first and running `git init` first.

Example:

```bash
ssh my-site.wp-palvelu.fi -p <port>
cd /data/wordpress/
git config --global user.name "<Full Name>"
git config --global user.email <email>
git init && git commit -am "Initial commit"
```

Now you can just clone the remote git repository to your machine and start working.

```bash
$ git clone ssh://$SSH_USER@$SITE.wp-palvelu.fi:[$SSH_PORT]/data/wordpress ~/Projects/$SITE --origin production
```

### Tip: you can have multiple git remotes:
```bash
$ git remote add github git@github.com:ottok/example-site.git
$ git remote -v
github	git@github.com:ottok/example-site.git (fetch)
github	git@github.com:ottok/example-site.git (push)
production ssh://example@example.wp-palvelu.fi:12345/data/wordpress (fetch)
production ssh://example@example.wp-palvelu.fi:12345/data/wordpress (fetch)
upstream	https://github.com/Seravo/wordpress (fetch)
upstream	https://github.com/Seravo/wordpress (push)
```

## Copy your site from production with git

If you already have an instance in [WP-palvelu.fi](https://wp-palvelu.fi) you can use ```git``` to copy your site to local environment.

You need to use your unique credentials but for this example we are using following:

SSH Port | Username | Hostname
--- | --- | ---
*12345* | *example* | *example.wp-palvelu.fi*

Start by cloning your site to your home folder and running Vagrant:

```bash
# Clone the site to ~/Projects/example
$ git clone ssh://example@example.wp-palvelu.fi:12345/data/wordpress ~/Projects/example --origin production

# Go to your repository
$ cd ~/Projects/example

# Start vagrant and follow the questions from the installer
# It's safe to just push enter to all of them
$ vagrant up

# You can connect into vagrant
$ vagrant ssh

# You can pull the production database
$ wp-pull-production-db

# You can pull the production uploaded files
$ wp-pull-production-uploads
```

Now you can open in a browser http://wordpress.local/ and edit the files in you project and see the result immediately.
