---
title: "Dual-boot problem - Is WinXP corrupting my Grub?"
date: 2007-04-24
forum: General Help
---

### Post by Boztech on 2007-04-24
**PREFACE**
I have a Dell 600m laptop with a 60GB (internal) SATA drive.

My partitioning is as follows-
Primary - 40GB - NTFS - WinXP
Logical - ~17GB
    15GB - ext3 - / (Kubuntu 7.04)
    2GB - swap

I use WinXP as the primary OS and it was installed first.  I used a Gparted live cd to shrink the XP partition to 40GB, and left the remaining as free space.  I then installed Kubuntu 7.04 in the remaining free space with the above partitioning scheme, and Grub on the MBR.

**PROBLEM**
After installing Kubuntu, I can reboot into Grub and everything is listed correctly and I can boot into Kubuntu just fine.  I can also reboot from within Kubuntu and boot back into Kubuntu from Grub just fine.

The problem begins when I reboot and choose to boot into WinXP from Grub - WinXP will run fine, but what happens is I get a prompt that a new device was installed and I need to reboot my computer.  When I do this, my computer will POST but Grub will not be displayed.  Instead, the computer will perpetually reboot after POST.
[B]
ACTIONS TAKEN
[/B]I have found two ways of working temporarily around this problem.  I can boot to the recovery console of my Window XP disc and run FIXMBR and FIXBOOT, which of course overwrites Grub but allows me to boot into Windows.  I have also tried reinstalling Grub per the "Reinstalling Grub from Ubuntu live CD" instructions on this forum.  This will get Grub working again and I can boot into Kubuntu - but as soon as I boot WinXP again the problem occurs again after I reboot XP - the computer goes into a reboot cycle before Grub is displayed.

I can only assume one of two things - either WinXP itself is writing something to the MBR or somehow corrupting Grub when I boot into for the first time - or it has something to do with the fact that I erased the factory FAT32 utility boot partition that Dell puts on all of its laptops (for diagnostics) before I installed XP.  Either way I have dug through the dual boot guides here and have yet to come to a solution for this issue.

---

### Post by dcstar on 2007-04-24
> **Boztech said:**
> 
..........
I can only assume one of two things - either WinXP itself is writing something to the MBR or somehow corrupting Grub when I boot into for the first time - or it has something to do with the fact that I erased the factory FAT32 utility boot partition that Dell puts on all of its laptops (for diagnostics) before I installed XP.  Either way I have dug through the dual boot guides here and have yet to come to a solution for this issue.

The code that starts Grub resides in the first 446 bytes of your boot device, you can save this data with the "dd" command to a file and then copy it back with the same command if Windows changes things.

You may want to try this, but if XP (or something running on XP) detects a change and "fixes" things then you may have to find what is doing that and disable it - it may well be an option buried somewhere in XP (or some Spyware/Virus program).

---

### Post by asipi on 2007-04-26
FUN
looks like another gift from M$ userfriendly "we know the user needs just before they realize it" spirit :)
/FUN

anyway it is very strange xp also never touch MBR some software should do this on your laptop. Is that the originally installed by DELL? In case you should ask Dell's support about this wtf... Is it possible that any "userfriendly" service "fixes" the MBR if it is "corrupted"?

When you boot into xp do you see any action of chkdsk before the loginscreen?

Do you really put grub into MBR and not into the linux partition's boot sector?

---

