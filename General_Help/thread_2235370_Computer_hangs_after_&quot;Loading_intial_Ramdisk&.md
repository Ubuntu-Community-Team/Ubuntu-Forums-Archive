---
title: "Computer hangs after &quot;Loading intial Ramdisk&quot; . . . . sometimes"
date: 2014-07-20
forum: General Help
---

### Post by RangerK on 2014-07-20
I'm looking for advice on how to diagnose this.  I've owned this machine for almost exactly a year.  What's strange is that this problem has been happening since I first installed Ubuntu, but I lived with it b/c it would always start on the second or third try.  But lately, it almost never starts.

The problem looks like this:

From the GNU GRUB menu (version 1.99-21ubuntu3.14) I chose "Ubuntu, with Linux 3.2.0-59-generic (recovery mode)".  Two rows of text flash on the screen.

"Loading Linus ver. . . . . ."
and
"Loading initial ramdisk"

Then the screen goes dark.

It's really strange that it work sometimes and not other times.  Any advice on diagnosing this is appreciated.  Here are some specs about the machine:

Processor: Intel Core i3 3220  (BX80637I33220) s1155, 2 core, 3.30GHz, QPI 4.8 GT/s, 650 MHz, L2: 2x25
Motherboard: ASUS P8B75-V B75, 1155, DDR3 2200(O.C.)*
Videocard: Radeon HD 7870 2048Mb Sapphire OverClock (11199-19-20G) GDDR 5, 1050MHz/4800MHz, 256 Bit


Memory: DDR3 4GB 1600 MHz Hynix (HMT351U6CFR8C-PBN0 / HMT451U6MFR8C-PB N0) 1600 MHz, PC3-1280

 HD: 3.5"  1TB WD (WD10EZEX) 7200 &#1086;&#1073;./&#1093;&#1074;, 64 Mb, SATA III



Partitions:
sda1 vfat      47M /boot/efi  
sda2 ext4     286M /boot      
sda3 swap     7.5G [SWAP]     
sda4 ext4      28G /          
sda5 ext4   372.5G /home      


(Note, I think I have a separate problem with the partitions.  Either /boot or /boot/efi is too small for the latest updates I'm getting.  So I haven't updated in months, and now I can't install new software because of package conflicts.  But I'd like my computer to start normally before working on this problem.)

Any help is appreciated.  Thanks.

---

### Post by oldfred on 2014-07-20
Generally an efi partition is minimally 100MB and usually 300MB. And most desktops do not need a separate /boot partition. Server type installs or RAID or LVM may need a separate /boot.

Since you partitions are small you have to houseclean regularly. And if now you need video drivers it may be impossible to add them unless you make room first.

Are you using the proprietary video driver? Or the default open source one?
I do not know AMD as I use nVidia.

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)


 Updates, backups, delete old kernals - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by pretty_whistle on 2014-07-20
oldfred-

There's a duplicate of this thread right here:

[http://ubuntuforums.org/showthread.php?t=2235371](http://ubuntuforums.org/showthread.php?t=2235371)

---

### Post by oldfred on 2014-07-20
Duplicate threads merged.

Please do not create duplicate threads, we all are volunteers and need to see what others have posted to as not to waste our efforts on helping users.

---

### Post by tgalati4 on 2014-07-20
How full is your boot partition?

```
sudo fdisk -l
df -h
```

It's possible that your latest initrd.img* is damaged.  If your /boot partition is full, then any update that touches the kernel will force a new initrd.img to be created and so you are only getting part of the initial RAM disk loaded.

You should be able to boot with a previous kernel.  That is why they exist.

Check the SMART status of the drive:

```
sudo smartctl -a /dev/sda
```

---

### Post by RangerK on 2014-10-17
FYI: This turned out to be a hardware error.  I ended up replacing the motherboard.

---

