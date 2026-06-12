---
title: "Partition Problem"
date: 2006-12-14
forum: General Help
---

### Post by kainino on 2006-12-14
I have an extra unpartitioned 2.7GB on my hard disk and I want to use it, for Ubuntu or just storage. When I partition the space with either the installer or GPartEd, in NTFS, EXT3, or LINUX-SWAP (under an Edgy [COLOR="Red"]*[/COLOR]Desktop CD), Windows XP seems to boot normally for a few seconds, then says (BSoD):

```

A problem has been detected and Windows has been shut down to prevent damage to your computer.
UNMOUNTABLE_BOOT_VOLUME
(blah blah blah...)
Technical information:
*** STOP: 0x000000ED (0x87282E30, 0xC000014F, 0x00000000, 0x00000000)

```

When I get rid of the partition, it works again. Does this have something to do with the BOOT.INI settings in msconfig? There seems to be a line that says where Windows is installed. (By the way, if I install Ubuntu, will I have to manually add it to the list of OSs?) When I boot in safe mode, it shows all the drivers loading, with the partition ID at the beginning. It also boots normally from hibernate, so it must be something later on in the startup.

```

BOOT.INI:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by kainino on 2006-12-15
eh... bump?

---

### Post by wpshooter on 2006-12-15
Why are you trying to partition the space as NTFS ?  I don't think Ubuntu can be installed on an NTFS partition.

In the first place, I don't think you really have enough space to properly install and run Ubuntu.  It may possibly install and work in 2.7gb of space but that would be too little for my taste.

And then if you want to install Ubuntu why are you not just booting to the Ubuntu DESKTOP installation CD and then running the installer icon on the desktop and let the Ubuntu installer perform the installation including the partitioning of your open hard drive space ?

Partitiioning for Ubuntu should be on this wise:

/ - for root file system - ext3 filesystem type
/home - home partition - ext3 filesystem type
/linux swap - for Ubuntu/linux swap - linux swap parition type

Perhaps you should try this on another separate computer first before you wind up damaging your M/S windows installation.

Good luck.

---

### Post by patrick.dylan on 2006-12-15
Definitely don't try to install Ubuntu on a 2.7GB partition. You'll eat up most of that with the default installation, IIRC.

---

### Post by OBnascar on 2006-12-15
Something just does not sound right what you are explaining after you format that 2.7GB partition. I have resized a Windows partition many times with Gparted and have never had a problem.

I am assuming your Windows partition is NTFS ?

I would just delete that 2.7GB partition you have so that you only have one partition. Then I would resize your Windows partition using Gparted and use what you have chose to have left over on a second partition for you storage. Everything should run just fine........

---

### Post by kainino on 2006-12-17
> **wpshooter said:**
> Why are you trying to partition the space as NTFS ?  I don't think Ubuntu can be installed on an NTFS partition.


I tried NTFS because it is be compatible with Windows; I knew that 2.7GB would be a little small for Ubuntu. I was thinking that *maybe* I could run Ubuntu, but store all my files new files in the Windows partition.

> **wpshooter said:**
> And then if you want to install Ubuntu why are you not just booting to the Ubuntu DESKTOP installation CD and then running the installer icon on the desktop and let the Ubuntu installer perform the installation including the partitioning of your open hard drive space ?

Sorry, I meant Desktop CD. I have tried letting the installer do it automatically, in fact I did that the first time, and I got a bit freaked out the first time when I did it.

> **OBnascar said:**
> I would just delete that 2.7GB partition you have so that you only have one partition. Then I would resize your Windows partition using Gparted and use what you have chose to have left over on a second partition for you storage. Everything should run just fine........

I already deleted the 2.7GB partition, because I needed to boot Windows. I already have 27.6GB of stuff on that partition and it is only 34.5GB, and I will probably still use Windows often, so I'll still need space. I'm (probably for no reason) really paranoid about breaking anything on my main partition, so I haven't tried changing it yet. Will Windows have problems if I change it's size?

---

