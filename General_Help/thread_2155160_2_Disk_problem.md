---
title: "2 Disk problem"
date: 2013-06-17
forum: General Help
---

### Post by makamba on 2013-06-17
Hi,
The other day I got problems with bad sectors on my home drive. So I freed some partitions on my XP system and used the gparted CD to made them into one ext3 partition. 

However, I have 2 drives, an older and smaller drive and a newer bigger drive. And my bootmanager is on the bigger drive, and my system wants to boot from the smaller one. The big question is how to solve this?

TIA
Makamba

---

### Post by grahammechanical on 2013-06-17
> [COLOR=#000000] my system wants to boot from the smaller one[/COLOR]

Why does it want to do that? On which drive is Ubuntu installed? When we install Ubuntu it puts a boot loader (GRUB) into the MBR of the drive it is being install on. I also have two drives. I can select which drive to boot from in the Computer BIOS (Basic Input Output System). At the moment I am booting from the second drive (sdb) and using Grub in the MBR of the second drive to select from several versions of Ubuntu I have installed. I can use the BIOS to boot from the first drive (sda) and then Use Grub in the MBR of the first drive.

So, why is your machine booting from the smaller drive? Is it because this is the setting in the BIOS? Or is it because Ubuntu is installed on the smaller drive?

Regards.

---

### Post by makamba on 2013-06-17
> **grahammechanical said:**
> Why does it want to do that? .

That is possible the same question as asking after the meaning of life.

Ubuntu is installed on the bigger drive. I can only answer your question to the meaning of life with the observation that what is sda and what is sdb sometimes switch in my computer. 

> **grahammechanical said:**
> So, why is your machine booting from the smaller drive? Is it because  this is the setting in the BIOS? Or is it because Ubuntu is installed on  the smaller drive?
I don't know - AFAIK it is not a setting in my BIOS, but will check - Ubuntu is installed on the bigger drive, together with XP. The smaller drive is only data.

Edit:
I asked the original question from my mobile, now I'm after my computer which is currently running a life Ubuntu CD. Looking at the 'Ubuntu Explorer' (excuses for the misnomer) I can see the partitions I created. They seem to be okay. That led me to believe my problem is caused by my computer wanting to start from the small drive.

---

### Post by makamba on 2013-06-17
I rebooted my computer and am looking at my BIOS. I have
Primary IDE Master - Atapi CDROM
Primary IDE Slave - The small HD
Third IDE Master - The big HD

How can I move my big drive to become the primary Slave?

---

### Post by makamba on 2013-06-17
I thought I had found the solution in my BIOS. In the 'Advanced BIOS Features - Boot Settings Configuration - Hard Disk Drives' I changed the order of the HD's. but when I save and boot my system halts with
Error: no such partition
Grub rescue >

So, what's next?

---

### Post by oldfred on 2013-06-17
May be best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Generally main boot drive is primary master with the old IDE chain. Often the CD drive was secondary and may be master or slave.
Old IDE systems controlled primary & master by jumpers on drives and only primary master was bootable. Newer IDE systems use cable select and you can boot from other than the primary master. Drives are jumpered to cable select and how you connect to new 80 conductor IDE cable determines primary & slave.

      
 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

I once tried using a 40 conduction cable that came with CD on my hard drive in cable select. It does not work. :)

---

### Post by makamba on 2013-06-18
Well ...

I seem to have invented a few snags of my own. I tried to install Boot-Repair as instructed on the page if the first URL. I got a bunch of warnings of urls that where not available.  Next I downloaded the Boot-Repair CD, but could not burn it. Now I have to start all over again.

---

### Post by makamba on 2013-06-18
> **makamba said:**
> Next I downloaded the Boot-Repair CD, but could not burn it. Now I have to start all over again.

Ah, some more time later learned me that when I removed the Live CD to burn the CD Ubuntu Live CD lost its memory, could not find what it had to do, and kept on preparing, ad infinitum. This is what I had to do [http://ubuntuforums.org/showthread.php?t=1930926&highlight=burning+cd+preparing+burn](http://ubuntuforums.org/showthread.php?t=1930926&highlight=burning+cd+preparing+burn). So thanks to Lisiano I have to load the Live CD into memory to be able to burn a CD-R :frown:

---

### Post by makamba on 2013-06-18
> **oldfred said:**
> May be best to see details.

Well, after some struggling I can say that my BootInfoSummary can be found at [http://paste.ubuntu.com/5776879]("http://paste.ubuntu.com/5777038"). Looking at this file I can say that /dev/sda9, /dev/sda10 and /dev/sda11 have been merged using GParted. 

I tried using a Boot-repair-disk I finally managed to burn, but after the instruction
```
sudo chroot "/mnt/boot-sav/sda10" dpkg-configure -a
```
I got the message
```
dpkg: error2: unknown option -o
```
And that was AFAIK the end of my boot repair mission.

Edited because of security reasons.

---

### Post by mastablasta on 2013-06-18
or put the image on USB boot from it and then burn the CD.

though you should be able to repair grub from live CD.


boot order is indeed the one you were after in BIOS so you've seem to done that part correct. 

However it seems you installed grub in the wrong place, otherwise you wouldn't get the boot error i believe. grub can be repaired from live disk.: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

if you want a better suggestion then post the botoinfo script form boot repair tool.

---

### Post by mastablasta on 2013-06-18
grub should replace windows master boot loader on sda1 (use boot repair tool to do that)

---

### Post by makamba on 2013-06-18
> **mastablasta said:**
> However it seems you installed grub in the wrong place, otherwise you wouldn't get the boot error i believe. grub can be repaired from live disk.: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

if you want a better suggestion then post the botoinfo script form boot repair tool.

I could finally run the instructions from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) using a Life CD that was for Ubuntu 12.04. I was working with a Life CD for Ubuntu 10.04. And that explains many problems I had today. So, always use the newest Life CD.

The new BootInfo file is [http://paste.ubuntu.com/5777038/](http://paste.ubuntu.com/5777038/)

And now for the big finaly, trying to boot my system again.

---

### Post by makamba on 2013-06-18
I can boot my system again. At least half (Windows) is accessible. After start-up Ubuntu froze, sort-off, and I had to reboot again. But that might be caused by the bad sectors on my home drive.

---

