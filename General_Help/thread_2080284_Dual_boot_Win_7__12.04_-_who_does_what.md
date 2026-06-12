---
title: "Dual boot Win 7 / 12.04 - who does what?"
date: 2012-11-03
forum: General Help
---

### Post by Quarkrad on 2012-11-03
I've had some experience dual booting ubuntu with winxp - I normally install winxp first - then ubuntu and use burg as the boot manager.  Father-in-law has bought a new pc and wants win7 for his son and ubuntu 12.04 for himself.  I did my normal thing - as win 7 was pre installed I shunk the hd and installed 12.04 along side and used burg as the boot manager. Had a bit of a disaster - cloned the whole HD using Clonezilla on to a 2nd HD in the pc but when I tried the OSs win 7 was corrupt.  (I could not restore win 7 so it's another rebuild).  I could have been unlucky re the corruption but I did some reading re the dual boot and there seem to be two camps - using burg as I did or '..not touching burg/grub..'  and use EasyBCD. As I haven't used win 7 before I'm not sure if burg is OK or if I should use the EasyBCD boot loader.  What is the experience on this forum?

---

### Post by oldfred on 2012-11-03
It is my understanding that burg has not been maintained for a while.

With XP you could use gparted to shrink XP's NTFS partition. But with Vista or 7, better to use Windows to shrink its own partition with MMC and reboot several times before installing Ubuntu, so it can update its internals.

Some use EasyBCD.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
dual boot Windows 7 & Ubuntu 12.04 with EasyBCD

But most with Ubuntu just use grub2.

And how new? 
Some new systems are using UEFI which is a lot different than BIOS/MBR. Then you use an efi partition with both Windows efi loader and grub's efi loader in the efi partition.

Is this a two drive system. 
If two drives better to have Windows on first drive and Ubuntu on second drive.

---

### Post by Quarkrad on 2012-11-04
This machine uses  BIOS/MBR.  Although I have two HDs installed I use one of them for OSs/user data and the other as a backup as there is lot of user picture/music files and a single HD is a single point of failure hence, my reason to use the second HD as a backup device.   From what you say there looks to be no differene between using grub/burg or EasyBCD as the boot loader.

---

### Post by oldfred on 2012-11-04
While I still prefer to have an operating system on every drive and every drive separately bootable so when one fails I can still boot the other, you can leave the Windows boot loader in the system drive and put grub2's boot loader in the data drive still booting the Ubuntu on the system drive. Then set data drive as boot in BIOS. If issues with grub then you can still use the Windows boot loader to boot Windows. 

Always better to have grub in a MBR over a PBR. It really does not fit in a partition boot sector and use blocklists or hard coded addresses to the rest of grub. And change on the sytem to those files like a major update may break the boot and require a reinstall of grub to the PBR. So just be sure to have liveCD to reinstall grub2's boot loader is using EasyBCD. It will not be on every update, but only on major grub updates or a fsck that has to move a grub file.

I just use Ubuntu but use this logic.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by gordintoronto on 2012-11-04
I wrote about my experience, in Full Circle Magazine, issue 41, page 36. The net: I use Grub, and I've done several installations to test new versions or distros, and I've always used Grub, and it has never caused a problem.

---

### Post by RLDr on 2012-11-04
> **gordintoronto said:**
> I use Grub, and I've done several installations to test new versions or distros, and I've always used Grub, and it has never caused a problem.
Above quote is true for me also.

I first install Windows 7, then shrink/partition the drive/free portion respectively using windows disk management, then restart the system, log-in to Windows to final check the partitions, then again restart the system, then install Ubuntu through boot-able CD/pen-drive (I create root & swap partition manually). This process never caused to me any booting problem to Windows or Linux.

---

### Post by Quarkrad on 2012-11-07
Thank you all.  I did exactly what I did last time (and as per RisingMan) and it runs perfectly.  My first experience re Clonezilla was a one off - although this time I did not clone the whole disk!

---

### Post by Dn4mycrownj on 2012-11-07
i have had problems with using grub and windows 7

microsoft will not install service pack with grub  kinda crap in my op

i had to grab my windows 7 disk and reinstall the mbr from them to get the service pack to update then reinstall grub.

all other microsoft updates no prob just the service pack and grub didnt get along.

---

