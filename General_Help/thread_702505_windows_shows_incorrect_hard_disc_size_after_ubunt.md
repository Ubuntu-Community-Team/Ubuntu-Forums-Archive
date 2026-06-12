---
title: "windows shows incorrect hard disc size after ubuntu install"
date: 2008-02-20
forum: General Help
---

### Post by trickytrickytricky on 2008-02-20
I may have already asked this, but if so then I can't find the post.

After installing ubuntu 7.04 onto slave hd when I open "my computer" in windows the size of the slave hd shows as only 5gb, which is the size of the partition I made to house ubuntu. The hd is actually 40gb. I have looked in disk/storage management and I can see a reference to the unknown partition which seems to correspond with the actual size of the disc. How can I get windows to show it correctly?

Another thing, after the ubuntu installation my windows date and clock were incorrect, by about 5 years! That has never happened before so are there any other surprises in store for me?

---

### Post by cdenley on 2008-02-20
Are you sure the capacity you're looking at isn't supposed to be the partition capacity? In windows, "drive c" refers to a partition, not a physical drive. The "disk management" utility is the only way I know of to get information about the physical drive in windows.

> Another thing, after the ubuntu installation my windows date and clock were incorrect, by about 5 years!
It sounds like your CMOS battery is dead, and you unplugged your computer. I think ubuntu has caused the time to be off a few hours for me before, but that's because some computers store UTC in their bios, some local time.

---

### Post by trickytrickytricky on 2008-02-20
thanks for the reply, yes it's showing drive F as my ubuntu partition and it's not showing the rest of the drive. Is it possible to make it show the rest as drive G or something, with the correct size.

I did notice in the bios setup that is said my cmos battery is low, I need to find out how to change it but I gather it's a simple task. 

I also need find out how to used my webcam on ubuntu, it will work with gq but I don't how to load that and set it up. I will probably have to start a new thread for that if I can't find  a similar one.

---

### Post by cdenley on 2008-02-20
Windows won't show a partition unless it can actually read it's filesystem. You can install a driver so it can read ext3 filesystems.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by trickytrickytricky on 2008-02-21
Thanks cdenley, this could be what I need. Although xp is reading the files on the whole hd, including those that were on the disc before I partitioned it and installed ubuntu.

---

