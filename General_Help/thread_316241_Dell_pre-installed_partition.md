---
title: "Dell pre-installed partition"
date: 2006-12-10
forum: General Help
---

### Post by Zanwar000 on 2006-12-10
Dell preinstalls 2 extra partitions, one 4.64gb and another 70mb, for what I assume is for drivers. Should I keep these for the driver, unles they are for something else and install the drivers to my Windows partition everytime I install Windows?

Basically, I am asking if I should keep the two partitions Dell sends me with.

---

### Post by Iarwain ben-adar on 2006-12-10
Hi,
i have deleted these partitions, and have no particular need for them..

Alas, i only found out after that my MediaDirect buttons (on the front) won't work without the Dell partition (complete bs if you ask me).
Anyways, that's is Windows..

Feisty recognises every one of them!


Iarwain

---

### Post by bodhi.zazen on 2006-12-10
> **Zanwar000 said:**
> Dell preinstalls 2 extra partitions, one 4.64gb and another 70mb, for what I assume is for drivers. Should I keep these for the driver, unles they are for something else and install the drivers to my Windows partition everytime I install Windows?

Basically, I am asking if I should keep the two partitions Dell sends me with.

These two partitions are to restore windows.

If you want to remove windows go ahead and delete these as well. Otherwise you should keep them....

---

### Post by mayonaise15 on 2006-12-10
You may want to see if Dell sent you any CDs of your Windows OS.  A while back they started putting the re-install data on a separate partiton, so they quit sending Windows CD's.

If it is the case that one of those partitions has your Windows re-install stuff on it, you can still get rid of it.  You may just want to image the partiton first and burn it to a DVD or something.

---

### Post by Ramses de Norre on 2006-12-10
As you paid for windows after all I'd keep them, maybe on a dvd somewhere or so? It's a pity to throw something you paid for away and it might be handy sometimes..

---

### Post by yopnono on 2006-12-10
If you have the product key then you can download the windows cd from any torrent site, and it's legal. Since you have your legally purchased key.

Or order a replace cd from MS.

---

### Post by Zanwar000 on 2006-12-10
I've already installed Ubuntu, i resized all of the partitions except for the ones Dell made for me. It shouldn't have effected these though, right? I am asking because now when I enter my operating system Dell sent me all I get is a blank screen. However, Dell also sent me a Drivers and Diagnostics Disk, should I be okay or should I send for a new Windows disk?

---

### Post by mayonaise15 on 2006-12-10
The drivers and diagnostics disk won't be enough to re-install your OS.  You could order an OS CD from Dell.  I think they are $10 plus shipping and handling.

So after resizing your partitions you are not able to boot back into Windows?  Can you boot into safe mode?

---

### Post by Zanwar000 on 2006-12-10
EDIT
Okay, I have inserted a boot disk and "Fdisk /MBR" to remove GRUB. When I enter my OS disk now it says "Press any key to boot fom CD." but when I do my CD drive makes alot of noise and after awhile I get; "CDBOOT: Memory Overflow error
A kernel file is missing from the disk. Insert a system disk."
:( 

I am not able to boot into Windows because I reformatted the partition it was on, and then partitioned it to get an extended partition. I have a Drivers and Diagnostics Disk as well as an orange disk that read Operating System. Whenever I enter the operating system disk the disk drive is very noisy and is blank, when something does it come up it reads:

GRUB loading, please wait...
Error 22

This is probably because I installed GRUB with Ubuntu but because I have an Inspiron 1501 Ubuntu didn't recognize my hard drive so I had to reformat the drive that was on too. So currently I have no operating system on my computer; all I have are two partitions that Dell sent with one I assume being the Drivers partition. I have tried the operating system CD on my Acer laptop and it came up. I am booting from the CD on Inspiron it's just it doesn't come up. What is wrong here?

---

### Post by wool on 2006-12-10
> **Zanwar000 said:**
> EDIT
Okay, I have inserted a boot disk and "Fdisk /MBR" to remove GRUB. When I enter my OS disk now it says "Press any key to boot fom CD." but when I do my CD drive makes alot of noise and after awhile I get; "CDBOOT: Memory Overflow error
A kernel file is missing from the disk. Insert a system disk."
:( 

I am not able to boot into Windows because I reformatted the partition it was on, and then partitioned it to get an extended partition. I have a Drivers and Diagnostics Disk as well as an orange disk that read Operating System. Whenever I enter the operating system disk the disk drive is very noisy and is blank, when something does it come up it reads:

GRUB loading, please wait...
Error 22

This is probably because I installed GRUB with Ubuntu but because I have an Inspiron 1501 Ubuntu didn't recognize my hard drive so I had to reformat the drive that was on too. So currently I have no operating system on my computer; all I have are two partitions that Dell sent with one I assume being the Drivers partition. I have tried the operating system CD on my Acer laptop and it came up. I am booting from the CD on Inspiron it's just it doesn't come up. What is wrong here?

use this thread
[http://ubuntuforums.org/showthread.php?t=299929&page=3&highlight=dell+1501]("http://ubuntuforums.org/showthread.php?t=299929&page=3&highlight=dell+1501")
post#24

I got it by adding this boot param:
acpi=force irqpoll

edgy running on inspiron 1501

---

### Post by mikeymouse on 2006-12-10
If you did not get CD's with your system you can phone Dell and they will send them out to you.
I purchased a new pentium D930, it came with no cd's so I phoned them and they sent new ones out immediately.
 If you have the xp media centre on your system make sure you tell them so they will send out the proper CD's.
 Actually i formatted my system and made it fat32. I found when it was ntfs i could not put my backups on CD's or dvds..just wouldnt let me move the backups anywhere..
 Good luck
 mikeymouse

---

