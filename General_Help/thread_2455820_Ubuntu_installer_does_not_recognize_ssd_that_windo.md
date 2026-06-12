---
title: "Ubuntu installer does not recognize ssd that windows 10 is on - want to dual boot"
date: 2020-12-28
forum: General Help
---

### Post by jaredbuck on 2020-12-28
Hi all -

I'm trying to install Ubuntu onto an internal platter based hard drive while keeping windows 10 on the internal ssd so I can dual boot.  The problem I'm having is the Ubuntu installer will not recognize the SSD AT ALL - I think it needs to do that in order to recognize that Windows is installed and thus give me the option to dual boot? I can mount the ssd just fine on the live session, but even after I do that it still won't recognize the ssd for dual booting purposes.  My computer is set to boot windows in uefi mode - and the live session apparently does that too.

Could use some help/advice here.

Jared

---

### Post by dragonfly41 on 2020-12-28
Since you are starting from a Windows 10 environment I suggest using Rufus (in Windows) to create the Ubuntu USB installer in a flash drive. All in UEFI mode.
Then you should be in a position to use the Rufus created installer.
I would then prepare your dual boot SSD using GParted to prepare partitions in advance. My first partition in ext SSD is 500MB, fat32, boot flags set. This allows me to boot up SSD independent of Windows 10 
For example I have Windows 10 (OEM) on an internal HDD. Then a USB 3.0 connected SSD runs external Ubuntu 20.04.
I have my SSD's in a USB docking bay.

---

### Post by CelticWarrior on 2020-12-28
1. Disable Fast Startup in Windows and try again. If still not recognized then 
2. You need to change the drive mode to AHCI instead of the unsupported "RAID" or "Intel RST".

If you need #2 then be aware you need to install AHCI support in Windows otherwise it won't boot after the change (but can easily be changed back and then Windows will boot normally again)

---

