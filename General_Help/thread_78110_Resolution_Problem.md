---
title: "Resolution Problem"
date: 2005-10-17
forum: General Help
---

### Post by redbull on 2005-10-17
I was running Hoary and decided to start fresh with Breezy. Now the resolution is 640x480 and I can't change it under preferences? It worked fine with 5.04, so what's changed? (I'm being forced to use Win XP right now, so please help!)

---

### Post by aysiu on 2005-10-17
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by dbott67 on 2005-10-17
My xorg.conf file got hosed during installation as well.  Fortunately, the same thing happened when I upgraded from Warty to Hoary, so I took the precaution of backing up all my config files:
- video (/etc/X11/xorg.conf)
- network (/etc/network/interfaces)
(as well as sound & modules)

Anyhow, that's probably of no help now, so you have a couple of options:
1. Search the forums for similar video card & monitor and check their xorg.conf file.
2. Download the Hoary "Live CD" and boot into it.  If the resolution is okay (it should be if it was when you originally installed Hoary to your hard disk) and make a copy of the xorg.conf file to floppy or usb drive (or just print it out/write it down/whatever).  Then, boot into your installed version of Breezy and copy over the existing xorg.conf file.

3. The really, really (really) long way: install Hoary, make a backup of all config files to floppy or usb drive, then re-install Breezy and copy the Hoary config files into Breezy.

-Dave

---

