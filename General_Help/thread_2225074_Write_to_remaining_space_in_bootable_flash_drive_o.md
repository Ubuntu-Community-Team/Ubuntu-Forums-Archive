---
title: "Write to remaining space in bootable flash drive or have larger than 4 GB persistence"
date: 2014-05-19
forum: General Help
---

### Post by A-DavRoyShi-X on 2014-05-19
Hello, I have tried UNetbootin and elementary OS (based on Ubuntu) with persistence, but cannot find a way to write the remaining space on the flash drive itself no matter how I edit the permissions. I want to store downloads and stuff like that there instead of my limited persistent storage.

The alternative is to max out the flash drive with persistent storage, but that doesn't seem possible on FAT32 with it's 4 GB file size limit. Using NTFS and exFAT doesn't even boot. I just want to fully utilize my flash drive!

I've tried formatting the partition as ext4 in Minitool Partition Wizard and ext3 in Easeus Partition Master, but the persistent file doesn't seem to be created according to amount of time and free space. Please help.

---

### Post by oldfred on 2014-05-19
Similar question in another recent thread, with same answers?

[http://ubuntuforums.org/showthread.php?t=2224922](http://ubuntuforums.org/showthread.php?t=2224922)

---

### Post by A-DavRoyShi-X on 2014-05-19
Not exactly, but are you telling me to create a blank partition called casper-rw, and that'll work? Is that what unetbootin did when the drive was formatted to ext3/ext4?

---

### Post by oldfred on 2014-05-19
Installer is always FAT32 formatted.
If you have ext4 partitions you may have done a full install not a installer. But unetbootin does not do a full install, just create a installer in a FAT32 partition on a flash drive.

---

### Post by A-DavRoyShi-X on 2014-05-19
What I meant was its behaviour installing on a drive that was already formatted as ext3/ext4. If UNetbootin only supports FAT32, then how am I supposed to have larger than 4 GB of persistence?

---

### Post by oldfred on 2014-05-19
I have never used persistence. If I want larger storage I do a full install.

Did you review the links in other thread?

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

      
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by A-DavRoyShi-X on 2014-05-20
That is a possibility, any instructions on how to do it preferably under Windows 7 64-bit?

Yes, but they show Ubuntu-specific instructions.

I thought full installs are configured specifically for your hardware and may not work as well generically on other systems?

Once again, Ubuntu-specific instructions. I only use Ubuntu in VirtualBox.

---

### Post by oldfred on 2014-05-20
The live installer boots most systems, but may need help with boot parameters.

If you do a full install and do not install proprietary drivers for video or other hardware it will boot most systems. I have seem some add scripts at boot to change which drivers get swapped in and out.

You have to create a live installer DVD or flash drive and install to another flash drive. If you have Ubuntu you can directly boot the ISO from the hard drive and use that to install to another drive or device.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

