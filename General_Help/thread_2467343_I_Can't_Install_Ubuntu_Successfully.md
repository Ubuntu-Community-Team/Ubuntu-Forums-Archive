---
title: "I Can't Install Ubuntu Successfully"
date: 2021-09-23
forum: General Help
---

### Post by squiddykat on 2021-09-23
Every time I try, it completes, but the drive doesn't show up, or if it does, the black screen with grub> shows up.

I looked at the drive, everything appears to be there, I go to the home folder, and only 3 items are in there:
.bash_logout
.bashrc
.profile

I tried different drives on different computers. Both install dries were burnt via Etcher.

---

### Post by squiddykat on 2021-09-23
Update: I tried using the built in USB installer in Ubuntu, the same thing happened.

---

### Post by squiddykat on 2021-09-23
Since I tried installing on another computer with other Ubuntu installs,all the other disks bring up grub> screen. My installs won't work.

---

### Post by C.S.Cameron on 2021-09-23
There are many reasons a persistent USB might not boot. Please provide more detail about your case.

**BIOS**

- USB not set as first hard drive in BIOS

- Problems with BIOS or UEFI boot partitions or files.

- Secure Boot is not turned off

- Drive not compatible with computers BIOS or UEFI boot mode

- Incorrect partition table

- Out of date BIOS/UEFI firmware

- Junk in volatile memory

- Fstab entry in Full install USB referring to HDD's efi boot partition on drives created on uefi machines.

**GRUB**

- Incorrect root partition in grub

- Incorrect path to ISO in grub

- Incorrect persistent-path, (if used), in grub

- Grub menu entry structure not suiting OS

- Incorrect file type for vmlinuz and initrd (.efi and .lz)

- The word "persistent" is missing from grub.cfg, txt.cfg, syslinux.cfg or text.cfg

**Persistence (casper-rw and home-rw)**

- Persistence partition is not an ext filesystem 

- Persistence file not on FAT filesystem

- Persistence file/partition reused from different version

- Persistence file full of data, or file update attempted

**Hardware**

- Corrupted flash drive, reformat and reload

- Bad flash drive

- Not enough RAM to run Ubuntu

- Bad or incorrect USB socket

- Incompatible computer CPU

- Incompatible computer GPU

- Computer does not meet minimum specs, a lighter version of 'buntu is required

- Motherboard voltage irregularities

- Motherboard BIOS limitation with multiple USB devices

**Software**

- Bad MD5SUM / corrupt ISO file

- Modified or corrupted ISO9660 partition

- USB was removed from computer before ISO file is completely copied

- Out of date boot drive creation tool

- User inexperienced with boot procedure

---

### Post by TheFu on 2021-09-23
> **squiddykat said:**
> Update: I tried using the built in USB installer in Ubuntu, the same thing happened.

Don't install, use the "Try Ubuntu" choice on the boot menu.  If that doesn't work, then there is likely an incompatibility with the flash drive and the USB controller.  I wish there were some way to know in advance whether any specific flash storage will work with any specific USB port. I've found none.  Some expensive flash drives don't work on 1 machine, but work fine on 5 others.  Some cheap flash drives work everywhere I've tried, but not on 1 random machine.  

There's just no way to know.

Try a different flash drive.
Try a different copy program to get the ISO bits onto the USB storage.  I use the normal Unix 'cp', not any fancy program.
Try a different port on the computer.  For a long time, USB2 was better than USB3 for compatibility.
On computers with SDHC slots, you can try to boot from that as well.  All my recent laptops do that and for an ISO of 1.2GB, using a 4G SDHC for emergency needs is much nicer than wasting a 64G USB3 flash drive.  Just sayin'.

I think Ubuntu requires the system BIOS to have storage devices in AHCI mode.  Usually the other option is some sort of RAID.  [https://askubuntu.com/questions/1171279/do-i-need-to-switch-storage-mode-in-bios-from-raid-to-ahci-to-install-ubuntu](https://askubuntu.com/questions/1171279/do-i-need-to-switch-storage-mode-in-bios-from-raid-to-ahci-to-install-ubuntu)
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

Some Intel systems with Intel Optane Memory (it is a caching addon, I think) had/have issues. I don't know if that has been fixed or not.
[https://askubuntu.com/questions/1009710/intel-optane-memory-support-for-ubuntu-and-windows-10-dual-boot-on-dell-i7](https://askubuntu.com/questions/1009710/intel-optane-memory-support-for-ubuntu-and-windows-10-dual-boot-on-dell-i7)

Those are my ideas.

---

### Post by squiddykat on 2021-09-24
It installs fine, and Try Ubuntu works, it just is not detected as a bootable drive, even in another computer.
Weird thing 1: At my parent's house, I installed Ubuntu on it, it worked fine. I bring it home and it won't work in my computer, nor my other one.
Weird thing 2. I try another drive, this one is detected, and I install Ubuntu 20.04 on it, it still shows up. I get the grub> screen again. In my main Ubuntu drive, I look at the drive and it's the same thing, just the 3 files listed in the home folder.

It's  one of those Twilight Zone experiences, which I've had many. It kinda  reminds me of one when I bought a HDD enclosure quite a few years ago,  any drive connected to it, it would wipe the partition table off of it,  like you just brought it home from the store.

---

### Post by oldfred on 2021-09-24
What is the system?
UEFI or old BIOS?
If very old BIOS, Ubuntu may be too much and you need a lighter weight flavor?
If newer UEFI (since 2012) you need to update UEFI and change settings in UEFI. Depending on brand/model settings may vary.
See also link below in my signature if UEFI system for general UEFI install instructions & some special settings.

---

### Post by squiddykat on 2021-09-27
I got it working. Here's what I did. I installed it on a computer with no other OS.

Ubuntu  doesn't like other OSs or other copies on the same computer apparently.  The Windows drive made it hang, and I couldn't complete the  installation. I had already installed Windows, and my laptop, Ubuntu was  the only OS. When I tried to install Ubuntu on other computers, it  must've took out the boot files.

Everything is working now. 

Here's what I tried:
~  Installed Ubuntu 20.04 x64 on a computer with Windows and Ubuntu (Same  version). No drive show as bootable, but showing up in the BIOS, accessible within Ubuntu.

~ I try another flash drive, burnt the same. No same issue.

~  I try burning it with the burnt in USB burner that comes with Ubuntu.  No luck, then I was able to access the drive, for a little while, than I  couldn't (maybe when I conected it to my main computer).

~ I try installing it on a laptop via USB to SATA cable. No luck, and I then get grub> screen on my laptop's boot screen.
~  I take the laptop, and drives to my parent's house, and reburnt the  flash drives with Ubuntu 20.04 x64, to make sure they are not corrupted.
~  I successfully install Ubuntu 20.04 x64 on the laptop and the drive  (one drive, I brought the wrong one). I had installed Ubuntu like before  on a drive via the laptop via USB to SATA cable. Success.
I bring that drive home, and connect it to my computer. It's not seen as a bootable drive.
~ I try that same drive in another computer, not seen).
~ I connect another drive that already has Ubuntu installed, and it's seen in the as bootable.

~ I reinstall Ubuntu on that drive, and it's still seen as a bootable drive at that point, but black screen, no boot.

~  A while later I decide to boot on a drive on another computer, at this  point it is the only drive, and it works. I used Try Ubuntu.

~ I try another drive, the same thing, no other drives connected, Try Ubuntu, success.

~  I try the drive that wouldn't be shown as as bootable, same thing as  before, no other drives connected, it now shows up and is bootable. I  believe I also tested it on my other computer and it works there also,  but I have a different drive on my main computer with another Ubuntu OS,  the same version because I just happen to use that first

---

### Post by oldfred on 2021-09-27
Confused on all your drives.

Ubuntu installer, installs grub boot loader to first drive, usually a Windows drive. With UEFI they share the same ESP - efi system partition. Grub will boot working Windows.
With old BIOS, grub overwrites the Windows BIOS boot loader in MBR, but grub will boot working Windows. 
But Windows fast start up must be off and Windows must not need chkdsk whether UEFI or BIOS boot.

You can always see details of your  boot configuration with Boot-Repair's report. I regularly run & save a copy of the report, so part of my normal backup. 

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

