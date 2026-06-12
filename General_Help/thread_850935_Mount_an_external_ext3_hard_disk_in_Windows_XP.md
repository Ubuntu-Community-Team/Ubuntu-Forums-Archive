---
title: "Mount an external ext3 hard disk in Windows XP"
date: 2008-07-06
forum: General Help
---

### Post by Tryfon on 2008-07-06
Hi! I have Ubuntu 8.04 installed, which I mainly use, therefore my external 500GB HD is ext3 formatted. But occasionally I need to access it (read/write) from Windows XP. Do you know a way to do that? I have installed Ext2 IFS which is great, but only mounts the Ext3 partition in which I have the Linux installed. Any idea?

---

### Post by Linux&amp;Gsus on 2008-07-06
I have never tried something like that before myself. But I have 2 links for you that might be of some help for you.
[http://www.diskinternals.com/linux-reader]("http://www.diskinternals.com/linux-reader/") - read only
[http://sourceforge.net/projects/ext2fsd]("http://http://sourceforge.net/projects/ext2fsd") - read/write from my understanding

---

### Post by PGScooter on 2008-08-15
I do not like the diskinternals one.

I am using Ext2IFS_1_11.exe (which I think might be the second link of Linux&Gsus) which works great. You see and use the drive just like any other!

---

### Post by unutbu on 2008-08-15
If the above link does not work, try [http://www.fs-driver.org/](http://www.fs-driver.org/).
According to the FAQ: Ext2IFS has:> 
Complete reading and writing access to files and directories of volumes with the Ext2 or Ext3 file system.

---

