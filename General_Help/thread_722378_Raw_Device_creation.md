---
title: "Raw Device creation"
date: 2008-03-12
forum: General Help
---

### Post by Rotbert on 2008-03-12
Hi, I'm using Rawdevices on 7.04 Desktop and at the moment they will be activated manually by executing:

#! /bin/sh
modprobe raw
mkdir /dev/raw
mknod /dev/raw/raw0 c 162 1
mknod /dev/raw/raw1 c 162 2
mknod /dev/raw/raw2 c 162 3
mknod /dev/raw/raw3 c 162 4
ln -s /dev/rawctl /dev/raw/rawctl
raw /dev/raw/raw0 /dev/hdc1
raw /dev/raw/raw1 /dev/hdc2
raw /dev/raw/raw2 /dev/hdc3
raw /dev/raw/raw3 /dev/hdc4
chown admin:dba /dev/raw/raw0
chown admin:dba /dev/raw/raw1
chown admin:dba /dev/raw/raw2
chown admin:dba /dev/raw/raw3
chmod a+r /dev/rawctl

What do I have to enter into /etc/udev/rules.d to activate these raw devices during startup?
I found the /sbin/MAKEDEV script, does it help creating the /dev/raw/rawX entries or is this script now obsolete in Ubuntu - I never got it working?

---

### Post by psusi on 2008-03-12
The raw device driver is obsolete and should not be used.  It will be removed from future kernel versions.

---

