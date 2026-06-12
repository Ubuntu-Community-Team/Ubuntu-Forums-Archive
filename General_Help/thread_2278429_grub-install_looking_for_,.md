---
title: "grub-install looking for /,"
date: 2015-05-16
forum: General Help
---

### Post by karat on 2015-05-16
Installing regular ubuntu updates via software updater gives me the following error:

grub-install: error: cannot find a GRUB drive for /,. Check your device.map.

I have no idea why it is looking for a drive mounted on "/,", but it doesn't exist.

Before fixing this, I'd like to know if killing software updater will screw up my boot.

---

### Post by QDR06VV9 on 2015-05-16
Hi karat this should point you in the right direction [http://ubuntuforums.org/showthread.php?t=2036730](http://ubuntuforums.org/showthread.php?t=2036730)
Pay close attention to post #10 after reading the whole page.
More help here [http://askubuntu.com/questions/510434/grub-install-fails-after-upgrading-from-12-04-to-14-04-grub-pc-is-broken](http://askubuntu.com/questions/510434/grub-install-fails-after-upgrading-from-12-04-to-14-04-grub-pc-is-broken)
Kind Regards

---

### Post by karat on 2015-05-16
That was not especially helpful.  I did clone the disk from a failing hard drive recently.  The following may be the problem:

karat@karat-mini-overlord:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x002641b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648  1219397759   609493056    7  HPFS/NTFS/exFAT
/dev/sda3      1219399678  1424185343   102392833    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda4      1424185344  1465149167    20481912    2  XENIX root
/dev/sda5      1219399680  1220411391      505856   83  Linux
/dev/sda6      1220413440  1243029503    11308032   82  Linux swap / Solaris
/dev/sda7      1243031552  1301616639    29292544    b  W95 FAT32
/dev/sda8      1301624832  1360216063    29295616   83  Linux
/dev/sda9      1360218112  1424185343    31983616   83  Linux

---

### Post by karat on 2015-05-16
Here is a boot repair summary:

[http://paste.ubuntu.com/11168917/](http://paste.ubuntu.com/11168917/)

---

### Post by QDR06VV9 on 2015-05-16
So it is always good to report if it was normal install or cloned that could and dose in this case make a difference.
> Partition 3 does not start on physical sector boundary
Thats bit past my experience though, but this shows promise [http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)
Regards

---

### Post by Bucky Ball on 2015-05-16
```
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 411647 204800 7 HPFS/NTFS/exFAT
/dev/sda2 411648 1219397759 609493056 7 HPFS/NTFS/exFAT
/dev/sda3 1219399678 1424185343 102392833 5 Extended
**Partition 3 does not start on physical sector boundary.**
/dev/sda4 1424185344 1465149167 20481912 2 XENIX root
/dev/sda5 1219399680 1220411391 505856 83 Linux
/dev/sda6 1220413440 1243029503 11308032 82 Linux swap / Solaris
/dev/sda7 1243031552 1301616639 29292544 b W95 FAT32
/dev/sda8 1301624832 1360216063 29295616 83 Linux
/dev/sda9 1360218112 1424185343 31983616 83 Linux
```

The one in bold is an issue. The other drive may not have been failing. If this was cloned directly from another drive, it may just have been this issue. Start having a dig for 'Partition does not start on physical sector boundary ubuntu' and you should find plenty. I'll have a quick look also. It may be a Win issue which may need to be fixed with Win tools. Can't remember. Be back ...

PS: Just for clarity, you were doing a regular update, not an upgrade to a new release, when this occurred? Which release are you using? Just wondering if the two issues are related ...

---

### Post by karat on 2015-05-16
I'm going to try gparted from a 12.04 liveInstall DVD.

---

### Post by Bucky Ball on 2015-05-16
Yep, that would be the way to do it. Either resize that partition or delete and recreate it. If you can back it up, I'd delete and recreate. 

[This]("http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary") link gives some info. Good luck.

Hmm, hold it, though. sda3 is the extended partition. Might be best to resize after all, but that could be difficult because there's no room at the beginning of the partition to resize into (and you can't shrink it probably). 

Have you got a clone of the whole disk or did you do it a partition at a time? If you did a partition at a time, the other option would be to delete the extended partition, recreate it, check that all is well this time, THEN add the logical partitions and data back inside the extended. :-k

---

### Post by karat on 2015-05-16
Well, there's 4 MB of unused space at the end of that partition, so I can slide everything over.

The problem I'm having now is that I can't boot from any of my LiveInstall disks.  Error: File not found.  I was able to boot from one of them just 2 weeks ago.  I remember having a problem burning the disks because of the recursive Ubuntu file.

Ugh.  Yak-shaving.  Is it better to start another thread with a different issue or try to discuss it here?

---

### Post by oldfred on 2015-05-16
The extended partition does not have to start on a boundry. Only the partitions you actually write into or all the logical partitions inside the extended should. And that is only a requirement if your drive is the new 4K or SSD. Yours is a new 4K drive.

       Partition 4 does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Not sure if part of issue or not, but sda4 shows are NTFS, but partition table is type 2 Xenix. It should also be type 07. You can use Disk Utility or command line to reset to 07, but do not format, just change type.

You have grub installed to lots of partitions. That normally is not correct, but should not otherwise cause issues. Only the install to MBR is critical.

It says grub installed correctly and above it said it used /boot partition:

```
Reinstall the GRUB of sda8 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
```

---

### Post by karat on 2015-05-16
Right now, I'm trying to figure out why I can't boot from a live ubuntu disk so that I can run gparted.  I get the following:

kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)

I found another thread with this issue, but they could boot off the live disk and not the hard drive.  I have it backwards.

(Also, sda4 is the manufacturer bloatware partitition.  I ignore it because it is small.  I don't really consider it an issue.)

---

### Post by karat on 2015-05-16
Here is a summary of the problem:

I used to be able to boot from a LiveCD as of a week ago, but now I can't.  What has changed since then is that I cloned and replaced my hard drive.  Since the cloning process, some partitions now start in the middle of a sector.  I have also successfully updated grub.  I am now trying to boot from a LiveCD to use gparted.  However, the LiveCD that booted before now doesn't.  I get into the LiveCD's grub menu, but whichever option I pick, I now get an "Error: Can't read file", followed by "kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)".

The only thing that has changed is the hard drive.  Could that be causing the LiveCD to fail to boot?  Is it possible that the older LiveCD can't handle the newer hard drive?

One more thing.  I had an old thread on here (from several years ago) possibly on this same problem.  I can't find it when I look at my profile and look at my activity.  I believe I had a similar problem once, which may or may not be related, and the issue was the Ubuntu directory that pointed to itself.

Would burning a newer DVD help?  How about a thumb drive?

---

### Post by oldfred on 2015-05-16
Are you sure you are booting live CD?

Live CD does not have grub menu, unless booting in UEFI boot mode.
So either you switched from BIOS to UEFI (is system newer and has UEFI?) or LiveCD is not booting at all and it just switches to hard drive to boot.
Hard drive should not change whether CD works or not.

---

### Post by karat on 2015-05-16
> **oldfred said:**
> Are you sure you are booting live CD?

Live CD does not have grub menu, unless booting in UEFI boot mode.
So either you switched from BIOS to UEFI (is system newer and has UEFI?) or LiveCD is not booting at all and it just switches to hard drive to boot.
Hard drive should not change whether CD works or not.

I am absolutely sure that the live CD boots a screen that says "grub" with options to "try ubuntu without installing", "install ubuntu", and "check disk for errors".  That menu is the menu I am referring to.  I am not always precise in my terminology, and I admit that I could have said something imprecisely that has caused some confusion, but I am sure that it is not the HD grub menu.

The hard drive *is* changing whether CD works or not, whether or not it should.  I genuinely don't know why.  Could it be trying to mount the hard drive and failing due to the partitions being unaligned or missing drivers?

Also, I get the problem with Ubuntu 16.04 beta (or so my friend told me the version was) on a thumb drive I borrowed, so changing that doesn't help either.

---

### Post by karat on 2015-05-17
Okay, I checked the bios settings, and UEFI was set to enabled.  Disabling it allowed the liveCD to boot.  Now, I can't go back in time to check the settings before, but I know it booted before I swapped the hard drives, so something in the process of cloning and swapping drives did change something.  (I swear I remember seeing it boot the LiveCD in UEFI mode and give me the grub menu before too, but I can't verify that and wouldn't bet my life on it.)

However, I still have a problem booting from the USB stick, but it looks like it is missing files (and it's not my USB stick, so I'm not messing with it).

Anyway, this allowed me to run gparted, move around the partitions a bit, and fdisk is now happy.  As long as I don't worry about the USB stick which worked for my friend and not me, I am considering this solved.

PS Any ideas why the USB stick would complain about missing files for me and not for my friend?

---

### Post by karat on 2015-05-17
> **Bucky Ball said:**
> ```
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 411647 204800 7 HPFS/NTFS/exFAT
/dev/sda2 411648 1219397759 609493056 7 HPFS/NTFS/exFAT
/dev/sda3 1219399678 1424185343 102392833 5 Extended
**Partition 3 does not start on physical sector boundary.**
/dev/sda4 1424185344 1465149167 20481912 2 XENIX root
/dev/sda5 1219399680 1220411391 505856 83 Linux
/dev/sda6 1220413440 1243029503 11308032 82 Linux swap / Solaris
/dev/sda7 1243031552 1301616639 29292544 b W95 FAT32
/dev/sda8 1301624832 1360216063 29295616 83 Linux
/dev/sda9 1360218112 1424185343 31983616 83 Linux
```

The one in bold is an issue. The other drive may not have been failing. If this was cloned directly from another drive, it may just have been this issue. Start having a dig for 'Partition does not start on physical sector boundary ubuntu' and you should find plenty. I'll have a quick look also. It may be a Win issue which may need to be fixed with Win tools. Can't remember. Be back ...

PS: Just for clarity, you were doing a regular update, not an upgrade to a new release, when this occurred? Which release are you using? Just wondering if the two issues are related ...

For reference, I was doing a regular update, not an upgrade to a new release.  This was with 14.04.  I was using a 12.04 LiveCD, though.

I also believe the drive was failing because it worked fine for years but suddenly started failing to boot.  However, it would boot after the drive was warmed up for 5-15 minutes (or maybe just many retries, but waiting for a while and rebooting seemed to work well).  I haven't booted up the old drive to check it, but I certainly never noticed an error with fdisk before, and I noticed it pretty quickly on the new drive -- which is why I posted it.  So, I have reason to believe this only cropped up in the cloning process (or now that I think about it, if the old drive were cylinder-aligned, I suppose that could maybe cause this too).

Anyway, thanks for everyone's help, especially Oldfred -- disabling UEFI did help.

---

### Post by oldfred on 2015-05-17
Glad you got it resolved.

Part of reason I just prefer new installs. But with Windows that is tricky and you have to usually clone it if moving to a new drive. But Ubuntu installs and you can copy /home, re-install apps and be back to a working system very quickly.

But if system is newer and has both UEFI & CSM/BIOS, you must be consistent on how you boot. And how you boot installer both Windows & Ubuntu is then the boot mode it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by karat on 2015-06-04
Update hit the same problem again:

Installing for i386-pc platform.
grub-install: error: cannot find a GRUB drive for /,.  Check your device.map.

I fixed a number of problems, but not the original problem.

[Moderators: Please let me know if I should start another thread.]

---

### Post by oldfred on 2015-06-04
Ok to be same thread, just so those that review things know what has been done.

Is sda4 really a Xenix partition? Partition tools, grub and many be few other things want to review partition table and mount to search for bootable systems or system to mount even if not mounting them now. If type is wrong then that causes issues.
If really NTFS, you can use Disks or command line just to change type (not reformat) to 07. If really something else you have to know what it should be.

---

### Post by karat on 2015-07-24
> **oldfred said:**
> Ok to be same thread, just so those that review things know what has been done.

Is sda4 really a Xenix partition? Partition tools, grub and many be few other things want to review partition table and mount to search for bootable systems or system to mount even if not mounting them now. If type is wrong then that causes issues.
If really NTFS, you can use Disks or command line just to change type (not reformat) to 07. If really something else you have to know what it should be.

Well, gparted thinks it is an NTFS partition, but there doesn't seem to be a way to change the type to 07.  Yes, fdisk still thinks the type is 02.

1) Is there a non-destructive way to change this, since this partition contains my backup software?  Every method I've seen is destructive.
2) I am far from convinced this is relevant, so I'm not going to do any destructive operations.  Where could my system be thinking \, is a drive name?

---

### Post by oldfred on 2015-07-24
Just use Disks and change type, not format. Use little gear or stars icon for more actions. Edit partition and change type.

Or command line for MBR(msdos drives):
       change sda4 to type 07
sudo sfdisk --change-id /dev/sda 4 7
see also
man sfdisk

---

