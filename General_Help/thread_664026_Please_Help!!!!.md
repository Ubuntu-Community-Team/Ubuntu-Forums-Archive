---
title: "Please Help!!!!"
date: 2008-01-10
forum: General Help
---

### Post by weaver2109 on 2008-01-10
I installed ubuntu awhile ago on my vista pc, and, due to lack of use, deleted the partition it was on and extended the vista partition to completely get rid of the Linux partition
so far so good..
i kept on working in vista and installed some updates, so i had to restart my computer
upon restarting, a screen came up saying

Loading GRUB, Please wait...
ERROR 22

then nothing else happened; it just froze:confused::mad::confused:
Can someone please tell me how to restore/access the vista bootloader and get rid of GRUB
any help would be appreciated please

---

### Post by Sef on 2008-01-10
> GRUB Error 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

From a previous [Catlett]("http://ubuntuforums.org/showthread.php?t=206262") post:

> You deleted grub when you deleted Ubuntu. Right now you do not have a boot loader to boot up XP. You can do 2 things. Reinstall Ubuntu or get a windows XP install disk. Boot to it. Select recovery mode by entering r at the first prompt.
It will take you through a quick dialogue eventually asking you which version of windows you want to use for the recovery. You only have 1 so enter 1 and it will give you a command line i.e. C:\
Enter this command there
Code:

fixmbr

This will rewrite the mbr with windows bootloader and you will be able to boot to XP like you did before ubuntu

---

### Post by weaver2109 on 2008-01-10
> **Sef said:**
> From a previous [Catlett]("http://ubuntuforums.org/showthread.php?t=206262") post:

i do not have a vista install disk
the only disk i have is the one that came with my laptop. if i install that, it will completely reformat my hard drive and reinstall vista to factory settings. i dont want to do that...is there an easier way?

---

### Post by arokicki on 2008-01-10
If you want to get linux back try to resize your drive and reinstall linux.
Try rescue cd from here [http://www.sysresccd.org/Download.en.php]("http://www.sysresccd.org/Download.en.php")
and run gparted from CD. This will allow you to resize you partition, to make room for Linux than reinstall linux.

---

### Post by Slayta on 2008-01-10
I'm having a similar problem where my ultimate goal is to install a small windowz partition on my ubuntu laptop and the last thing i remember doing was running a mandriva install dvd so i could use the disk partition program (by the way, im an uber noob here) and i don't remember it actually doing anything then its giving me that error. grub won't load and its giving me an error 22. Is it possible to save my system? i dont remeber doing any partitioning stuff.

---

