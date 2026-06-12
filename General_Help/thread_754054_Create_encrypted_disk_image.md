---
title: "Create encrypted disk image"
date: 2008-04-13
forum: General Help
---

### Post by DrQuincy on 2008-04-13
In OS X you can create a mountable 128 or 256 bit encrypted disk image and mount it like an other .dmg file. Is there a native way in Ubuntu to do this? So you double-click it, enter a password and it mounts it. Is this possible?

---

### Post by eaglestrike7339 on 2008-04-13
I would look into truecrypt for linux. It allows you to make a container file, alot like a disk image, with a defined size that is encrypted, then can be decryted at will and mounted as a system disk. 

This sounds like it would suit your needs, and to find out how to install it google "truecrypt ubuntu" and you should be able to find a good tutorial

---

### Post by RTrev on 2008-04-13
TrueCrypt suggestion seconded.  I hear incredibly good things about this program, and have to try it myself soon.

---

### Post by Drew10th on 2008-04-13
I found this link with a quick google search, don't know if it will help you.

[http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-04-61312.shtml)

---

### Post by TheWizzard on 2008-04-13
truecrypt is definitally the best! 
and it works on linux, windows and osx.

---

### Post by eaglestrike7339 on 2008-04-13
> **TheWizzard said:**
> truecrypt is definitally the best! 
and it works on linux, windows and osx.

hey theWizzard, i wonder....do you know if the volumes themselves are compatble? say, if i have a triple boot computer (Xp, ubuntu, OSx86), would they all be able to read that volume?


srry for little bit of thread hijacking, but this is definitely not worth a thread on it's own

---

### Post by panayk on 2008-04-13
You can also try [encfs]("http://www.arg0.net/encfs"): [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
I haven't tried any of the other methods, but this has the advantage that you are not limited to a predefined filesystem size.
You can also roll your own GUI: [http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_GNOME_and_Zenity](http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_GNOME_and_Zenity)

---

### Post by update_manager on 2008-04-13
> **panayk said:**
> You can also try [encfs]("http://www.arg0.net/encfs"): [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
I haven't tried any of the other methods, but this has the advantage that you are not limited to a predefined filesystem size.
You can also roll your own GUI: [http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_GNOME_and_Zenity](http://gentoo-wiki.com/TIP_EncFS#Using_encFS_with_GNOME_and_Zenity)

There is a GUI (in 8.04 it is apt-get able.
[http://www.getdeb.net/release.php?id=1371]("http://www.getdeb.net/release.php?id=1371")

---

### Post by TheWizzard on 2008-04-14
> **eaglestrike7339 said:**
> hey theWizzard, i wonder....do you know if the volumes themselves are compatble? say, if i have a triple boot computer (Xp, ubuntu, OSx86), would they all be able to read that volume?


srry for little bit of thread hijacking, but this is definitely not worth a thread on it's own

yes, i have an USB-stick encrypted with truecrypt and i use it between winows and different linux pc's.

---

### Post by xaenyx on 2008-04-14
Truecrypt interfaces with the linux kernel itself I believe, as does the windows version.  This means that it will only work with linux and windows unless a third party gets the source and rewrites much of it.  It does not work in freebsd or os x (unless it's changed in the last few months).

---

### Post by TheWizzard on 2008-04-14
> **xaenyx said:**
> Truecrypt interfaces with the linux kernel itself I believe, as does the windows version.  This means that it will only work with linux and windows unless a third party gets the source and rewrites much of it.  It does not work in freebsd or os x (unless it's changed in the last few months).

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

### Post by panayk on 2008-04-14
> **update_manager said:**
> There is a GUI (in 8.04 it is apt-get able.
[http://www.getdeb.net/release.php?id=1371]("http://www.getdeb.net/release.php?id=1371")

That's nice to know, thanks!

---

