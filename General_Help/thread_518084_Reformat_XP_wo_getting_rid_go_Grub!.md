---
title: "Reformat XP w/o getting rid go Grub!"
date: 2007-08-05
forum: General Help
---

### Post by kris2pe on 2007-08-05
I have to partition on xp & an ubuntu partition
The problem is that when I restart xp I will mostly like remove ubuntu's Grub!
So how do I go about this?
Remember Noob here need step by step process!

---

### Post by bernied on 2007-08-05
> **kris2pe said:**
> I have to partition on xp & an ubuntu partition
The problem is that when I restart xp I will mostly like remove ubuntu's Grub!
So how do I go about this?
Remember Noob here need step by step process!
Restarting XP will not get rid of grub.

Are you talking about reinstalling XP?
If you are talking about reinstalling, then windows will reinstate the master boot record (mbr), which is the first 512 bytes (like letters) of the disk. This is currently the grub mbr, but windows has its own mbr, which only boots windows. When you reinstall windows it replaces the grub mbr with the windows mbr.

So you only have to reinstall the grub mbr. Not all of grub, not all of ubuntu.

There are many ways to do this. I recommend you get the super grub disk, and learn how to use it, before you reinstall windows. It is also a good idea to have a linux live cd handy, and to know that you can connect to the internet with it. Once on the web, you can solve most things.

Here is a useful link:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bruce2000 on 2007-08-05
You're intending to reinstall XP but want to keep Grub?

I did this during the week, and found some helpful advice in the Official Ubuntu book - It shows you how to backup and restore your MBR.

```

Backing Up and Restoring Your Boot Sector
When GRUB runs, the boot sector part of your hard disk contains information about which OS you can boot. This sector sometimes gets corrupted due to a system crash or power loss and your computer won't boot. Luckily, with a few carefully chosen commands, you can back up and restore this important sector.
Back it up using this command:

foo@bar:~$ sudo dd if=/dev/hda of=MBR-backup bs=512 count=1

The dd command copies the sector from the first disk (/dev/hda-change this to your disk) and saves it as MBR-backup in the current directory.
Quick Tip
When referring to boot sectors you may see it prefixed as MBR-this is short for master boot record.
To restore the sector, run this command:

foo@bar:~$ sudo dd if=MBR-backup of=/dev/hda bs=512 count=1 


```


This worked like a charm for me.

---

