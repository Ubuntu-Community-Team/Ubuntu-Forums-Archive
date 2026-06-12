---
title: "Ubuntu LIve 12.04 cd 32 bit - fsck: fsck.ntfs: not found"
date: 2013-09-20
forum: General Help
---

### Post by lars3 on 2013-09-20
im trying to remove som bad sectors on a harddrive using Ubuntu LIve 12.04 cd 32 bit live boot from cd.

The harddrive is NTFS. i can mount the partition and have full read / write access.

to find badsectores i use "sudo badblocks -v /dev/sda1 > bad-blocks" and it finds 12 bad sectores.

to remove the bad sectores i write "sudo fsck -t ntfs -l bad-blocks /dev/sda1" but the system gives me error

fsck from util-linux 2.20.1[FONT=arial black][FONT=arial][/FONT][/FONT]
fsck: fsck.ntfs: not found 
fsck: Error 2 while executing fsck.ntfs for /dev/sda1

i tried

sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs
sudo ln -s /usr/bin/ntfsfix /usr/sbin/fsck.ntfs-3g

still the same error "fsck: fsck.ntfs: not found"

i then tried "sudo apt-get install ntfsprogs" but it says that this might be better ntfs-3g but the live boot has the newest version.

so no chances in that.

what can i do to to make the system find fsck.ntfs so i can repair my harddrive and remove the bad sectors...

and before u say that ubuntu is not a Windows scan tool, i dont care i just want to remove the bad sectores out of usability.

---

### Post by dcstar on 2013-09-20
The badblocks man page says it was written for the EXT filesystems, I would have serious doubts that it will work for NTFS.

---

### Post by oldfred on 2013-09-21
You can only run chkdsk from Windows and you need to run chkdsk. If you do not have Windows you probably should not be using NTFS. You can use a Windows repairCD or flash drive. I have used a Windows 7 flash drive to run chkdsk on my XP install, but it converted PBR- partition boot sector to Win7 type and I also had to convert back to XP type.

Some third party Windows partitioning tools may also run chkdsk.
       Third party chkdsk tools
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

