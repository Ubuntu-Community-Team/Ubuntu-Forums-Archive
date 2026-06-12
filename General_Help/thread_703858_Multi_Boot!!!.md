---
title: "Multi Boot!?!?!?"
date: 2008-02-21
forum: General Help
---

### Post by DoomBusterFX on 2008-02-21
Hi, i just have a complex question about multi boot with Linux Boot Loader (GRUB). I have Windows Vista Ultimate 64 bits on one HDD (750G Western digital Sata2) (THIS IS DISK 1) and Windows XP Home Edition on a other HDD (500G Western digital Sata2) (THIS IS DISK 2). I don't have any multi boot between this 2 OS. Now a have to reinstall Windows XP because he is corrupt and i don't wanna reinstall Wndows Vista because I have so much thing install that it will take a week to reinstall everything. If I reinstall windows XP and after I install Linux Ubuntu 7.10 on DISK 2, I know that I will get a multiboot with Ubuntu and Windows XP but what about Vista??. How can I have a multi boot with all three OS??? I tis possible without reinstalling all three OS?? 
 
Thanks and have a nice day!!!

---

### Post by ace007 on 2008-02-21
This can easily be done by editing the file menu.lst by typing the following at the terminal:

```
sudo gedit /boot/grub/menu.lst
```

Then you can scroll to the bottom and add the Vista installation.  When you add another entry it just has to be told to boot from the other HD.  If Vista is on the first hard drive the root should be defined as (hd0,0).  It is possible the drive is named a different name, but you wont know this until you install Ubuntu. hd0 is the first hard drive, and the second 0 is which partition, 0 means the first.  This should look like this (Dont quote me on this) just append it to the bottom of menu.lst:

```

title		Windows Vista
root		(hd0,0)
makeactive
chainloader	+1

```

If the Ubuntu and XP installations are on the second hard drive, they should appear near the bottom of this file as something like root (hd1,0) and (hd1,1).

Check out the forum for some help. menu.lst has some examples and instructions in it as well.

---

