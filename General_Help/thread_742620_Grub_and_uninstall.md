---
title: "Grub and uninstall"
date: 2008-04-01
forum: General Help
---

### Post by ensou on 2008-04-01
Ok, so I am trying to uninstall Ubuntu for the sole reason that I would like to completely erase all data on my computer (all partitions, GRUB, everything) and restart.

I have Feisty Fawn and Windows XP dual-booting right now, with GRUB as the bootloader.

I have the live cd that I want to use to reformat the hard drive (modify partitions, etc.) but the computer won't boot from it, instead it goes straight to GRUB EVEN if I choose to boot from CD. Now, I chose to try and boot from the system rescue CD (that didn't work) and then from the Gparted liveCD in order to delete both partitions. After, I was going to reinstall windows, then ubuntu. Too bad that the CD drive wont read the live cd now. The only thing that semi-works is the ubuntu live cd which doesn't even fully work - simply goes to grub. 

I have tried everything. All I have now is functioning Ubuntu Feisty Fawn, and functioning Windows XP (thought that the system recovery CD that came with my laptop (no it doesn't include the microsoft system recovery that you can do "fixmbr", it's made for Toshiba) would wipe the whole hard drive clean, but it left Ubuntu partition and grub). AND I still have GRUB. So I'm basically stuck at square one now. No way to remove grub and no way to remove ubuntu. I just wish I could get in there somehow to delete the partitions, but it won't boot into gparted or the livecd or the system rescue cd made available on sourcefourge... I'm so stuck. I feel like ripping it out (the hard drive, it is). 

Any help?

---

### Post by forrestcupp on 2008-04-01
You're sure that your boot options in your bios settings are set to boot to the CD first?  Maybe you should recheck that just to make sure.

---

### Post by ensou on 2008-04-01
It doesnt provide a way for order, but I was able to disable all others except CD-DVD. It wont read gparted cd or system rescue (hangs on black page with single underscore (_), disk spins slowly foreeeeevvvverr), boots to ubuntu live cd (sort of) but just moves on to Grub, like I said. It boots to my laptop product recovery CD too, but that's useless. Only provides factory-default for the Windows partition.

---

### Post by Oldsoldier2003 on 2008-04-01
> **ensou said:**
> It doesnt provide a way for order, but I was able to disable all others except CD-DVD. It wont read gparted cd or system rescue (hangs on black page with single underscore (_), disk spins slowly foreeeeevvvverr), boots to ubuntu live cd (sort of) but just moves on to Grub, like I said. It boots to my laptop product recovery CD too, but that's useless. Only provides factory-default for the Windows partition.
have you tried using the [ultimate boot cd]("http://www.ultimatebootcd.com/")?if your system cd boots there is a fair change that this one will too. if it does work you should be able to completely blast your partitions and set up your windows partition the size you want, then use the alternate ubuntu installer and install ubuntu in the unallocated space.

edit : and as i think about it UBCD should also have fdisk... you should be able to wipe grub with  fdisk /mbr

---

### Post by ugm6hr on 2008-04-02
UBCD has a load of HD eraser tools as well.

Of course, once erased, you may find that you still can't boot from the various CDs anyway, since it is unusual that the BIOS would bypass a bootable CD if it is specified as 1st boot device..

---

### Post by ensou on 2008-04-02
My cd drive isn't reading really any CD-RWs I am putting in it anymore while in Windows, so I'll burn it on another computer and try it later tonight. Thanks for your advice. I still have a strange feeling that I will have to get a new drive soon...

---

### Post by ensou on 2008-04-04
Ok, turned out that the drive is not the problem. I'll be a little bit more descriptive.

Processor on this computer: Intel 915GM

Ok, so I was able to burn UBCD to a cd-r, and I was all ready to go. I turned off the computer and popped the CD in. Then I pressed F10 to choose a boot device - chose CD/DVD. Of course, the cd starts spinning, and shortly thereafter, grub loads and gives me my usual selection of Ubuntu and WinXP.

I turn the computer off. I restart and enter BIOS where I set the order of boot to CD, HDD, FDD, LAN. Same thing happens as above.

This time, I set boot order to CD/DVD, with all the rest disabled. Now the CD gets going but I receive a black screen saying this (repeats over and over again):
```

Intel UNDI, PXE-2.0 (build 082)
Copyright (c) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v2.13 (020326)
PXE-EG1: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.

```
As per the search results at the top of google when searching 'PXE-EG1', I removed the HD and put it back in. No luck. I tried resetting the BIOS to default. No luck.

I'm stuck with an unchangable computer, and it's making me want to throw it out the window. Actually, it's 3-ish years old so I wouldn't mind that much, but I wanted to use it exclusively for Ubuntu, which is why I need to do this (eventually getting rid of windows).

Any help?

---

### Post by ensou on 2008-04-04
And I forgot to mention - Ubuntu is still installed, so is there anything I can do from inside?

---

### Post by ugm6hr on 2008-04-04
> but I wanted to use it exclusively for Ubuntu, which is why I need to do this (eventually getting rid of windows).

Hang on - you are asking a completely different question now.

It appears that there is a problem with the IDE connection from CD-drive to motherboard.  Have you tried a different cable?  Is the cable well-seated?

> And I forgot to mention - Ubuntu is still installed, so is there anything I can do from inside?

As for doing something from "inside" - what do you mean?

If I understand correctly, the current situation is that you want to delete Feisty and XP, and install Ubuntu fresh to fill the whole drive.  Which version did you want?

Do you have ethernet (wired) broadband?

If so - then there is a possible solution with unetbootin.

---

### Post by ensou on 2008-04-05
It wasn't the connection - I got the CD to boot, it was simply a corrupt CD, and it couldn't boot from other methods (since I had disabled them) so it gave me the error (don't know why that one specifically, buttt..)

By inside I mean inside ubuntu. 

But now I got the partition to go away, but can't fix the mbr because the boot cd won't not fail. (Grub gives me error 22)

So I'm working on that.

---

