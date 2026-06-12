---
title: "Mounting reiserfs partition"
date: 2007-04-28
forum: General Help
---

### Post by pundip on 2007-04-28
I am having trouble mounting a slave disk. I have formated it as reiserfs /dev/hdb
I can get it to mount and i havent found a thread that shows me how. This drive used to be a windows 98 partition that i have formated after installation.  I would appreciate any help re mounting this drive. I would have thought this was a simple thing to do. Its almost easier to mount a ntfs drive under linux. My distro is Xubuntu  and please keep in mind that i am very new to linux. 
Here is my  /etc/fstab  file
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=896472c0-a63a-4c83-ad60-10a8eafa2e54 /               ext3    defaults,erro$
# /dev/hda5
UUID=ef7ffbd8-7c50-4993-b99c-6a4c797092be none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
 fdisk -l

```

Disk /dev/hda: 6440 MB, 6440394752 bytes
255 heads, 63 sectors/track, 783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         746     5992213+  83  Linux
/dev/hda2             747         783      297202+   5  Extended
/dev/hda5             747         783      297171   82  Linux swap / Solaris

Disk /dev/hdb: 1281 MB, 1281982464 bytes
255 heads, 63 sectors/track, 155 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         155     1245006   83  Linux

```
mount 
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)

```

---

### Post by spd106 on 2007-04-29
Assuming you have created a /media/sdb1 directory, does this command work?
```
sudo mount -t reiserfs /dev/sdb1 /media/sdb1 
```

If so you can add it to your fstab, to find the uuid use this command
```
sudo vol_id -u /dev/sdb1
```

---

### Post by pundip on 2007-05-07
Thanks a lot for that. It seems to have done the trick. The drive is now mounted.

---

