---
title: "NTFS USB Issues"
date: 2013-01-27
forum: General Help
---

### Post by d4m1r on 2013-01-27
Hey guys, have been having serious issues transferring files to an external USB stick of mine (2GB, NTFS) lately under Ubuntu 12.04. The stick works fine under Windows and I can even read files from it under Ubuntu, but as soon as I write something to it, it corrupts the filesystem :confused:

Basically, it mounts fine and I can copy/read files from the USB stick but when I paste a file to it for example, I get the below window after I click the dismount button:

[IMG]http://i.imgur.com/dRmam2rl.png[/IMG]

^It basically plays in a loop and never completes (10-15 minutes) so you just pull the USB out, but when you put it back in, you get the below error and the file system is corrupt, meaning you lost all your files :(

[IMG]http://i.imgur.com/3RZCV6Ml.png[/IMG]

It's weird because if I dismount the drive from sudo'd nautilus, I don't get the 1st window but still get the 2nd error when I try to mount it again....As well, I have 2 internal NTFS harddrives (SATA 2) that get automatically mounted at boot and I can read/write to those just fine....

---

### Post by d4m1r on 2013-01-27
100 views and no suggestions? :(

I also forgot to post the output of "sudo apt-get ntfsfix /dev/xxx" which was a suggested troubleshooting tip I found online:

```
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
The alternate bootsector is usable
Set sector count to 3913988 instead of 3913925
Rewriting the bootsector
The boot sector has been rewritten
ntfs_mst_post_read_fixup_warn: magic: 0xe384910e  size: 1024   usa_ofs: 39399  usa_count: 32751: Invalid argument
Record 0 has no FILE magic (0xe384910e)
Failed to load $MFT: Input/output error
Volume is corrupt. You should run chkdsk.
```

---

### Post by The Spectre on 2013-01-27
Try formatting the flash drive FAT32 to see what happens.

NTFS really isn't the ideal file system to use on a 2 GB flash drive anyways.

---

### Post by d4m1r on 2013-01-27
FAT32 may or may not work better but that is beside the point as I explicitly want to get NTFS USB drives working under my Ubuntu partition....The fact that it is a 2GB stick in this case shouldn't matter either as I have 16GB+ sticks as well...

---

### Post by sammiev on 2013-01-27
Format the USB stick and try it again. It should work with Ubuntu again.

---

### Post by d4m1r on 2013-01-27
> **sammiev said:**
> Format the USB stick and try it again. It should work with Ubuntu again.

Format the USB stick under which OS? I've tried that multiple times and the stick was healthy each time after the reformat...Until I copied some files to it again.

---

### Post by divergex on 2013-01-27
In my experience flash drives that behave that way are always close to death and data loss. USB flash drives can be very flaky, and I have seen brand new drives where two out of three identical capacity and branded drives work fine and the third doesn't. They are kind of like light bulbs - sometimes you get a bad one, and there's no figuring out what's wrong. I have had drives that work on one computer but not another, every time. I even had a Sony drive that refused to work in a Sony laptop, but worked great everywhere else.

I would get whatever data I could off the drive, then format the drive under Windows (full format, not quick), then physically destroy the drive.

I have a drive like yours. It's a 16GB Sandisk that doesn't like to mount under Ubuntu. I always have to mount it manually under Disk Utility. The other day I plugged it into a Vista box and it wanted to format the drive. I unplugged it and put it in again and it was then recognized. Needless to say I will not be trusting this drive to keep any of my data safe.

---

### Post by The Spectre on 2013-01-28
Maybe the USB Port on that Ubuntu PC is the problem.

Did you try plugging the Flash Drive into a Different USB Port on that Computer?

---

### Post by d4m1r on 2013-01-28
> **The Spectre said:**
> Maybe the USB Port on that Ubuntu PC is the problem.

Did you try plugging the Flash Drive into a Different USB Port on that Computer?

I did, but this is definitetly not a hardware problem with either the stick or the USB port because both work perfectly fine under Windows 7....It is a problem with Ubuntu writing to NTFS USB drives....

---

### Post by sammiev on 2013-01-28
I went into Dash and select "Disk" and choose my USB drive. Then I selected more actions and formated the USB pen. It was the only program in Linux that would format the pen. Gparted did not work which surprised me.

---

