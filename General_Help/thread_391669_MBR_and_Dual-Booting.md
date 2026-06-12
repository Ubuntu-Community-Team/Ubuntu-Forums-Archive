---
title: "MBR and Dual-Booting"
date: 2007-03-23
forum: General Help
---

### Post by antex on 2007-03-23
I'm completely new to Linux as of about 24 hours ago, and I installed Ubuntu on an old computer where I wouldn't care if the entire thing imploded and collapsed in on itself. I have a few issues with wireless not working, or connecting to a shared internet connection, or my screen resolution being stuck on 800x600, with the only other option being 640x480. I digress.

My old computer has two physical hard drives, both with a single partition. I installed Ubuntu on D: - I'm now trying to find a way to turn that hdd back into an empty drive formatted to NTFS, so that Windows can use it again. I tried to use Partition Magic 8.0 (pre-Symantec) to format the Linux partitions, but they don't change over to NTFS.

My second issue is a little complicated. My actual computer that I use has a single drive that is partitioned into C: and D:, and what I plan on doing is putting the second hard drive into this computer, and then installing Ubuntu on there, so that I don't have to be concerned about losing data from installing on a single hard drive. Assuming that the first problem above can be solved, that is. If I can't get the hard drive added onto this computer, I will just partition the drive, and install Ubuntu on there.

Now, my computer is a Packard Bell (not my decision, believe me) and as such, it came with no XP discs or CD Key; the only way to "reinstall" Windows is to restore to factory settings. If, in future, I wish to clear the Ubuntu installation (plus Grub, of course), I know that I need to fix the MBR. However, two things come out of this:

Firstly, I can't use FDISK or fixmbr, since I have no XP disc, and my computer has no floppy. Secondly, if I could use FDISK, wouldn't this completely destroy the "dual-boot" I have on this computer right now? Packard Bell comes with a hidden partition for recovery / restore to factory settings. So, I would need a way to restore this in the boot loader. Does that concern the MBR? As a point of note, my boot.ini reads:

```
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

A response to anything here would be greatly, greatly appreciated. I think that there should be some sort of user-friendly way to cleanly remove Ubuntu (or any Linux system), to be honest.

Thanks

---

### Post by cyberdork33 on 2007-03-23
If you really must, I think there is a way that you can install grub to the same partition as the linux root and then use the windows bootloader to load grub.

Here is a link showing the process for Gentoo Linux...
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

---

### Post by RonKZ on 2007-03-23
Antex:
I'm not a long-termer with any Linux, but using and will be sticking to edgy.  Some things I've learned enuf to have formed some opinions for myself.  

Your Packard Bell, well I would leave that drive ALONE if the drive holds your only link to restoring windoze.  But even if it were otherwise, I would stick a 2nd harddrive in that box and let Linux have the entire drive.  It's just a little too easy to make a partitioning mistake while installing, and wiping out your present installation would leave you in a melluvahess.  Right now I have a big HD partitioned for both, but would rather anyday have 2 separate HD's and not have to fret about that.

BUT good news is that Ubuntu can Read-Only your NTFS drive and R/W a fat32 partition.  You should be able to accomplish with that anything you might need to access your data.  e.g. I'm using Thunderbird in both windoze and Ubuntu partitions, with my e-store on a fat32 partition and usuable by both OS.  To me, that's sweet!

happy puting...
Ron

---

### Post by zvacet on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")
[http://ubuntuforums.org/showthread.php?t=56723&highlight=mbr]("http://ubuntuforums.org/showthread.php?t=56723&highlight=mbr")
[http://ubuntuforums.org/showthread.php?t=24113&highlight=mbr]("http://ubuntuforums.org/showthread.php?t=24113&highlight=mbr")

---

