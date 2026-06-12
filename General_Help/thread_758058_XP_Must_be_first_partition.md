---
title: "XP Must be first partition?"
date: 2008-04-17
forum: General Help
---

### Post by Wally_dog on 2008-04-17
I just heard from a friend, that if I want to dual-boot Windows XP and Ubuntu using this guide: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) That I will have to have XP as the first partition in order for XP to work. So, if I have Ubuntu installed first (pre-installed from Dell), is it possible to put a XP partition in front of the Ubuntu partition, so it goes like this:

(Before installing XP)

Ubuntu - Swap

(Installing XP, not wiping hard drive of Ubuntu)

XP - Ubuntu - Swap

And, where is a good place to put the swap file (which is virtual memory, correct?)? I heard that partitions at the end of the HDD will run slower than those at the top, so I naturally put Swap at the bottom since it's not an OS.

Any suggestions/answers would be greatly appreciated!

Wally

---

### Post by Trollslayer on 2008-04-17
XP first is the method I've used and is easy.
It makes no real difference where on the hard drive the partition is.

---

### Post by Wally_dog on 2008-04-17
Ok. Well if I have Ubuntu installed first, using the GParted Live CD, can I make a partition in front of Ubuntu?

---

### Post by kk0sse54 on 2008-04-17
i would install windows first because i have read that if you install ubuntu first and then windows that the windows installtion can screw up your ubuntu system

---

### Post by confused57 on 2008-04-17
You should be able to install Windows to a partition after your Ubuntu partition, as long as it's installed to a primary partition.  Then you would need to reinstall grub to the mbr after installing Windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

### Post by Wally_dog on 2008-04-17
Ok, so then when I get my Dell Desktop with pre-installed Ubuntu, format the hard drive, split it into 3 partitions: one for XP(first), one for Ubuntu(second), and then one for the swap file(third). Then after I install XP, if I install Ubuntu on the second partition, GRUB will overwrite XP's bootloader, so then I get no problems?

---

### Post by confused57 on 2008-04-17
That should work OK...unless you've already ordered a Dell with Ubuntu, it would probably be easier(& possibly cheaper) to order a similar Dell with XP(if possible), then install Ubuntu as a dual boot.

---

### Post by SegaFan on 2008-04-17
> I just heard from a friend, that if I want to dual-boot Windows XP and Ubuntu using this guide: [http://apcmag.com/how_to_dual_boot_l...lled_first.htm](http://apcmag.com/how_to_dual_boot_l...lled_first.htm) That I will have to have XP as the first partition in order for XP to work.
No, I followed that guide when I set up my dual boot and I have XP as the 2nd partition. You should be able to keep your Ubuntu installation and install XP in the second partition by following the guide.

---

### Post by bodhi.zazen on 2008-04-17
As has been mentioned the only requirement for windows XP is that it is on a primary partition.

You can create a new primary partition in front of ubuntu with gparted. You may need to update /etc/fstab and /boot/grub/menu.lst as your partitions may change.

here is a guide you can look at to give you an idea of things you may need to check.

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

IMO best to resize your Ubuntu partition and make a new primary partition AFTER your ubuntu partitions.

I think the confusion is that Windows "needs" to be installed on the first hard drive, although this is not true either, you would need to map the hard drives in GRUB in this event (which is a little beyond this thread).

============

If you install windows first, then Ubuntu everything (grub) should be set up just fine.

If you add windows to your current installation you will need to restore grub

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Wally_dog on 2008-04-19
**[center]XP Pre-installed[/center]**

PROCESSOR	[right]Intel® Core™2 Duo Processor E8200 (6MB L2 Cache,2.66GHz,1333FSB)	[/right]
OPERATING SYSTEM	[right]Genuine Windows® XP Home Edition	[/right]
MONITOR	[right]No Monitor	[/right]
MEMORY	[right]2GB Dual Channel DDR2 SDRAM at 800MHz- 2DIMMs	[/right]
HARD DRIVE	[right]250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™	[/right]
OPTICAL DRIVE	[right]16X DVD+/-RW Drive[/right]	
VIDEO CARD	[right]ATI RADEON HD 2400 XT 256MB	[/right]
SOUND	[right]Integrated 7.1 Channel Audio	[/right]
KEYBOARD & MOUSE	[right]Dell USB Keyboard and Dell Optical USB Mouse[/right]	
FLOPPY & MEDIA READER	[right]No Floppy Drive Included[/right]	
MODEM	[right]No Modem Option[/right]	
My Software & Accessories
SPEAKERS	[right]No speakers (Speakers are required to hear audio from your system)	[/right]
ANTI-VIRUS SOFTWARE	[right]No Subscription (only 30-day protection)	[/right]
OFFICE SOFTWARE	[right]No Productivity software pre-installed	[/right]
My Service
WARRANTY AND SERVICE	[right]1Yr In-Home Service, Parts + Labor, 24x7 Phone Support	[/right]
DATASAFE ONLINE BACKUP	[right]Included 3 GB DataSafe Online Backup for 1Yr	[/right]
ALSO INCLUDED WITH YOUR SYSTEM
Mouse	[right]Mouse included with Keyboard purchase	[/right]
Adobe Software	[right]Adobe® Acrobat® Reader 8.1	[/right]
Internet Access Service	[right]6 Months of America Online Membership Included	[/right]
Network Interface	[right]Integrated 10/100 Ethernet	[/right]
Labels	[right]Windows XP™	[/right]
PHOTO AND MUSIC SOFTWARE


There... that is my configuration for an XP system that will dual-boot Ubuntu. Can someone confirm that this hardware will work with Ubuntu, or offer me a link where I can check myself?

---

### Post by confused57 on 2008-04-19
I would definitely recommend getting a Nvidia graphics card vs ATI.  You might try doing a Google search with the model of the pc, plus Linux & Ubuntu keywords.

---

