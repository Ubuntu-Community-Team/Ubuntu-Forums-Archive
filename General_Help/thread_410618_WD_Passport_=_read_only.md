---
title: "WD Passport = read only"
date: 2007-04-15
forum: General Help
---

### Post by ar1stotle on 2007-04-15
Hello all. Well, I have a 120gb WD Passport. It's formatted with FAT32, so it should be readable and writeable by Ubuntu. However, when I plug it in, it automounts itself but it's read only. From looking on these forums, it seems you might ask for the output of fdisk -l, so I'll paste it below. I'd appreciate any help!

```
Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    c  W95 FAT32 (LBA)
```

---

### Post by Famicommie on 2007-04-15
Try running the following command in a terminal:
```
sudo chmod -R 777 /dev/sdc1
```

---

### Post by ar1stotle on 2007-04-16
All that seemed to do was enable the context menu entries for creating files and folders, but I still get an error about it being read only.

---

### Post by ar1stotle on 2007-04-16
Anything else to try?

---

### Post by Famicommie on 2007-04-17
What is the output of ```
mount -l
```?

---

### Post by ar1stotle on 2007-04-17
```
aristotle@Tsunami:~$ mount -l
/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda3 on /media/hda3 type vfat (rw,utf8,umask=007,gid=46) []
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdc1 on /media/WD Passport type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8) [WD Passport]
```

---

### Post by ar1stotle on 2007-04-19
Still need some assistance :-/

---

### Post by lemonfriend on 2007-04-23
Sorry no assistance, only solidarity. I've got the same problem.
It used to work fine for the first weeks after I purchased it, but the drive is read-only since two weeks or so.
Can it have to do with one of the latest updates to dapper ?

---

### Post by ar1stotle on 2007-04-23
Grrrr, I saw the ro option in the properties for the drive, so I just tried adding in rw (thinking it was read-write). Well now, whenever I plug it in I just get this message saying "Invalid mount option when attempting to mount the volume 'WD Passport'."

Any idea how I can remove that parameter? I just right clicked on it on the desktop and went to properties-->volume-->settings and added it to mount options, which I suppose I shouldn't have done.

Edit: Yay, I figured it out and fixed the problem! If you go to places-->computer I could right click the drive and change the properties again. After removing the rw from the mount options, it mounts fine, AND I can write to it!

---

