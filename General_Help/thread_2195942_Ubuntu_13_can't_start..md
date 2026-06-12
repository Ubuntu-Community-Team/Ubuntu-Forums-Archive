---
title: "Ubuntu 13 can't start."
date: 2013-12-27
forum: General Help
---

### Post by tarciovini on 2013-12-27
Hi, some days ago I tried to install manually the GLib 2.36.4, to do that used the standard procedure:

$ ./configure
$ make
# make install

Done it my system started to present problems so I restarted it. So when it was starting the Ubuntu's logo appeared normally, but then, it stopped on a black screen with a blinking underscore and it didn't start anymore. I have tried some things like memtest (it didn't find out any error), fsck and I tried to log in as root. What's more weird is that my directory didn't appear in the directory home. I'm worried about it because I didn't make any backup.

---

### Post by Impavidus on 2013-12-27
Installing a new version of glib on a production machine without backups sounds a bit dangerous. glib is used by so many important programs that an incompatible version can easely break your system. I think it should be possible to install two versions side-by-side.

I understand you can no longer boot. Maybe you can boot from a live disk, chroot into your installation on the hard drive and use the package manager to properly reinstall the version of glib that came with your Ubuntu release.

Do you have a separate /home partition? If so, the /home directory will appear empty when using the recovery console or a live disk unless you manually mount your /home partition there. It should still exist, I don't think you lost your data.

---

### Post by tarciovini on 2013-12-27
I got a live cd into my system and I can see my root directories.
But how exactly I use the chroot to install the glib from a live cd to other machine? Sorry for it, I'm not an expert...

---

