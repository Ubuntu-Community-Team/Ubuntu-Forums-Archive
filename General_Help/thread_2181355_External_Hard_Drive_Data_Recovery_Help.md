---
title: "External Hard Drive Data Recovery Help"
date: 2013-10-17
forum: General Help
---

### Post by 3K8spPx on 2013-10-17
Hi all,

I recently tried to access my Seagate FreeAgent Go 320GB external hard drive using Windows 7 on my laptop and when trying to access and delete a folder, the problems began. Whenever I tried to plug in the HDD and access it via My Computer, explorer would crash. I tried running chkdsk but that ran for hours on end but still didn't work. So I downloaded and made a live version of Ubuntu on my 8GB USB pen and booted from there. Upon which I get this error message:

> **Unable to Mount User's FreeAgent Drive**

Error mounting /dev/sdc1 at /media/ubuntu/Users's FreeAgent Drive: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdc1" "/media/ubuntu/Users's FreeAgent Drive"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page.
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sdc1: Input/output error
Failed to close volume /dev/sdc1: Input/output error



I have tried googling for various solutions but many did not help as they were slightly different to my situation when I followed the first few steps so I am starting here.
I haven't used linux in years so consider me an absolute beginner, thanks in advance.

---

### Post by whitesmith on 2013-10-17
Seagate has utilities for verifying health of their HDDs. FreeAgents seem susceptible to shock damage. I's suggest you begin with that. Cheers.

---

### Post by 3K8spPx on 2013-10-17
Thanks for your reply, when I installed a free trail of the software that seagate are offering to recover data, they have warned me that attempting to recover data from a drive with physical damage could potentially end up in further data loss. Is there no other way using linux to attempt to recover my data? I'm just treading carefully before doing further harm to my drive. (Note: I'm not fully sure if my drive has physical damage, does the symptoms I've described above indicate that there is physical damage?)

Note: I decided to bite the bullet anyway and attempt to at least start this program and see what the process is like, at first I started it up without having the hard drive in question plugged in then I restarted the program after I plugged in the HDD, then it crashed. I'm starting to think that this is a physical problem, is there any hope of recovering data using ubuntu?

---

