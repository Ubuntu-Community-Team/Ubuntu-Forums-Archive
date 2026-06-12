---
title: "Errors on dist-upgrade"
date: 2006-11-06
forum: General Help
---

### Post by evilmercer on 2006-11-06
In my attempts to upgrade it when im doing a dist-upgrade I get the following


Setting up dbus (0.93-0ubuntu3) ...
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on dbus (>= 0.90); however:
  Package dbus is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.0); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.17-10-386 (2.6.17-10.33) ...
Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version 
2.6.17-10-386 on running kernel 2.6.17-10-386 in /usr/sbin/mkinitramfs
dpkg: error processing linux-image-2.6.17-10-386 (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.17-10-386; however:
  Package linux-image-2.6.17-10-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 libgnomevfs2-0
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 linux-image-2.6.17-10-386
 linux-image-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant seem to find any cause or fix for this problem.

---

### Post by taurus on 2006-11-06
What does your /etc/apt/sources.list look like?

```
more /etc/apt/sources.list
```

---

### Post by evilmercer on 2006-11-06
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy aiglx
#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy main



##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb [http://thomas.enix.org/pub/debian/packages/](http://thomas.enix.org/pub/debian/packages/) edgyy main

---

### Post by Sef on 2006-11-07
Just checking, but before doing ```
sudo apt-get dist-upgrade
```  did you do ```
sudo apt-get update
```?

---

### Post by evilmercer on 2006-11-07
yes I have done that, and there are no updates available.

---

### Post by evilmercer on 2006-11-08
ttt

---

### Post by Evil on 2006-11-16
I got exactly the same errors while updating the 32-bit ubuntu chroot on my 64-bit Kubuntu system tonight.  :\

---

### Post by Evil on 2006-11-17
I've also noticed that when I 'dchroot -d' into my chroot, the 'ps -A' command produces no output.  Does that sound familiar to anyone?  It's like the terminal/shell isn't working right.

---

