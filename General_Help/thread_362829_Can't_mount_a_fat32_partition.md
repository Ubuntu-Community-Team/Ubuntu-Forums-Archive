---
title: "Can't mount a fat32 partition"
date: 2007-02-16
forum: General Help
---

### Post by doddy on 2007-02-16
When i tryed to mount a newly created fat32 partition, a dialog box appeared telling me that "Can not mount". How do i fix this?

---

### Post by yabbadabbadont on 2007-02-16
How did you create it? What are the contents of your /etc/fstab file?  What is the output of running, "sudo fdisk -l", in a terminal window?  Details man, give us details.  :D

---

### Post by Znupi on 2007-02-16
How are you trying to mount it? Just by clicking "Computer" on the "Places" menu and then double clicking the FAT32 partition? It didn't work this way for me, neither. But here's how I did it:
First, go to /dev/ and find out what your partition is called (in my case, this was hda6 but it can be any hdaX). Then, create a new folder somewhere, in my case:
```
~$ mkdir Share/
```
Then, use the mount command to mount the volume to the newly created folder, in my case it was like this (you have to sudo this):
```
$ sudo mount /dev/hda6 /home/felix/Share
```
It may take a while depending on the contents of the partition but it should work, it did for me :)

---

### Post by doddy on 2007-02-16
Znupi, i tried what you said and it came up with errors.

---

### Post by Maestro23 on 2007-02-16
> **doddy said:**
> Znupi, i tried what you said and it came up with errors.

> sudo fdisk -l

and 

cat /etc/fstab


So we can begin to help you.

---

### Post by doddy on 2007-02-23
fdisk -l
[INDENT]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7179    57665286    7  HPFS/NTFS
/dev/hda2            9093        9729     5116702+  83  Linux
/dev/hda3            8710        9092     3076447+  82  Linux swap / Solaris
/dev/hda4            7180        8709    12289725    b  W95 FAT32

Partition table entries are not in disk order[/INDENT]

---

### Post by doddy on 2007-02-23
fdisk -l
[INDENT]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7179    57665286    7  HPFS/NTFS
/dev/hda2            9093        9729     5116702+  83  Linux
/dev/hda3            8710        9092     3076447+  82  Linux swap / Solaris
/dev/hda4            7180        8709    12289725    b  W95 FAT32

Partition table entries are not in disk order[/INDENT]

---

### Post by yabbadabbadont on 2007-02-23
..... and the /etc/fstab too.  :)

---

### Post by doddy on 2007-02-25
Cat /etc/fstab
[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/INDENT]

---

### Post by yabbadabbadont on 2007-02-25
```
sudo mkdir -p /media/hda4
sudo gedit /etc/fstab
```
Add a line to /etc/fstab that looks like this:```

/dev/hda4  /media/hda4  vfat  defaults,utf8,umask=007,gid=46 0  1
```
Save your change and quit gedit.
Logout and reboot.

---

### Post by knocturnal on 2007-02-25
I am a new ubuntu user. i have a similar problem just like doddy. then i followed Znupi's reply about creating a new directory. it was successful. but however, i still cant copy my files to that parition (directory created).

can anyone help me with this problem please?

---

### Post by doddy on 2007-02-26
It worked, thanks a million

---

### Post by Znupi on 2007-04-23
> **knocturnal said:**
> I am a new ubuntu user. i have a similar problem just like doddy. then i followed Znupi's reply about creating a new directory. it was successful. but however, i still cant copy my files to that parition (directory created).

can anyone help me with this problem please?
You don't have permissions. This happens to me, too, and I don't know how to fix it. First I tried this:
```

$ sudo chmod -R 0777 ~/share/*

```
But it didn't work. The only workarounds are to use the command line to copy files to the partitions using sudo or
```

$ sudo nautilus

```
Which will start the file browser using the root user, and will be able to copy files to that drive. I'm not a Linux expert so there probably are more manageable workarounds.

---

