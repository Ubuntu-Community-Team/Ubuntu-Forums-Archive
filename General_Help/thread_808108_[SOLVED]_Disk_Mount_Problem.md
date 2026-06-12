---
title: "[SOLVED] Disk Mount Problem"
date: 2008-05-26
forum: General Help
---

### Post by gus_zernial on 2008-05-26
My kubuntu system has a system disk (two physical disks in software raid) and an "extra" disk I want to mount on boot. The extra disk is in /etc/fstab as follows

/dev/sdc1  /mnt/DevSDC ntfs atime,rw,exec,auto,dev 0 0

the problem is, sometimes the extra disk shows up as /dev/sdc, in 
which case it mounts correctly, but other times the device naming
order changes and the extra disk shows up as /dev/sda, in which
case it doesn't mount automatically (I can always mount it manually 
using the correct device name). 

I can't figure out any pattern as to why the extra disk's name
changes. Is there a way I can force device naming so the extra 
disk comes up the same way each time?

---

### Post by nick_h on 2008-05-26
Mount it using UUID or LABEL instead of by device name.

For details on how to do this read this thread - [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131).

To change the label of a volume see - [RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive).

---

### Post by wootah on 2008-05-26
Yes, mounting using the UUID should fix it. If it does, don't forget to mark as solved :)

---

