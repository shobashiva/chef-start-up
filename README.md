# Getting Started
This file is an attempt to document the installation process for tools used to interact with a chef server and resources it manages.

It assumes that you already have a code base that has its own git repository

It also assumes that you have a local settings template, usually named something like local_settings_dist.py.  This should have something a template that can be used to fill in database connection info for different development environments.  If you do not yet have one you should create one, and if you do have one, change it to look like the example below, adding entries for additional variables you might have

```
DATABASES = {
        'default': {
            'NAME': '<%= @config["DATABASE_NAME"] %>',
            'ENGINE': 'django.db.backends.postgresql_psycopg2',
            'HOST': '<%= @config["DATABASE_HOST"] %>',
            'USER': '<%= @config["DATABASE_USER"] %>',
            'PASSWORD': '<%= @config["DATABASE_PASSWORD"] %>',
            'PORT': '<%= @config["DATABASE_PORT"] %>',
        },
}

#ANOTHER_ENVIRONMENT_SPECIFIC_VARIABLE = <%= @config["ANOTHER_ENVIRONMENT_SPECIFIC_VARIABLE"] %>

```

## ChefDK
ChefDK includes several utilities for creating and managing chef resources.  It also provides tools to upload and download cookbooks to and from a chef server.  APAX has a chef server which stores cookbooks to be used by server nodes that it manages.  To get up and running, complete steps 1 - 5 of the [docs](https://docs.chef.io/install_dk.html).

## VirtualBox / Vagrant
When developing a cookbook, you'll want a fairly small feedback loop to test out changes.  VirtualBox and Vagrant will provide you with a virtual machine to provision using a cookbook.  You can download VirtualBox [here](https://www.virtualbox.org/wiki/Downloads) and Vagrant [here](https://www.vagrantup.com/downloads.html).

Once those are installed, install a couple of vagrant plugins:

```bash
vagrant plugin install vagrant-berkshelf
vagrant plugin install vagrant-omnibus
```

