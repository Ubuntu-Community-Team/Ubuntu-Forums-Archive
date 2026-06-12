---
title: "Fsck log file missing Root and Home"
date: 2013-03-27
forum: General Help
---

### Post by SuperFreak on 2013-03-27
I set up autofsck to run on shutdown. I found the log output of this in var/log/boot.log which I have partially shown below. I am wondering if my SSD is healthy as it contains the Root (sda 3)and Home partitions (sda4) but I don't see these partitions listed in the log. sda1 is the EFI boot patition. Documents and Music are on another hard drive.How do I get log records for the missing partitions?
```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:45/20, 72:46/20, 73:49/20, 78:00/20, 79:00/20, 80:00/20, 81:00/20
  Not automatically fixing this.
/dev/sda1: 13 files, 1619/504090 clusters
Documents: clean, 24087/64004096 files, 17852787/256000000 blocks
Music: clean, 60575/178028544 files, 189131378/712105472 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Starting mDNS/DNS-SD daemon[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting network connection manager[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting crash report submission daemon[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ]
Running MusicMagicServer
Making sure that Logitech Media Server is not running first: No process in pidfile '/var/run/logitechmediaserver.pid' found running; none killed.
Starting Logitech Media Server.
```

The fsck log reads "(Nothing has been logged yet.)"

---

### Post by dcstar on 2013-03-28
fsck can only run correctly on unmounted file systems. Since the root and home filesystems are required to be mounted until the system shuts down it is basically impossible for fsck to run at that time on those filesystems.

---

### Post by SuperFreak on 2013-03-28
Thanks,

I guess I thought that was the way autofsck worked. The computer shut down and fsck ran at some point just before the power shut down. I am using a UPS I wonder if that might be an issue

edit: I ca try Fsck from a live disk I guess

---

### Post by SuperFreak on 2013-03-28
I ran a Live USB and my Root and Home partitions are clean, but there seems to be a problem with the EFI partition? Can someone please have a look at the output from my Live USB terminal below and tell me if I need to take any action. I believe sda2 is actually not used for anything:


```
root@ubuntu:/home/ubuntu# fsck /dev/sda3
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
ROOT: clean, 316850/2162688 files, 3960451/8650752 blocks
root@ubuntu:/home/ubuntu# fsck /dev/sda4
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
HOME: clean, 50572/2621440 files, 1262720/10485760 blocks
root@ubuntu:/home/ubuntu# fsck /dev/sda1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:45/20, 72:46/20, 73:49/20, 78:00/20, 79:00/20, 80:00/20, 81:00/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sda1: 13 files, 1619/504090 clusters
root@ubuntu:/home/ubuntu# fsck /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/home/ubuntu# 
```

---

### Post by Bashing-om on 2013-03-28
SuperFreak; Hi !

Your sda1 partition appears to be a Windows partition, best looked at with Window's tools.
Let's look and see what ubuntu sees as your disk structure:
```
sudo fdisk -lu
``` And we will know better how/what to advise.[INDENT=3]
my opinion, for what it is worth

[/INDENT]

---

### Post by SuperFreak on 2013-03-28
I know that sda1 is  a FAT32 partition but it is my EFI boot partition. I don't use windows on this machine only Ubuntu and the EFI partition was set up according to directions from OldFred for booting from UEFI Bios under Ubuntu. Perhaps the Fsck readout for Sda1 does not mean anything as it is not in a Linux format.


Here is the output  of sudo fdisk -lu  

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

```

---

### Post by Bashing-om on 2013-03-28
SuperFreak;

That is a step in the right direction. As you can see the disks are in GPT format. "fdisk" can not deal with that format, other tools exist to handle the GPT formats. I have no experience with it so must take a back seat, Others with greater knowledge will advise.
[INDENT=2]
still learning

[/INDENT]

---

### Post by SuperFreak on 2013-03-28
Thanks Bashing-om

Perhaps I am concerned over a non issue. Hopefully someone will clarify the matter

---

### Post by SuperFreak on 2013-03-29
Bump

from googling fsck it appears fsck does read FAT32. Should I try to repair my EFI partition. If so how do I do this safely if the above post of my sda1 output does indicate a problem?

---

### Post by dcstar on 2013-03-30
> **SuperFreak said:**
> Bump

from googling fsck it appears fsck does read FAT32. Should I try to repair my EFI partition. If so how do I do this safely if the above post of my sda1 output does indicate a problem?

An EFI partition is a special partition - there is nothing to "fix" and it is probably extremely dangerous to even try to touch it.

If there are no problems then DO NOT muck around with things!

---

### Post by SuperFreak on 2013-03-30
Thanks

---

### Post by Jay_E on 2013-03-30
Greetings:

Might want to look for bug list in your version of ubuntu
like
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

(Debian had reported bugs in grub writing to the correct device.  (Oh my.)  )

Or take a look in here:
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
Lots and lots and lots..... of uefi problems

I had re-installed Debian - with an ext2 /boot/uefi partition
Raring 13.04 installed OK too.
But I used Darik's Boot and Nuke (DBAN) to clean out old boot records..

I prefer to do fsck the old-fashion way - by doing a touch /forcefsck
and in each filesytem.

I put this in root's cron file
```

# m  h  dom mon dow   command
 59 11   *   *   6    touch /forcefsck; touch /home/forcefsck

```

This will run fsck during boot on Saturdays - or the next time after that when you re-boot.

I do agree with dcstar, I do not run fsck on the boot partition.

Have fun,
Jay


stop the bleeding.
protect the wound.
treat for shock.

---

### Post by SuperFreak on 2013-03-30
Thanks Jay_E

will leave well enough alone

---

