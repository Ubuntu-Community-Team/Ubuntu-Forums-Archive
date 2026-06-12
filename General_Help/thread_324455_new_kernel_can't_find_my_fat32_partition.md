---
title: "new kernel can't find my fat32 partition"
date: 2006-12-23
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-23
I have compile the kernel 2.6.19.1 and success.
But there is still a problem.It can not mount my fat32 partition.
It show this argument iso8859-1 .

---

### Post by taurus on 2006-12-23
What happens when you run this command from a terminal, Applications -> Accessories -> Terminal?

```
sudo fdisk -l
```
Otherwise, you need to go back and build it again, enabling vfat in the kernel...

---

### Post by LaoLiulaoliu on 2006-12-23
It show that  FAT: IO charset iso8859-1 not found
when I use
sudo fdisl -l 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021       10011    72220207+   f  W95 Ext'd (LBA)
/dev/sda5            1021        3637    21021021    7  HPFS/NTFS
/dev/sda6            3638        6187    20482843+   7  HPFS/NTFS
/dev/sda7            6188        8737    20482843+   b  W95 FAT32
/dev/sda8            8738        9884     9213246   83  Linux
/dev/sda9            9885       10011     1020096   82  Linux swap / Solaris

---

### Post by taurus on 2006-12-23
What happens if you run these two commands, especially the second one?

```
sudo mkdir /media/share
sudo mount -t vfat /dev/sda7 /media/share -o iocharset=utf8,umask=000
```

---

### Post by LaoLiulaoliu on 2006-12-23
In the document share all the files and folders in sda7 come back
Thank you very much!
Can I mount them in sda7?

---

### Post by taurus on 2006-12-23
You mean you want to mount /dev/sda7 to /media/sda7!  

```
sudo umount /dev/sda7
sudo mkdir /media/sda7
sudo mount -t vfat /dev/sda7 /media/sda7 -o iocharset=utf8,umask=000
df -h 
```
Otherwise, edit your /etc/fstab
```
gksudo gedit /etc/fstab
```
and add this line to the end so it will be mounted each time you boot into Ubuntu...

```
/dev/sda7   /media/sda7   vfat   iocharset=utf8,umask=000   0   0
```

---

### Post by LaoLiulaoliu on 2006-12-23
I will say thank you to express my appreciation.
Happy Christmas Eve!

---

