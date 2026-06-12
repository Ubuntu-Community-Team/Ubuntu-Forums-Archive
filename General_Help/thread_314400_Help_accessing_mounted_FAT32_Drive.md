---
title: "Help accessing mounted FAT32 Drive"
date: 2006-12-07
forum: General Help
---

### Post by Meatpuppet on 2006-12-07
Hello,

I am very much a Linux newbie.  I just setup a dual boot (Edgy, XP) system.  My partitions are as follows (in order):
XP-NTFS-15GB
Shared space-FAT32-260GB
Edgy-15GB-EXT3
Swap-2GB

The issue I am having is that I can access the FAT32 partition in XP but not in Edgy.  

Here is the output of mount:

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda2 on /shared type vfat (rw,iocharset=utf8,umask=000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

The shared FAT32 space I am trying to access is /dev/hda2 and as you can see it is mounted.  The Gnome Partition Editor sees it and shows it mounted and formatted as FAT32 as well.

My ultimate goal is to have an icon on my ubuntu desktop that links me to the contents of the shared data on /dev/hda2.  So I can share mp3s and other data between operating systems

Can anyone tell me how to do this?

Thank you! [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by rpkehoe on 2006-12-07
double check to make sure you have the address correct and that it is not /dev/hda4 or something. unmount the fat32 sudo umount /dev/hda2 then remount mount /dev/hda2 /shared then create the link sudo ln /~/Desktop/shared /shared

---

### Post by bodhi.zazen on 2006-12-07
rpkehoe's technique with a link will work.

"traditional" solutions is:

First umount the shared partition```
sudo umount /dev/hda2
```

Now move the mount point to /media
```
sudo mv /share /media/share
```

Update fstab:> /dev/hda2 /media/shared vfat auto,users,iocharset=utf8,umask=000 0 0

Re-mount:```
mount /media/share
```

---

### Post by Meatpuppet on 2006-12-07
Thank you guys very much.  I now have a shortcut that will allow me to access the shared space.  My only problem now is that in Ubuntu I can not write to the partition.  I can only read.  What do I need to do to allow full access to that space?

Thanks again!

---

### Post by bodhi.zazen on 2006-12-07
(re)post fstab 

/etc/fstab

If you have the option umask=000, unount and remount the partition.

And chmod 777 ~/Desktop/shared

---

### Post by strabes on 2006-12-07
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

