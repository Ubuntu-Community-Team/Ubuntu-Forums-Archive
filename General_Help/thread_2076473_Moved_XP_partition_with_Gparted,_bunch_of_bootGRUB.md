---
title: "Moved XP partition with Gparted, bunch of boot/GRUB problems"
date: 2012-10-26
forum: General Help
---

### Post by pakopako on 2012-10-26
Awhile ago, I cloned my HDD into a new SSD, but now decided to re-align my partitions. After a big mess, I managed to get GRUB, but if I select Windows (XP), I hit a black screen and nothing happens. I'm trying to get my WinXP back.

Here's everything I think I did:

[LIST]
[*]GParted found bad sectors (some "cloned over", some maybe came with SSD?) for the XP partition (sda1) and NTFS data partition (sda5); ubuntu partition A-OK
[*]Took an external drive and backed up the affected partitions in the SSD  -- I copied stuff from the data partition and used DD for the XP partition```
sudo dd if=/dev/sda1 of=/media/USBiso/sda1.iso
```
[*]Backed up the MBR just in case too```
*dd* if=/dev/sda of=/media/USBiso/sda.boot.mbr  bs=512 count=1
```
[*]Formatted both sda1 (XP) and sda5 (data), re-aligned partitions sda1 and sda5 with GParted, and began copying stuff back (decompressing files to sda5 and DD to sda1)
[*]Reboot
[*]Ubuntu works fine, but XP no longer boots (black screen)
[*]I use the XP recovery disk and try to restore boot-order. I end up removing GRUB.
[*]I reboot using Puppy Linux and restore the old MBR from my USBdrive using DD (big mistake) ...
[*]... I get GRUB back, but Ubuntu no longer recognizes sda1 and sda5; in fact, both Disk Manager and GParted no longer recognize the entire drive (Ubuntu partition included, but I can navigate it just fine)
[*]I use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") to recover the partition table (swap sector at the end of the drive needed to be reformatted before I could enable it)
[*]So now.. I have GRUB working, I can log into Ubuntu, but logging into the XP option results in a black screen and the need to reboot
[/LIST]
 ***Woo-woo!*** Fixed the boot-sector mismatch using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"); launched the program and found that it could edit the boot record of the primary partition. Thanks to everyone who posted!

As a side note, this is an old machine (1.5GHz Pentium-M, 2GB RAM) with a small harddrive (32GB) -- do I really need a Linux Swap file (256MB) considering my Ubuntu partition is ~6GB (5GB filled)?

---

### Post by danielbauwens on 2012-10-26
Did you try booting in recovery mode?

Daniel

---

### Post by pakopako on 2012-10-26
> **danielbauwens said:**
> Did you try booting in recovery mode?
Booting which in recovery mode?
If you mean XP, XP won't boot at all -- no error message or anything, just a black screen if I select it on the GRUB menu.

I could boot using the XP recovery CD. Not sure what I could do from there.

---

### Post by danielbauwens on 2012-10-26
Here: [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
Hope it helps :)

Daniel

---

### Post by pakopako on 2012-10-26
Oh, Ubuntu's recovery mode.

But, what do I do from there?

---

### Post by danielbauwens on 2012-10-26
Woops :)
You might want to use this for windows: [http://www.computerhope.com/issues/ch000627.htm](http://www.computerhope.com/issues/ch000627.htm)

---

### Post by pakopako on 2012-10-26
Still don't have great confidence in using XP's recover console (from the CD) -- changing the MBR is what got me into this mess. Or is there a command I'm not thinking of?

---

### Post by mikewhatever on 2012-10-26
Try updating grub from Ubuntu with **sudo update-grub**. If XP still doesn't work after that, use the [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/") and post its outpus here.

PS: I see no point in using XP's recovery mode for now, and no, you don't need the swap.

---

### Post by pakopako on 2012-10-26
Ran BootInfoScript. I think the attached TXT file says it better than I can, but here are some excerpts I thought could be problematic:

```
sda1:
    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  Windows XP
    Boot files:        /grub.cfg /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr
``````
sda3: 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
``````
=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.603542328 = 29.639077888   boot/grub/core.img                             1
  23.685981750 = 25.432629248   boot/grub/grub.cfg                             1
  28.316383362 = 30.404485120   boot/initrd.img-2.6.38-15-generic             15
  29.570312500 = 31.750881280   boot/initrd.img-2.6.38-16-generic             110
  25.293716431 = 27.158921216   boot/vmlinuz-2.6.38-15-generic                 3
  28.189914703 = 30.268690432   boot/vmlinuz-2.6.38-16-generic                 7
  29.570312500 = 31.750881280   initrd.img                                    110
  28.316383362 = 30.404485120   initrd.img.old                                15
  28.189914703 = 30.268690432   vmlinuz                                        7
  25.293716431 = 27.158921216   vmlinuz.old                                    3

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by oldfred on 2012-10-26
I kept using XP for years just for one application, but with my new SSD I had to stop using XP.  With SSD you have to turn on AHCI for trim to work and XP does not normally have drivers for that. Most suggestions were just to backup data and  reinstall XP to add drivers during install.

All NTFS partitions have in the PBR - partition boot sector info on the NTFS sector start and size that has to match what is in partition table. That is what boot script is telling you does not match. Normally running chkdsk will update that, but sometimes MFT interferes and reinstall is the only solution.

I  did run chkdsk from a Windows 7 repair USB. It worked better than the chkdsk from XP disk, but wrote a Windows 7 PBR. (Testdisk showed difference between backup & new PBR). I was able to reinstall a Windows XP PBR with the Windows 7 repair USB.

---

### Post by pakopako on 2012-10-26
> **oldfred said:**
> I  did run chkdsk from a Windows 7 repair USB. It worked better than the chkdsk from XP disk, but wrote a Windows 7 PBR. (Testdisk showed difference between backup & new PBR). I was able to reinstall a Windows XP PBR with the Windows 7 repair USB.
So... I can attempt to remove the drive and put it on a USB and use Windows Vista to CHKDSK it. Or should I boot using a Vista Recovery Disc and running CHKDSK. And won't it wipe out my GRUB again?

Pardon me, but it seems the lack of sleep is getting to me. Can you detail what you did step-by-step?

---

### Post by oldfred on 2012-10-26
I only had XP and wanted to see if I could make a Windows 7 repair disk in case friends needed help. Back then you could download Vista or 7 repair ISO for free, now $10 from that site. But you can make the same CD or USB flash drive from a Vista or 7 install.

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I never was able to directly from Ubuntu create a Windows repairUSB. But I created a RepairCD and used the CD to create the USB by copying itself to the USB flash drive.

---

### Post by pakopako on 2012-10-26
Sounds like a plan.  I have a Viata recoveryCD I'll try in the meantime.  I presume I use the liveCD to enter recovery mode, enter a console/terminal, and run CHKDSK /B until something clicks?  Also. In case I screw up and lose GRUB again, what's a safer way of recoverying GRUB with only liveCDs for Puppy, Damn Small, and I think AntiX? (Machine is very limited when it comes to boot options -- USB devices are out.)

---

### Post by oldfred on 2012-10-26
Not sure if Boot-Repair works with any of those or not. It works with most Debian based installs, but needs the default apps & scripts that Debian/Ubuntu have.  It also has its own repair liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

The new versions of grub2 now seem to need you to have the same version liveCD to make the easier repairs. Full chroot should work with any install.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by YannBuntu on 2012-10-26
> **oldfred said:**
> Not sure if Boot-Repair works with any of those or not.

i haven't tested, but i think it doesn't work with Puppy, Damn Small, AntiX. I only tested Debian-based, Fedora, OpenSuse and Arch.

---

### Post by pakopako on 2012-10-26
Ah, what a good rest will do. Still, it's bloody annoying that the Vista recovery CD takes 30 minutes to load, and another 10 to process everything.

I've run chkdsk /x /b on the C: drive (sda1), but to no avail. It detects the reordered space on the drive, but doesn't really do anything. (It can't even write a log file. *""failed to transfer logged messages to the event log with status 50"* -- likely because it would have written the log to the temporary "X:" drive the RecoveryCD created.)

I rebooted back into Ubuntu 11.04 and ran BootInfoScript again, and only one line had changed and it was in the Mount Point section (my Ubuntu partition, sda3; commit=600 changed to commit=0):
```
/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
```I'm apprehensive about loading the Vista RecoveryCD and running FIXMBR -- last time I did that, I had to use a Puppy liveCD to restore much older MBR into my drive and borked my partition-table so much that I needed TestDisk to recover it.

Should I make a backup of my current MBR in case Microsoft's FIXMBR flubs, or should I avoid using FIXMBR altogether? This is the only method I know of to back up my MBR, are there any better ways out there?
```
sudo dd if=/dev/sda of=SDA-backup bs=512 count=1
```

---

### Post by oldfred on 2012-10-26
If you backup with dd and use 512 which includes partition table, then change partition table your backup will destroy your system. Back to testdisk.

Better just to use Boot-Repair or manual ways to use a Ubuntu liveCD to restore grub2's boot loader or install lilo or syslinux boot loaders to the MBR,  which are Windows like boot loaders and will boot Windows directly.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Boot live cd -  knoppix syslinux also in Ubuntu
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by pakopako on 2012-10-27
> **oldfred said:**
> With SSD you have to turn on AHCI for trim to work and XP does not normally have drivers for that.
Wait, XP can run TRIM? (Even with drivers?)

> **oldfred said:**
> All NTFS partitions have in the PBR - partition boot sector info on the NTFS sector start and size that has to match what is in partition table... Normally running chkdsk will update that, but sometimes MFT interferes and reinstall is the only solution.
This sounds... odd.

CHKDSK /B /X (Vista) fixes two bad sectors, but nothing was fixed. Bootrec (Vista) wiped something from the drive (computer saw it as an empty drive, even though the partition tables were intact when I loaded it as a USB drive). FixBoot (XP) did nothing, FixMBR (XP) wiped away the boot record.

I ran Puppy, restored the MBR and got Ubuntu back (and the Grub menu). The odd thing is that running HIREN's CD, I can get to the XP loader and load XP.

I even tried running XP installer... but after a reboot, I still get to the black screen (because it gets rid of GRUB).

I can't run LiLo to create a new boot sector?

---

### Post by pakopako on 2012-10-28
Nevermind.

Started up TestDisk to fix the MBR again when I noticed there was a Boot management option. Fooled around with the XP partition and managed to fix the size mismatch.

Woo-hoo, [TestDisk](http://ubuntuforums.org/showthread.php?t=387922)!

---

