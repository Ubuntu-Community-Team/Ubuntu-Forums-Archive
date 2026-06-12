---
title: "Storage partition of internal hard disk not accessible after a win7 reinstall failure"
date: 2013-04-25
forum: General Help
---

### Post by maryam123 on 2013-04-25
Recently I had problems with my laptop and thought of reinstalling win7. But then the reinstall caused some problems and then switched to ubuntu. I can see my harddisk but it says unable to mount location and can't mount file. I'm a very first user of ubuntu and need urgent help.

---

### Post by Mark Phelps on 2013-04-25
Unfortunately, you've given us no details to use ...

HOW did you try to do the Win7 reinstall?

What do you mean "then the reinstall causes some problems and then switched to Ubuntu"?  What were the problems? What did you do?

Where are you "seeing your hard disk"? 

What location are you trying to mount?

NOTE: We're not mind readers here -- we need details.

---

### Post by maryam123 on 2013-04-26
It's cause I'm a novice failed to include all the details required. 
My hard disk has two partitions: c drive on which the windows was installed and d drive for storage only.
Tried to reinstall windows on c drive but it caused some error and didnt install properly and was left with out a functioning operating system.
Booted using a bootable pendrive with ubuntu. 
Somehow ubuntu got installed in harddrive which I didn't intend to. Where exactly I don't know. Had no idea of ubuntu then.
hard disk is visible in Dash Home as 320Gb Hard Disk but says unable to mount location, can't mount file
Thanks for the reply.

---

### Post by maryam123 on 2013-04-26
sorry not in Dash home. It's from the menus Go above Dash Home in My Computer

---

### Post by maryam123 on 2013-04-27
this is what 'mount' gives in terminal
/dev/sda1 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/maryam/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=maryam)

---

### Post by maryam123 on 2013-04-27
and _ls -l /dev/sda*_ gives
brw-rw---- 1 root disk 8, 0 Apr 26 15:10 /dev/sda
brw-rw---- 1 root disk 8, 1 Apr 26 15:10 /dev/sda1
brw-rw---- 1 root disk 8, 2 Apr 26 15:10 /dev/sda2
brw-rw---- 1 root disk 8, 5 Apr 26 15:10 /dev/sda5

---

### Post by maryam123 on 2013-04-27
and _sudo fdisk -l /dev/sda_ gives

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002dcd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   618995711   309496832   83  Linux
/dev/sda2       618997758   625141759     3072001    5  Extended
/dev/sda5       618997760   625141759     3072000   82  Linux swap / Solaris

---

