---
title: "GRUB error 5"
date: 2007-07-20
forum: General Help
---

### Post by bathat on 2007-07-20
The GRUB error stemmed from an attempt to wipe the MBR on /dev/sda1), which I had assumed was the device assigned to my usb stick. The filesystem under fdisk showed up as W95 so I thought there was no way it contained the MBR and instead was the usb stick formatted as vfat or something. After staring at the dreadful 'error 5' for awhile, I decided to try to use a hard drive tool included with UBCD to try to restore the MBR. That didn't help and probably only served to make things worse. Now there is no GRUB and it just says 'unable to boot OS' or something to that effect. I tried using a GRUB bootdisk but the only available root partitions are hdx and fd0 whereas my root drive was sdx. This is very likely due to the fact I setup the bootdisk on a different machine a few years back.

I tried 'fdisk -lu' on a live cd but all it shows is information about my primary and secondary sata drives but the partitions on the hard drive containing the MBR are greatly reduced for some reason and all but /dev/sda1 and sda2 are mounted. Also, fdisk doesn't even cleanly exit without Ctrl+C.

After fiddling around some more trying to recover the MBR without a backup on floppy; the situation is only getting worse, it seems.




This might be a stupid question, but would it work if I were to replace my MBR with one from a different machine?

Also, I've tried UBCD hard drive tools and many live cds--none of them are able to detect my primary drive. At the very least, I would like to backup my important data. The only partition I wiped was the one containing the MBR, so it certainly seems like I'd still be able to mount the drive.


Am I at a complete loss or is there still hope?


Thanks

---

### Post by bathat on 2007-07-20
Update: I was switching in and out hard drives and--all of a sudden--my primary drive showed up in the BIOS.  I have no idea how I did it or what I did to fix the problem, but I was pleasantly surprised to say the least.

Now, when I run fdisk, I see an LBA extended and Linux filesystem--/dev/sda1 & 2; respectively.  Even more encouraging... when I run testdisk, it's able pick up all partitions with correct sizes, etc.  Now it's just a matter of figuring out how to mount the darn things so I can use 'grub-install' to reinstall GRUB and hopefully get my MBR back to normal.

I tried writing new MBR testdisk code to zero sector, but that did nothing.


Any help in regards to where I go from here is much appreciated.
Thanks

---

### Post by confused57 on 2007-07-20
You could try using the live cd to reinstall grub's IPL to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

