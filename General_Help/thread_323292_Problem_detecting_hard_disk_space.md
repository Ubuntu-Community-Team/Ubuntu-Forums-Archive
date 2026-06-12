---
title: "Problem detecting hard disk space"
date: 2006-12-21
forum: General Help
---

### Post by Manuito on 2006-12-21
Hello,

I'm running Kubuntu from an external hard drive, where I have the following partitions:

/dev/sdb1    --    30.0 GB    --  ext3   ----     Kubuntu main install
/dev/sdb3   --     87.0 GB  --    ntfs     ----    Free space to share with Windows using NTFS-3G
/dev/sdb5    --      3.0 GB --    swap    ----    Swap partition

Windows is located in my internal hard drive (two partitions /dev/sda1 and /dev/sda2).

The problem comes when trying to learn the free space, used spaced, or total disk space on /dev/sdb1, which is mounted as "/". 

If I leave the mouse in the desktop over another device icon, even if it's a partition of the external hard drive (/dev/sdb3, for example, which is mounted as /media/usbdisk), a yellow window appears and I can clearly read all the information regarding disk space. If I click on properties I can also see a files and folders count, which is being continuously refreshed. Disk usage information for the two Windows partitions works also OK.

The problem comes when I try to do the same with my "/" icon. I get the same yellow window but all the data regarding disk space read "0 B" and the disk usage percentage is 0%. Then, if I click on properties, no files and folders are counted. If I click on "refresh" it starts to count the files and folders of my internal hard drive (/dev/sda) together with the files and folders of the internal hard drive (/deb/sdb), but there is no way to limit the count to /dev/sdb1.

All disk diagnosis programs I've tried are not able to give me a correct reading about the used and free space in the root folder. They all say "0 kb of a total of 0 kb used". Those who also get information about the swap partition, give me the same reading about it.

I'm talking about a completely fresh Kubuntu installation (to be honest I have installed it 3 or 4 times trying to solve the problem, but it comes again in every new install).

Fstab is standard for a new installation. 

The only difference I see compared to the last time I installed Kubuntu, one or two months ago, is that now Grub sets my external hard drives as /dev/hda instead of /dev/sdb in /boot/grub/menu.lst (I have to change it after the installation so that the system can boot, but then everything works correctly).

The system works perfect, hard drives are mounted without problems, I can access "/" as normal... you just know you've got a problem when you try to look at the disk usage. Kubuntu was running perfectly just one week ago with the same system, hardware and type of installation.


I hope someone can help, thanks for reading!!

Manuito

---

### Post by bapoumba on 2006-12-22
Hi,
**df -h** will show you dsik space usage.

---

### Post by Manuito on 2006-12-22
Thanks for the reply but, for some reason, it doesn't work properly.

**df -h ** returns the disk space for the Windows partitions (sda1 and sda5), the ntfs partition of the usb drive (sdb6) and the CDROM (hda), I cannot see anything about my ext3 linux partition (sdb1) and swap partition (sdb5).

```

df -h

/dev/sda1              20G   15G  5,0G  75% /media/sda1
/dev/sda5              55G   50G  5,2G  91% /media/sda5
/dev/sdb6              80G  128K   80G   1% /media/usbdisk
/dev/hda              698M  698M     0 100% /media/cdrom0
```

On the other hand, **fdisk -l** just gives information about my external drive (ext3 and swap partitions included), but nothing about the internal hard drive (even if it's correctly mounted and working).

```
fdisk -l

/dev/sdb1   *           1        3647    29294496   83  Linux
/dev/sdb2            3648       14593    87923745    5  Extendida
/dev/sdb5            3648        4255     4883728+  82  Linux swap / Solaris
/dev/sdb6            4256       14593    83039953+   b  W95 FAT32
```

If I take a look at System Setting / Advanced / Disk & Filesytems I can see all my hard drives at the bottom of the page. The two internal drives (sda1 and sda5) and the ntfs partition of the external drive (sdb6) have a green circle on the right side and it says "Enabled", but the partition where I have ubuntu (sdb1) and the swap partition (sdb5) are "Disabled" and have a grey circle on the right side.

I tried to enable them both being root but it says they are busy. System is working correctly. The only sympton you get about the problem is that you cannot monitor the disk space, as I said in the first post.


Thanks again for the help!!

---

### Post by bapoumba on 2006-12-22
Not sure I can help you all the way, but what is in your fstab ?
**cat /etc/fstab**.

---

### Post by Manuito on 2006-12-22
Thanks again for the reply.

```
**cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4900-4780  /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=A0A02710A026EC8A /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46                                                        0       1
# /dev/sda5
UUID=E0C4260FC425E88C /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46                                                        0       1
# /dev/sdb3
UUID=5215-7829  /media/usbdisk  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4efac4b0-f3bb-41d9-be39-3ed710953276 none            swap    sw                                                                     0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I discovered that if I select all the folders in "/" and click in properties, it counts all the disk space occupied by the root folder (taking into account all the devices in /media/, that is, all others hard drives). Anyway I don't think it has anything to do with the problem, cause I still get the same when doing df -h

Swap must be working correctly

```
**free**

             total       used       free     shared    buffers     cached
Mem:       2075912     471560    1604352          0      62256     249320
-/+ buffers/cache:     159984    1915928
Swap:      2931820          0    2931820

But that's all I have to say it's working...
```


Thanks again!!

---

### Post by Manuito on 2006-12-22
I just discovered I can learn the free disk space available in the root folder by typing:

**df -h /**

Take a look at the name of the filesystem, I don't understand it.

```
manu@cuac:~$ df -h /
S.ficheros            Tamaño Usado  Disp Uso% Montado en
-                      30G  2,8G   26G  10% /
```

---

