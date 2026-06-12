---
title: "Flash drive managemant"
date: 2007-06-04
forum: General Help
---

### Post by stchman on 2007-06-04
Ok, I need to know a few things about flash drive management.

1.  Can you remove the U3 cr@p under linux?
2.  Can you delete the partitions and repartition the flash drive using gparted?
3.  It seems that when I try to format either a flash drive or external hard drive using gparted using FAT32 I get errors.
4.  How do you give a flash drive a new label?

Windows XP disc manager is the only way I can easily manage flash drives and do FAT32 stuff.  Yes I need FAT32 as both Linux and XP can read/write to them without difficulty.

---

### Post by defishguy on 2007-06-04
You can remove U3.  I've never used it myself but the information is at [http://www.u3.com/uninstall/]("http://www.u3.com/uninstall/")

You should be able to use GParted for any writeable media.

In fact GParted can take care of the formatting and disk labeling too.  The disk label is set from the gparted device menu.

Good luck, I hope this helps.

---

### Post by stchman on 2007-06-06
> **defishguy said:**
> You can remove U3.  I've never used it myself but the information is at [http://www.u3.com/uninstall/]("http://www.u3.com/uninstall/")

You should be able to use GParted for any writeable media.

In fact GParted can take care of the formatting and disk labeling too.  The disk label is set from the gparted device menu.

Good luck, I hope this helps.

I know how to remove U3 under Windows, I was wanting to know how to do it under Linux.  The u3 uninstall does not work using WINE.

I tried doing flash drive maintenance with gparted, but it does not want to deal with FAT32 very well.

How do you rename a disc using gparted?

---

### Post by steeleyuk on 2007-06-06
I was under the impression that U3 was simply an EXE (plus folders) and autorun file. You should just be able to delete anything relating to U3 rather than using an uninstaller.

---

### Post by mcduck on 2007-06-06
Remember to unmount your disk before trying to edit it with gParted ;)

Actually you might want to turn off automounting when you are doing that kind of things. (System/Preferences/Removable Drives and Media)

---

### Post by LaRoza on 2007-06-06
U3, the bane of flash drives. I was unable to use the U3 uninstaller on Vista or Linux, I needed to find a computer with XP and use it with Admin rights.

You might be able to erase U3 with GParted, but formatting doesn't get rid of it, I believe it is on a separate partition, which you would need to delete.

---

### Post by steeleyuk on 2007-06-06
If there are two partitions on the flash drive then GParted should show both and allow you to merge them if you want.

---

### Post by stchman on 2007-06-06
> **steeleyuk said:**
> If there are two partitions on the flash drive then GParted should show both and allow you to merge them if you want.

I still don't know what the function of U3 is?  A flash drive is supposed to be a place to store files for transport.  I gather that there are companies that will put trial software on the flash drive.  This probably generates revenue for the makers of the flash drive.  If that is the case then I would just want to be able to uninstall it.  Sponsors like that keep flash drives cheap.

No one has talked about gparted inability to format a flash drive in FAT32.

---

### Post by stchman on 2007-06-07
Update:

I was able to do flash drive maintenance.  If you go to the Removable media section under Preferences and turn off the auto mounting you can go to gparted and do your duties.

I was able to format a flash drive in FAT32 no problem.  Just another tip to document.

---

