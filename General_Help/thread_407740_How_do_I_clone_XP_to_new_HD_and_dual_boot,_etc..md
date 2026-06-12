---
title: "How do I clone XP to new HD and dual boot, etc."
date: 2007-04-12
forum: General Help
---

### Post by bpont on 2007-04-12
I know I'm asking for a lot of info / advice on a variety of issues here, so many thanks in advance to any willing advisers!  :)

My nephew has an XP box with two HDs.  He's going to install a new 320 Gb to replace his 37 Gb master which XP resides on.  Therefore, I'm trying to accomplish the following using an Ubuntu Live CD (or Knoppix if the Ubuntu CD doesn't have all the tools I need):

* Image the XP install (including MBR) and save to his second (80 Gb) hard drive.  Could I accomplish this using ntfsclone and is this tool included in Ubuntu Live CD?

* Install new 320 Gb HD (I can handle this step)

* Boot up Ubuntu Live CD and use Gparted to create a 25 Gb partition to restore the XP image too  (his 37Gb HD is not full, so XP image should fit onto the new 25 Gb partition).  Will that also write the MBR or is that a separate step? (I don't really know if the system partition contains the MBR, but I'm guessing not.)  I will also split the remaining space on the new HD into 100 Gb partitions since I've heard XP can't defrag partitions that are too large.  I understand that I can also use Gparted to write NTFS filesystems to the newly created partitions.

* Use ntfsclone to restore the XP image to the newly created 25 Gb partition (and, if necessary, write MBR back to new HD)

* Reboot and ensure that XP starts up and works as before

* Boot Ubuntu Live CD and install Fiesty on his second 80 Gb HD.  I can handle this part, but want to be sure Grub plays well with XP.

Thanks again for any/all advice on how to accomplish these goals!

---

### Post by m.musashi on 2007-04-13
I'll try and provide some ideas for a few of your questions.
> **bpont said:**
> * Image the XP install (including MBR) and save to his second (80 Gb) hard drive.  Could I accomplish this using ntfsclone and is this tool included in Ubuntu Live CD?
I don't know about ntfsclone but new HDs often come with windows software that allow you to migrate to a new HD. I have a WD and their data lifeguard tools will move everything (including the MBR if I remember correctly). It is not 100% perfect. I noticed that I lost some settings but nothing overly important. If your drive didn't come with similar software you can download it from WD.

Sorry I'm not supporting FOSS but it might just be the easiest solution. I have heard of some FOSS/Linux tools for this but have no experience with them. Xen supposedly can create an image (like Norton Ghost) which you can restore but the one time I tried to use it I didn't have much luck. Anyone?

> * Boot up Ubuntu Live CD and use Gparted to create a 25 Gb partition to restore the XP image too  (his 37Gb HD is not full, so XP image should fit onto the new 25 Gb partition).  Will that also write the MBR or is that a separate step? (I don't really know if the system partition contains the MBR, but I'm guessing not.)  I will also split the remaining space on the new HD into 100 Gb partitions since I've heard XP can't defrag partitions that are too large.  I understand that I can also use Gparted to write NTFS filesystems to the newly created partitions.
I would do the gparted bit before the first step. Gparted will not write the MBR afaik but it can create an ntfs partition. I don't know if you need to split the remaining space. I think XP will be fine. In fact, unless you have a specific reason to partition your windows drive I would leave it. Windows seems to work best on just one drive. I partition mine because I use most of it for Linux. If you are using a separate drive for Ubuntu I might partition the XP drive and use part of it as a backup for Linux files and vice versa. That is what I do. That way, if one drive dies, anything important is backed up on the second. Just a thought.

> * Boot Ubuntu Live CD and install Fiesty on his second 80 Gb HD.  I can handle this part, but want to be sure Grub plays well with XP.
Yes, grub plays well with XP but if you are using two drives make sure the drive grub resides on is your 1st HD in the BIOS. Things can get goofy otherwise. Since you should install windows first, set the windows drive to be first and then install (or copy the image) and then either set the Ubuntu drive to be HD0 and install or be sure to install grub to HD0 when you install. If you don't, windows will boot and grub (being on the second drive) will never start. If you later change the 2nd drive to the 1st grub won't work without editing since your partition names will have changed.

> Thanks again for any/all advice on how to accomplish these goals!
You're welcome. I just hope I was helpful.

---

