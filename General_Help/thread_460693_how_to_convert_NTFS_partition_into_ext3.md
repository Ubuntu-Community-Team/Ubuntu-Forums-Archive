---
title: "how to convert NTFS partition into ext3?"
date: 2007-05-31
forum: General Help
---

### Post by chunchengch on 2007-05-31
I am using ntfs-3g to access a 26GB NTFS partition where I store my personal datas, now for the sake of security and performance, I would like to make a new ext3 partition from this 26GB NTFS partition, I used partition magic to do this in Windows while I don't know which tool is available in Linux?  thanks!

---

### Post by confused57 on 2007-05-31
The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Here's an excellent guide for mounting your new ext3 partition:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by chunchengch on 2007-06-01
confused57,

Thanks a lot!

I downlaoded and extracted gparted-0.3.3.tar.bz2, while when I type **make** and **sudo make install**, it did not work, I did confuse?! 


here is the message

Desktop$ **ls**
**gparted-0.3.3  gparted-0.3.3.tar.bz2**
Desktop$ cd gparted-0.3.3
Desktop/gparted-0.3.3$ **ls**
[B]aclocal.m4    config.sub       gparted.desktop.in   intltool-update.in  NEWS
AUTHORS       configure        include              ltmain.sh           pixmaps
ChangeLog     configure.in     INSTALL              Makefile.am         po
compose       COPYING          install-sh           Makefile.in         README
config.guess  depcomp          intltool-extract.in  missing             src
config.h.in   gparted.desktop  intltool-merge.in    mkinstalldirs[/B]
Desktop/gparted-0.3.3$ **make**
[COLOR="Red"]make: *** No targets specified and no makefile found.  Stop.[/COLOR]
Desktop/gparted-0.3.3$ **sudo make install**
[COLOR="Red"]make: *** No rule to make target `install'.  Stop.[/COLOR]
Desktop/gparted-0.3.3$

---

### Post by jimbob on 2007-06-01
I think all you had to do was apt-get install gparted.

If you want the stand-alone live Gparted CD download and burn the iso from here:
  
    [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

