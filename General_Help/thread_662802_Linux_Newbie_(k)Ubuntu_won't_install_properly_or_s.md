---
title: "Linux Newbie: (k)Ubuntu won't install properly or something. Help??"
date: 2008-01-09
forum: General Help
---

### Post by EckoAK on 2008-01-09
I'm a longtime Windows user, and I thought I'd give Linux a shot. Downloaded Kubuntu and burned it to a disk. After finally getting the Live CD to work (I have an 8800 GTS, apparently theres some issue with the splash screen, got around it by deleting "splash --" from start-up screen with special options (F6)), I decided I'd like to make it a more permanent part of my computer, so I installed it, thinking nothing could go wrong. Sure, I still can't figure out how to install anything. I don't understand why I can't just double click on something and have some installer run for me. I don't know any command line stuff (any tips on this would be cool too).

The problem is neither of my operating systems will boot up without a disk anymore (and I can't find my dang XP disk). Kubuntu doesn't seem to have installed properly, because whenever I download anything, the files disappear after rebooting. Also, my optical drive won't eject the CD while Kubuntu is running. Whenever I try booting without the disk, I get some kinda error, just one line of text along the lines of "Operating System Error"


Right now I just want to be able to get into Windows because spring semester just started today. If it means getting rid of Kubuntu, then that is totally fine, but I can't seem to do that. QTParted won't run, and the few other ways I have managed to get to a partition editor have been while running Linux, so I couldn't format the partition it is on (both OSs are on the same hard drive). I read somewhere that I need to fix the MBR before Windows will boot properly.

Also, Grub isn't showing up anywhere, and when I've tried to install..well it just doesn't install.

I know absolutely nothing about Linux, or any command line things. Can anyone point me in the right direction or help me out here?

---

### Post by evil316 on 2008-01-09
> **EckoAK said:**
> I'm a longtime Windows user, and I thought I'd give Linux a shot. Downloaded Kubuntu and burned it to a disk. After finally getting the Live CD to work (I have an 8800 GTS, apparently theres some issue with the splash screen, got around it by deleting "splash --" from start-up screen with special options (F6)), I decided I'd like to make it a more permanent part of my computer, so I installed it, thinking nothing could go wrong. Sure, I still can't figure out how to install anything. I don't understand why I can't just double click on something and have some installer run for me. I don't know any command line stuff (any tips on this would be cool too).

The problem is neither of my operating systems will boot up without a disk anymore (and I can't find my dang XP disk). Kubuntu doesn't seem to have installed properly, because whenever I download anything, the files disappear after rebooting. Also, my optical drive won't eject the CD while Kubuntu is running. Whenever I try booting without the disk, I get some kinda error, just one line of text along the lines of "Operating System Error"


Right now I just want to be able to get into Windows because spring semester just started today. If it means getting rid of Kubuntu, then that is totally fine, but I can't seem to do that. QTParted won't run, and the few other ways I have managed to get to a partition editor have been while running Linux, so I couldn't format the partition it is on (both OSs are on the same hard drive). I read somewhere that I need to fix the MBR before Windows will boot properly.

Also, Grub isn't showing up anywhere, and when I've tried to install..well it just doesn't install.

I know absolutely nothing about Linux, or any command line things. Can anyone point me in the right direction or help me out here?


Sounds like you are still running off of the live CD even though you think you aren't.  At some point during the install it will ask you to remove the live CD.  Try installing it again and pay attention to when it asks you that.

---

### Post by pietjanjaap on 2008-01-09
If you finished the install of linux then download a bootable cd called "supergrub" then you can reinstall grub on the harddisk.
Then you can reboot, set the right bootdevice.

"Operating System Error" means no grub found, no os found, no bootable device found, wrong bootdevice choosen.

Fix the mbr on windows(then you lose linux), start winxp cd, goto repair(r), goto recovery console(black dos screen), then type: fixmbr or mbrfix.

---

### Post by EckoAK on 2008-01-09
I can't eject the Kubuntu CD, so I have no way of burning or running any other CDs. Also, I don't have a floppy drive :( However, I think there is hope. My RA was borrowing my Windows XP install disk, and I'll be able to get it back in about 6 hours. Hopefully that will work.

Is Super Grub a bootable program? Like..can I run it without running an OS? because I could get a friend to burn it for me

Thanks for the help!!

---

