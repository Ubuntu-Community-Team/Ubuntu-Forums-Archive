---
title: "Please help, After update Dapper doesn't boot"
date: 2007-02-16
forum: General Help
---

### Post by R2D2-Master on 2007-02-16
Hi thanks in advance.

I pressed the update button in the normal Dapper update notice on top, there were a kernel update on the list, when i reboot like it asked i got the following error.

It updated the kernel to version 2.6.15-28-386

I were running Ubuntu now for a year pressing the update button everytime it comes up this never happend i did do 1 upgrade from previous Ubuntu version to Dapper also.

"Kernel panic - not syncing: VFS: unable to mount root fs"

I have searched for a while, all the things a find didn't work yet.

This is an important computer if someone can help me fix this.

Here is the output of fdisk from live Dapper cd 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  fd  Linux raid autodetect
/dev/sda2               7         128      979965   fd  Linux raid autodetect
/dev/sda3             129        1344     9767520   fd  Linux raid autodetect
/dev/sda4            1345        9729    67352512+  fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           6       48163+  fd  Linux raid autodetect
/dev/sdb2               7         128      979965   fd  Linux raid autodetect
/dev/sdb3             129        1344     9767520   fd  Linux raid autodetect
/dev/sdb4            1345        9729    67352512+  fd  Linux raid autodetect

Disk /dev/md0: 49 MB, 49217536 bytes
2 heads, 4 sectors/track, 12016 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 10.0 GB, 10001842176 bytes
2 heads, 4 sectors/track, 2441856 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 68.9 GB, 68968906752 bytes
2 heads, 4 sectors/track, 16838112 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md3: 68.9 GB, 68968906752 bytes
2 heads, 4 sectors/track, 16838112 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table
ubuntu@ubuntu:/proc$

---

### Post by R2D2-Master on 2007-02-16
Update i am trying to mount the HD but it don't work.

ubuntu@ubuntu:/mnt/linux$ sudo mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
ubuntu@ubuntu:/mnt/linux$ sudo mount /dev/sda1 /mnt/linux
mount: /dev/sda1 already mounted or /mnt/linux busy
ubuntu@ubuntu:/mnt/linux$

And what is going on with this forum it doesn't remember that i am logged on i am having trouble posting on the forum. Asks the whole time for password and after it sais successfull and redirected i am log out again.

---

