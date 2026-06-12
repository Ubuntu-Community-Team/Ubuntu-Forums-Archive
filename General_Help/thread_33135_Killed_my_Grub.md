---
title: "Killed my Grub"
date: 2005-05-09
forum: General Help
---

### Post by artinla on 2005-05-09
Help!

I was trying to dual boot and killed my grub.  It says I have a drive geom error.

I can boot from knoppix and my root partition is intact, however I cannot boot the drive.

This is too important for me to screw up, so I am asking for advice from the pros.

My load is on SDA, I have no other drives attached other than a DVDRW.
SDA2 is my root partition.  My kernel version is 2.6.10-5.  The Ubuntu Rescue mode did not help.

What is the best way for me to repair grub on the drive?  I don't want any special options in the menu, I only need it to boot.  I can handle the menu entries if someone can help me boot back into the drive.

Thanks,

Art

---

### Post by Xian on 2005-05-09
[QUOTE=artinla]I was trying to dual boot and killed my grub. I can boot from knoppix and my root partition is intact, however I cannot boot the drive.[/QUOTE]
Can you be a little more specific? Were you installing another Linux OS and improperly wrote its bootloader to disk, or were you configuring Ubuntu's grub install and made some edits which need to be corrected? When you say that you were trying to dual boot, what exactly were you attempting in order to do this?

It would be helpful to know where to start looking for a solution....

---

### Post by kestasjk on 2005-05-09
I had this problem earlier today when I installed Windows.

Boot up into knoppix.

Insert a floppy into your floppy drive. (Make sure it's set on writeable, and that it's not a bad floppy.)

Run "grub-floppy /dev/fd0u1440" (The device node may be different for you, I've still got knoppix 3.3.)

Boot up off your new grub floppy.

At the grub terminal run:
root (hd0,0)
(If this isn't recognised as ext2fs just do (hd0,1), (hd0,2), (hd0,3). If none of these work move on to (hd1,0) and so on until you get the right one.)
kernel /boot/vm[press tab now and it will complete the rest] root=/dev/hda1
(Replace /dev/hda1 with the partition your root filesystem is on.)
initrd /boot/init[press tab now and it will complete the rest]
boot

And ubuntu will boot up again. :)

So you don't have to repeat this again, once you're in ubuntu go into a terminal and type:
sudo grub-install /dev/hda
(Replace /dev/hda with the hard disk ubuntu is installed on.)

If that command worked you're sorted.

---

### Post by artinla on 2005-05-09
I had HDA setup as my windows XP drive.  On advice from this forum, I setup a small 50M partition at the beginning of the drive for my bootloader.  HDA was the first drive, and I installed Ubuntu on SDA.  Windows was already installed on HDA and working prior to the install of Ubuntu. 

When i was done, I got the proper grub menu, including an entry for Windows. However, when I would select windows, the screen would just flash and windows would not start. 

I decided that I would just rather use two seperate drives and just switch the boot drive in the BIOS when i wanted to change OSes.  SO, I booted into Ubuntu and ran Gparted.  I removed the 50M partition at the beginning of HDA (the windows drive) and expanded the Fat32 windows partition to fill the empty space.  I then disconnected the linux drive (SDA) completely.  I used the XP CD to repair the MBR on HDA (Fixboot and FixMBR).  Windows would then boot perfectly.  I disconnected HDA and reconnected SDA, and when I started the computer, linux was gave me the drive geom error, even though I had just been running linux and had disconnected the drive before making any changes to the Windows drive.

I didn't know it would be such a pain to repair the bootloader on the Linux drive.  Windows was easy! LOL


Thanks,

Art

---

### Post by kestasjk on 2005-05-09
Funny because I had to reinstall Windows earlier today because it stopped booting for some weird hard disk reason, and despite using the repair disk to fixmbr and fixboot it still wouldn't boot up, so I had to reinstall.
Compared to reinstallation I think making a grub floppy is much easier and simpler. Once you've got a GRUB boot disk the installation process is
root (hd0,0)
kernel /boot/vm[tab] root=/dev/hda
initrd /boot/ini[tab]
boot
Compared to the Windows XP rescue CD which loads every driver in existance for 5 mins, just so you can 'fix' the mbr, it's much quicker.

So you have an ATA disk for Windows and a SCSI disk for ubuntu? And you put the ubuntu bootloader on the ATA disk? Can't you boot straight into SCSI disks?

---

### Post by artinla on 2005-05-10
No, actually I have a parallel ATA drive for windows and a SATA drive for Ubuntu.  I had some trouble getting Knoppix to work (grub-floppy cannot find /boot/grub/stage1, even though I know it is there) so I used the Ubuntu install CD in rescue mode and just ran grub from there.  No floppy required.

After fiddling around with it, I edited the .map file and the .lst file and did a grub-install /dev/sda 

All is well now and both OS's work.  I am now trying to get the windows xp selection working in the grub menu, so that I don't have to reset the boot sequence in bios to change from one OS to the other.  

Thanks for your help.

Art

---

