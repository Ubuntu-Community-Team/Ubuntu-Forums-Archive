---
title: "trying to get permistions on externeal hdd partition"
date: 2017-02-27
forum: General Help
---

### Post by orbitmipi on 2017-02-27
hay I have a mybook with 1 tb ntfs and 2 tb of ext4 the ext4 will not  leat me right to it from desk top. I created the partitions with gparted.

I tryed this:
sudo mkdir /media/odroid/ext4_backup/backups  (did acualy let me make the folder but I cant right or make folders in side it from deasktop)
sudo chmod 766 /media/odroid/ext4_backup/backups
sudo chown $USER:$USER /media/odroid/ext4_backup/backups

and this:
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

and this:
sudo mkdir /mnt/data
sudo chmod 766 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda1 /mnt/data

Shuld I try editing in the fstab ?

Right now the hdd(mybook) is going to be a back up if I can transfer my files from my old back up externeal drive.

---

### Post by sudodus on 2017-02-27
You can use ***chmod*** with the **ext4** file system.

The permissions of Microsoft file systems (FAT32 and NTFS) are ***fixed when mounted*** (and cannot be changed by chmod).

A workaround is described at the following link,

[Mount a FAT32 partition in a USB stick with write permissions for everybody](https://askubuntu.com/questions/886701/how-do-i-get-permission-to-edit-in-my-usb/886735#886735)

And yes, you can edit fstab to do the corresponding task at boot. See ```
man mount
``` and ```
man fstab
``` for details. Ask again, if you need help with some detail.

---

### Post by orbitmipi on 2017-02-27
well I have no problem having all permistions on the ntsf. lol 
but can you exsplan more on how I can right to the ext4 ?
I am a noob >_<

---

### Post by sudodus on 2017-02-27
Please post the output of the following commands when the external drive is connected.

```
df
sudo lsblk -fm
sudo parted -ls
sudo ls -l /media/$USER
```

-o-

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by orbitmipi on 2017-02-27
```

root@odroid:/# df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev              758432       0    758432   0% /dev
tmpfs             203852   10712    193140   6% /run
/dev/mmcblk0p2  30546964 4258388  25649448  15% /
tmpfs            1019252     196   1019056   1% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
tmpfs            1019252       0   1019252   0% /sys/fs/cgroup
/dev/mmcblk0p1    130798   12490    118308  10% /media/boot
tmpfs             203852      28    203824   1% /run/user/1000

```


```

root@odroid:/# lsblk -fm
NAME        FSTYPE LABEL        UUID                                 MOUNTPOINT                 NAME         SIZE OWNER GROUP MODE
sda                                                                                             sda          2.7T root  disk  brw-rw----
&#9500;&#9472;sda1      ext4   ext4_backup  bcf59324-2c98-4d8b-877e-78549352e5de /media/odroid/ext4_backup  &#9500;&#9472;sda1       1.8T root  disk  brw-rw----
&#9492;&#9472;sda2      ntfs   ntfs back up 161659BF429F7213                     /media/odroid/ntfs back up &#9492;&#9472;sda2       939G root  disk  brw-rw----
mmcblk0                                                                                         mmcblk0     29.7G root  disk  brw-rw----
&#9500;&#9472;mmcblk0p1 vfat   boot         52AA-6867                            /media/boot                &#9500;&#9472;mmcblk0p1  128M root  disk  brw-rw----
&#9492;&#9472;mmcblk0p2 ext4   rootfs       e139ce78-9841-40fe-8823-96a304a09859 /                          &#9492;&#9472;mmcblk0p2 29.6G root  disk  brw-rw----

```

```

root@odroid:/# parted -ls
Model: WD My Book 1235 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name          Flags
 1      1049kB  1992GB  1992GB  ext4         ext4_backup
 2      1992GB  3001GB  1008GB  ntfs         ntfs back up  msftdata




Model: SD SU32G (sd/mmc)
Disk /dev/mmcblk0: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  135MB   134MB   primary  fat16        lba
 2      135MB   31.9GB  31.8GB  primary  ext2

```

```

root@odroid:/# ls -l /media/$USER
ls: cannot access '/media/root': No such file or directory

```

EDIT: LOL I did not know that "$USER:$USER" meant the operater, admin, user :) I just typed in
```

chown odroid /media/odroid/ext4_backup/backups

```
and it work'd ty

---

### Post by sudodus on 2017-02-28
If you need more help, plsase ask :-)

Otherwise, (if you feel that your problem is solved), please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

