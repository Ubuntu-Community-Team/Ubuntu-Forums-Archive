---
title: "missing munin &amp; munin-node packages"
date: 2014-11-17
forum: General Help
---

### Post by Moses_Moore on 2014-11-17
I can see that Munin is still a part of Ubuntu in 14.04
[http://packages.ubuntu.com/trusty/munin](http://packages.ubuntu.com/trusty/munin)
But when I search for munin in the repositories using apt-cache, I get
> Package munin is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source

Here's my sources.list:
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe
```

And I can still see other munin-related packages:
> $ apt-cache search munin
munin-doc - network-wide graphing framework (documentation)
munin-plugins-core - network-wide graphing framework (plugins for node)
munin-plugins-extra - network-wide graphing framework (user contributed plugins for node)
mailping - monitor email service availability and functioning
mumble-django - Mumble-Server web interface
munin-async - network-wide graphing framework (async master/client)
munin-libvirt-plugins - Munin plugins using libvirt
munin-plugins-java - network-wide graphing framework (java plugins for node)
munin-plugins-openstack - Plugins for Munin compatible monitoring OpenStack based systems
pmuninstall - script to uninstall modules installed from CPAN
virt-goodies - A collection of helpful virtualisation related tools

I'm stumped as to why munin & munin-node aren't appearing in the repositories, but 'munin-doc' and 'munin-plugins-core' are.  What else can I look into to solve this missing package problem?

---

### Post by Moses_Moore on 2014-11-17
Found it.  A four-year old file in /etc/apt/preferences.d/* was pinning the munin and munin-node packages to an older version.  Somehow this quietly removed these packages from any apt-get search results, making it look like there were holes in the repositories.

---

