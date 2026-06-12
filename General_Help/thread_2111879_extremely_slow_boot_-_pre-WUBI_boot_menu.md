---
title: "extremely slow boot - pre-WUBI boot menu"
date: 2013-02-03
forum: General Help
---

### Post by Gigaz1234 on 2013-02-03
Hello
I'm not sure whether this is the right subforum for my problem but I'm rather clueless.

I installed the newest version Ubuntu and it works. I can choose between Windows and Ubuntu.
But when I restart my computer, it needs about 5 minuits to show me the bootloader screen where I can choose my operating system. Before I installed Ubuntu this only took some seconds.
Has this problem already occured to others? What can I do?

---

### Post by TheFu on 2013-02-03
We could like to help, but this is not enough information to go on.
* Which version of Windows?
* Which version of Ubuntu?
* Did you partition or is this a WUBI install?
* Is only 1 hard disk involved?
* UEFI BIOS?
* Does the hard disk have 4K sectors or 512b sectors?
* Is the PC a specific model from a famous vendor or home built?
* How old is the PC? Could some hardware be failing that Ubuntu sees and Windows ignores?
* Is networking wired or wifi?  Try wired.
* Is networking DHCP or static IPs? Try static.

A stopwatch would be useful too - from power, to BIOS screen, to first selection, to boot, to login .... timestamps for each would tell use more.

Lots of questions. Chances are that 1 of them is really the key to solving the issue you are seeing.

---

### Post by Gigaz1234 on 2013-02-03
> **TheFu said:**
> 
* Which version of Windows?


Windows 7 Home

> **TheFu said:**
> 
* Which version of Ubuntu?


Ubuntu 12.10

> **TheFu said:**
> 
* Did you partition or is this a WUBI install?


WUBI.

> **TheFu said:**
> 
* Is only 1 hard disk involved?


I have installed both Windows and Ubuntu on my SSD, but I have a backup Windows on a conventional hard disc.

> **TheFu said:**
> 
* UEFI BIOS?


BIOS.

> **TheFu said:**
> 
* Does the hard disk have 4K sectors or 512b sectors?


The SSD has 512b sectors.


> **TheFu said:**
> 
* Is the PC a specific model from a famous vendor or home built?


Home built.


> **TheFu said:**
> 
* How old is the PC? Could some hardware be failing that Ubuntu sees and Windows ignores?

I built it in summer '11. If something is failing it is probably my video card. With Ubuntu
it makes a different sound and occasionally I see graphic errors. But it works fine with Windows.

> **TheFu said:**
> 
* Is networking wired or wifi?  Try wired.
* Is networking DHCP or static IPs? Try static.


I did both and it doesn't solve the problem.


> **TheFu said:**
> 
A stopwatch would be useful too - from power, to BIOS screen, to first selection, to boot, to login .... timestamps for each would tell use more.

From power to BIOS - about 2-4 seconds.
From there it shows a blinking underscore in the left upper corner of my screen for 5 minuits and 10 seconds.
Afterwards I can select an operating system (Windows on SSD, Windows ond conventional hard disc, Ubuntu).
When I chose one I arrive at the login in 1-2 seconds.


Thank you for your help :D

---

### Post by Gigaz1234 on 2013-02-03
New information:

I installed GParted and it doesn't seem to see the conventional hard disc. The SSD has 4 partitions.

---

### Post by TheFu on 2013-02-03
WUBI is not a real-to-hdd install.  Sorry, but I've never, ever, used WUBI, so I can't help.  I wuold guess that gparted only sees the virtual storage that WUBI sets up, not the real physical disks, that would explain what you are seeing.

If you change the title of this thread to include "extremely slow boot - pre-WUBI boot menu" then people with that expertise might respond.

They will probably need to know which version of Ubuntu.  That is inside the /etc/lsb-release file.

Good luck.

---

### Post by Gigaz1234 on 2013-02-04
> **TheFu said:**
> WUBI is not a real-to-hdd install.  Sorry, but I've never, ever, used WUBI, so I can't help.  I wuold guess that gparted only sees the virtual storage that WUBI sets up, not the real physical disks, that would explain what you are seeing.

If you change the title of this thread to include "extremely slow boot - pre-WUBI boot menu" then people with that expertise might respond.

They will probably need to know which version of Ubuntu.  That is inside the /etc/lsb-release file.

Good luck.


Thank you.
I will ask a moderator to change the thread title.

Inside /etc/lsb-release is

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

---

### Post by oldfred on 2013-02-04
Changed title.

I do not know wubi, but that is inside NTFS partitions. 

I had XP installed and gparted would not show drive, even though XP booted. After running chkdsk gparted showed drive and XP booted a bit quicker. But I believe gparted usually now shows partitions but has warning flags.

I might try chkdsk on all NTFS formatted partitions.

---

### Post by bcbc on 2013-02-04
The time delay from BIOS to the first menu (Windows Boot Manager) does not involve any Ubuntu processes. It's the time the BIOS to load the bootloader in the MBR, and the bootloader locates the partition with the boot flag and loads the partition boot record, which then loads the Windows boot manager.

So, why does it take so long? No idea, but file system/partition table corruption seems the most likely.

There are a number of reports of file system corruption from users with Wubi. It's also not common to see Wubi installed on an SSD either. Whether this is a factor is hard to say. I had a Windows-only computer become unusable due to file system corruption (maybe from some bad sectors? because I was able to fix it by wiping and repartitioning the drive), so the cause is not always clear.

---

### Post by Gigaz1234 on 2013-02-04
Thank you, I will try that.

---

