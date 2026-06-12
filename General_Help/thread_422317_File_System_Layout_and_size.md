---
title: "File System Layout and size"
date: 2007-04-25
forum: General Help
---

### Post by shri_nath on 2007-04-25
Hi,

I have downloaded the Ubuntu 7.04 desktop and the server editions to be installed on two separate computers.

The Desktop edition will go in the computer with two SATA disks (each 250 MB).

The Server version will go on the the computer with four SATA disks (each 250 MB).

I would like to know any recommendations about :

01. What kind of file system to use (ext3, JFS, etc)
02. What mount points (/usr, /home, swap, /opt, or some user defined etc.) should be there
03 What the sizes should be for those mount points

I would like to have following servers installed: DNS, Apache HTTP and Tomacat, Database (either MySQL or Postgresql), email (SMTP?)

Any help is appreciated.

Thank you.

  - shrinath

---

### Post by zvacet on 2007-04-25
1.ext3
2.root home swap you must have and other is optional
3.root size depends of what do you want to install and say in your case 15-20GB
swap is usually 2xRAM
size of other partitions depends what you want to store and save in

If you don´t like your partitioning you can allways use Gparted to resize in way it is best for you
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

