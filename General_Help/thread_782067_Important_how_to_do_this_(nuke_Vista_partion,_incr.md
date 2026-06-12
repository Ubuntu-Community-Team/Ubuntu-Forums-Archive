---
title: "Important how to do this (nuke Vista partion, increase size of Ubuntu partition)"
date: 2008-05-04
forum: General Help
---

### Post by Linoman on 2008-05-04
Hey there, well I have Vista and Ubuntu both installed on my system in a dual boot setup. Same hard disk two different partitions. I want to do the following.

a) Delete the Vista Partition
b) With the free space increase the size of my Ubuntu partion


How do I do all of this, and if I do this will I damage my grub boot loader?

Did I mention to say that I really love Ubuntu 8.04 after tweaking it is an awesome system

---

### Post by tamoneya on 2008-05-04
you should install and run gparted```
sudo apt-get install gparted
gparted
```
From there delete the vista partition and resize the linux one.  Then you need to type ```
gksudo gedit /boot/grub/menu.lst
```This file controls the bootloader.  Go down to the bottom and comment out the entire part that talks about your vista OS.

---

### Post by ghost_ryder35 on 2008-05-04
boot into your live ubuntu cd  ********(HAVE TO DO THIS BECAUSE YOU CAN NOT RESIZE A MOUNTED PARTION)****
open gparted
delete the ntfs partiton
resize the partion you want to make bigger

---

### Post by forrestcupp on 2008-05-04
Use the [Gparted LiveCD](http://gparted-livecd.tuxfamily.org/) to delete your Vista partition and expand your Ubuntu partition.

Then go by [these instructions](http://ubuntuforums.org/showthread.php?t=224351) to restore GRUB.  When you delete Vista, it will change your partition numbering, but doing the restore of GRUB will take care of that.

Edit:
As always, I'm barely too late.  But if you use your Ubuntu Live CD to mess with your partitions, you'll have to unmount them first.

---

### Post by Linoman on 2008-05-04
Hey guys thanks for the respones, are you all sure that I will be able to get grub working again after I do this.. I do not want to reinstall Ubuntu

---

### Post by markharding557 on 2008-05-04
you could delete your vista partition and format to ext3 and use it as a second partition without altering the ubuntu patition at all

---

### Post by Linoman on 2008-05-05
Hey everyone, thank you all so much. I did it and my system works without a problem. I now have one big Ubuntu partition

---

