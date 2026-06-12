---
title: "I cant mount my HDD(HP ST3320418AS (HP35)) on Ubuntu 13.04 Beta 64-bit"
date: 2013-05-04
forum: General Help
---

### Post by shaolinwarrior on 2013-05-04
Im unable to open any hard disk partitions.When i try to open ,  it shows the following error 

"Error mounting /dev/sda5 at /media/athul/78A2DAF5A2DAB6BA: Command-line  `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dm   ask=0077,fmask=0177" "/dev/sda5" "/media/athul/78A2DAF5A2DAB6BA"'  exited with non-zero exit status 14: The disk contains an unclean file  system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.".

 I have Windows 8 Pro 64-bit already installed and  i installed 13.04  two days ago by removing Ubuntu 12.10 32-bit.I had  the same problem  with previous 12.10 but for C drive only.Now the  problem is partially  solved after running some repairing options from  Advanced Options for  Ubuntu from GNU GRUB.But still im unable to browse  my Nokia C6-00  smartphone and other pendrives and flash drives. but im  able to connect  to internet with this phone as modem.But after booting Windows once  agian these errors came back.All these happend after i update Ubuntu and  it was working fine the dual boot before update.Can  anybody help me to  solve this problem and restore my access to phone and  other USB  Drives.Thanks in advance

---

### Post by dino99 on 2013-05-04
***** The disk contains an unclean file system (0, 0). *******

so you need to fix that issue first inside windows OS

---

### Post by Mark Phelps on 2013-05-04
You're trying to mount an NTFS volume and Linux won't let you do that because it thinks the filesystem is corrupted.

Unfortunately, there are no Linux equivalents of Windows CHKDSK -- which you will have to use to fix the filesystem.

This is typically caused when you simply turn off or remove an external drive, formatted NTFS, without "safely removing" that drive.

Sorry ... but you'll have to connect the drive to a Windows PC and run CHKDSK on it.

---

### Post by shaolinwarrior on 2013-05-28
thaks to all.i will try.

---

### Post by Mark Phelps on 2013-05-28
As an alternative, if you know someone with a Windows PC, have them download and burn the Minitool Partition Wizard Boot CD.

Then, boot from that and use the Check option against the partition in question.  That will run CHKDSK for you.

---

