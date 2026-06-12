---
title: "Ubuntu -&gt; Ubuntu + XP = No GRUB = No Ubuntu"
date: 2007-03-03
forum: General Help
---

### Post by disco on 2007-03-03
Before I start explaining what I did, and what went wrong, here's a screenshot of my current partition setup (Should make my problem/solution easier)

[CENTER][IMG]http://img222.imageshack.us/img222/2558/gparted1ig7.png[/IMG][/CENTER]

Edit: Here's my fdisk -l output: 

[CENTER][IMG]http://img338.imageshack.us/img338/4432/fdisklud4.png[/IMG][/CENTER]

Explanation of the partitions:
[B]
sda1 = Apps/Videos etc.
sda2 = Music 

sdb1 = Ubuntu
sdb2 = Nothing? Extended partition
sdb3 = Windows XP
sdb4 = Non-existent? Where's it gone :/
sdb5 = Ubuntu swap partition
sdb6 = FAT32 Swap drive, for sharing between the two OSes
sdb7 = FAT32 Backup, where I store my XP image
sdb8 = XP NTFS Swap partition
[/B]

Here's my situation:

0. sdb was COMPLETELY formatted. I ran the Ubuntu install and it seperated it into two partitions, one for Ubuntu and one for the swap file

1. Ubuntu was installed, all worked well

2. I moved around, created and resized the partitions so they represented what's shown in the images above

** NOTE: Ubuntu worked perfectly at this point **

3. I installed Windows XP onto the correct partition(s)

- GRUB bootloader overwritten? I'm not too sure
- Boots into windows when **sda** is set to the boot disk (Which is what it has been for a while. I've got no idea WHY the XP bootloader was put onto this drive at all, but I think it's been like that for a while)

- At this point I could NOT get to GRUB/Ubuntu (Can't remember what the error message was exactly)

4. I booted the Ubuntu live cd, and tried sudo grub, root (hd0,0), setup (hd0), and all that. I tried many different combinations, but most of the time got a "Unable to mount partition" message.

5. I rebooted, with my boot drive set to **sdb** this time, and came to a GRUB screen, but when I selected Ubuntu to boot, I got a message about not being able to find anything at that location (Again can't remember the specifics)

6. Ran the Super GRUB CD, and told it to repair the MBR, and stick GRUB on it. I'm not sure how much actually happened there, it didn't look very convincing.

7. I rebooted (sdb as boot drive) and just got a message saying "GRUB Loading Stage 1.5". It hangs there forever, with no activity.

My current position:

- Can get to the XP Bootloader (Bootloader is shown because I have more than one entry in my boot.ini) which enables me to access my XP install by settings **sda** as the boot drive

- Can get to "GRUB Loading Stage 1.5" message by booting to **sdb**


Any suggestions or solutions enabling me to get to a working copy of GRUB that will let me boot to XP **OR** Ubuntu would be **very** much appreciated!

Thanks, disco

---

### Post by m.musashi on 2007-03-03
you usually want to install windows first as it will not play nice with any other OS. However, it can be fixed.

To avoid problems, grub should be on HD0. When you set sdb to boot (I'm assuming you did this via the BIOS) it became sda aka HD0. However, if it was sdb when you installed then grub is looking on sdbx (where x is the partition number for /) for the /boot/grub directory but no such directory exists on sdb because it's now sda.

I hope that's not a bunch of mumbo jumbo.

Anyway, I think the easiest way fix it is to set the HD containing grub to be HD0 and then using super grub disk to repair grub. You can also do this with the live CD but I'm not sure what the command is. You might want to check [this thread](http://ubuntuforums.org/showthread.php?t=224351).

Hope that helps. If not, post back.

EDIT: another option, if you are up for it, is to start over with a bit cleaner partitioning scheme. [This site](http://users.bigpond.net.au/hermanzone/) is a pretty good how to on dual booting. Check [here](http://www.psychocats.net/ubuntu/partitioning) for some tips on partition schemes.

One more thing. It doesn't help to have the XP swap on the same drive as XP as the head still has to move back and forth. If you want to speed up swapping in XP you should put the swap partition on a separate physical disk. You should probably put the XP backup image on a separate drive too. If the XP drive dies you want have access to the image either.

---

### Post by webofunni on 2007-03-03
grub stage1 resides in the mbr and grub stage2 in the another portion of hard disk. grub stage1.5 is an intermediate bt stage1 & 2 i think grub is unable to locate the stage2 .I think you need to upate your grub with current conditions to reflect

---

### Post by disco on 2007-03-05
Thanks for your replies people :)

I fixed it in the end by running the Super GRUB disk.

---

### Post by webofunni on 2007-03-05
disco are you using super grub for booting then are you able to boot the system directly without the disk

---

### Post by disco on 2007-03-05
No, I fixed the MBR using the disk, and now it works fine booting directly from the HD :)

---

