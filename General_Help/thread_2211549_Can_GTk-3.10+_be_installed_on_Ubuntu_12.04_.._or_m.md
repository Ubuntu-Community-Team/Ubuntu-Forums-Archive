---
title: "Can GTk-3.10+ be installed on Ubuntu 12.04 .. or must I now upgrade to Ubuntu 14.04?"
date: 2014-03-16
forum: General Help
---

### Post by dragonfly41 on 2014-03-16
I have Ubuntu 12.04 LTS. Trying some Python app development.

Is it possible to upgrade Gtk-3.4.2 to Gtk-3.10?

I've read this .. [http://askubuntu.com/questions/277959/installing-gnome-3-8-on-ubuntu-12-04](http://askubuntu.com/questions/277959/installing-gnome-3-8-on-ubuntu-12-04)

But Gtk-3.10 seems to be targeted for Ubuntu 14.04 onwards.

This is my current installed version ...

[color=blue]
dpkg -s libgtk-3-0|grep '^Version'
Version: 3.4.2-0ubuntu0.6
[/color]

---

### Post by Yellow Pasque on 2014-03-16
It's probably technically possible, but gtk is such a fundamental library that it would involve upgrading tons of packages and the potential for package management breakage would be very high.

---

### Post by dragonfly41 on 2014-03-17
Thanks.

To continue my experiments with building Python/Gtk+ apps I've decided that I can either install Ubuntu 14.04 into a VirtualBox VM on Ubuntu 12.04 (my 3GB memory permitting) .. or into a separate partition.   Needs a bit of juggling of my dual boot partitions into triple boot (Windows / Ubuntu 12.04 / Ubuntu 14.04).  Or I can install Ubuntu 14.04 into an external USB drive which might be the easiest option.

But then .. will any Gtk+ apps which I develop in Ubuntu 14.04 not be backward compatible with Ubuntu 12.04 because of later Gtk+ dependencies?

I had thought (incorrectly it seems) that Ubuntu 12.04 LTS would give longer term (to 2017) support to newer versions of Gtk.

---

