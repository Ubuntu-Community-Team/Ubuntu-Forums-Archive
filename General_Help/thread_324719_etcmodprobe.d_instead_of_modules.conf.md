---
title: "/etc/modprobe.d instead of modules.conf????"
date: 2006-12-24
forum: General Help
---

### Post by albesan on 2006-12-24
"make devinodes # to create device inodes in /dev"


Now, when I run "make devinodes" I get this output:

sudo make devinodes
cd drivers ; make devinodes
make[1]: Entering directory `/home/alberto/dmx4linux-2.9-ba-061001/drivers'
./setup_devs install
cp: cannot stat `/etc/modules.conf': No such file or directory
./setup_devs: line 10: /etc/modules.conf.bak: No such file or directory
cp: cannot stat `/etc/modules.conf': No such file or directory
make[1]: Leaving directory `/home/alberto/dmx4linux-2.9-ba-061001/drivers'

So if I'm getting any of this it can not find "/etc/modules.conf".

I checked whether the file exists on my system and I get this:

locate modules.conf
/var/lib/dpkg/info/libpam-modules.conffiles
/var/lib/dpkg/info/perl-modules.conffiles
/etc/gnome-vfs-2.0/modules/ssl-modules.conf
/etc/gnome-vfs-2.0/modules/mapping-modules.conf
/etc/gnome-vfs-2.0/modules/default-modules.conf
/etc/modules.conf

So the directory path and file exists, does his happen much? What can I do about it?


Azz from this forum told me "Ubuntu uses /etc/modprobe.d instead of modules.conf"

now, how do ou work around this? any comments appreciated. Thanks


a.

---

### Post by albesan on 2006-12-26
bump.

---

