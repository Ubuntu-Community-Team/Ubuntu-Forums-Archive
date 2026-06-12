---
title: "Hard disc health"
date: 2015-12-23
forum: General Help
---

### Post by alo12 on 2015-12-23
Hellow,

Is there any app or any command i can run on xubuntu in order to see if my hard disc needs replacement?

Thank you in advance

---

### Post by grahammechanical on 2015-12-23
On Ubuntu with Unity there is a utility called Disks that will let us run SMART data tests if the hard drive is compatible. There should be a similar utility in Xubuntu.

And then there is the fsck = file system check command.

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

We can run fsck from the recovery menu. At the Grub boot menu we select the Advanced options sub-menu and then select recovery mode and then from the recovery menu we select fsck - check all file systems. You might get some information that way.

Regards.

---

### Post by Bucky Ball on 2015-12-23
Yep, Disks is there in Xubuntu. Applications> Settings> Disks. You could start by checking the temperature of the drive(s). That gives some indication, particularly in a laptop, prior to running smart tests. The quick smart test will give you basic info. Dig deeper if there are problems.

---

### Post by slickymaster on 2015-12-23
> **Bucky Ball said:**
> Yep, Disks is there in Xubuntu. Applications> Settings> Disks. You could start by checking the temperature of the drive(s). That gives some indication, particularly in a laptop, prior to running smart tests. The quick smart test will give you basic info. Dig deeper if there are problems.

Sorry Bucky, but Xubuntu doesn't ship Disks by default```
~$ apt-cache show gnome-disk-utility
Package: gnome-disk-utility
Priority: optional
Section: admin
Installed-Size: 1204
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 3.10.0-1ubuntu3
Depends: libc6 (>= 2.10), libcairo2 (>= 1.2.4), libcanberra-gtk3-0 (>= 0.25), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.5.8), liblzma5 (>= 5.1.1alpha+20120614), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.18.0), libpangocairo-1.0-0 (>= 1.14.0), libpwquality1 (>= 1.1.0), libsecret-1-0 (>= 0.7), libsystemd-login0 (>= 31), libudisks2-0 (>= 2.1.1), dconf-gsettings-backend | gsettings-backend, udisks2 (>= 2.1.1), gnome-icon-theme-symbolic
Filename: pool/main/g/gnome-disk-utility/gnome-disk-utility_3.10.0-1ubuntu3_i386.deb
Size: 212058
MD5sum: d0993dc7d1a37a75e794afcd50320c69
SHA1: b9d52a7830584c187fe58a232645962cc38661a0
SHA256: ae75f4bce5ae09d63d0f9fc0b83b1503486a9494dcc3970f39820b90f8a40139
Description-en: manage and configure disk drives and media
 GNOME Disks is a tool to manage disk drives and media:
 .
  * Format and partition drives.
  * Mount and unmount partitions.
  * Query S.M.A.R.T. attributes.
 .
 It utilizes udisks.
Description-md5: 8bbfe121f73fcddf9e0a9c15f0e8afd8
Homepage: http://git.gnome.org/cgit/gnome-disk-utility/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
**[COLOR=#ff0000]Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, lubuntu-desktop, ubuntu-gnome-desktop[/COLOR]**
```In all cases OP can install it, it's just a matter of running```
sudo apt-get install gnome-disk-utility
```

---

### Post by oldos2er on 2015-12-23
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by pqwoerituytrueiwoq on 2015-12-23
i use [gnome-disks](apt:gnome-disk-utility) and [gsmartcontrol](apt:gsmartcontrol)

---

### Post by Bucky Ball on 2015-12-23
> **slickymaster said:**
> Sorry Bucky, but Xubuntu doesn't ship Disks by default ...

Ah ha. Thanks for that. Sorry all. My mistake. I'm running a bit of a hybrid with xfce4 so must have installed it myself at some stage. :| :)

---

