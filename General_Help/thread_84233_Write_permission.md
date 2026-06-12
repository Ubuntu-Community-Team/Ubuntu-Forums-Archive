---
title: "Write permission"
date: 2005-10-30
forum: General Help
---

### Post by Acerbic on 2005-10-30
How do I make my external hard drive writable? :confused:

---

### Post by Donnut on 2005-10-30
Is it ntfs?  You can't write to an ntfs HD.

---

### Post by Doc.Caliban on 2005-10-30
[QUOTE=Acerbic]How do I make my external hard drive writable? :confused:[/QUOTE]


It should be writeable unless it's NTFS.  If it is NTFS, you don't want to write to it because although there is a way that you can, it is very likely that you will damage the data structure and render the drive unuseable in Windows again.

-Doc

---

### Post by Cesium on 2006-01-15
[QUOTE=Doc.Caliban]It should be writeable unless it's NTFS.  If it is NTFS, you don't want to write to it because although there is a way that you can, it is very likely that you will damage the data structure and render the drive unuseable in Windows again.

-Doc[/QUOTE]

How do I tell if my external hard drive is NTFS or FAT in Ubuntu? :confused:  Thanks much!

---

### Post by aysiu on 2006-01-15
[QUOTE=Cesium]How do I tell if my external hard drive is NTFS or FAT in Ubuntu? :confused:  Thanks much![/QUOTE] Plug it in. Then go to Applications > Accessories > Terminal and type ```
sudo fdisk -l
``` Then, post the output of that command in this thread.

---

### Post by Cesium on 2006-01-15
Thanks Aysiu!  Here is my output (I dual boot with Windows XP, if that helps):
[COLOR="Blue"]
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12523   100590966    7  HPFS/NTFS
/dev/sda2           12524       14500    15880252+  83  Linux
/dev/sda3           14501       14589      714892+   5  Extended
/dev/sda5           14501       14589      714861   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS[/COLOR]

---

### Post by aysiu on 2006-01-15
[QUOTE=Cesium]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS[/QUOTE] This is your external hard drive, and it appears to be NTFS.

---

### Post by Cesium on 2006-01-15
Thanks much!  I suppose this means I can only read from the disk and not write to the disk.  Is there anyway that I can transfer files from the external hard drive to Ubuntu without having to change each file's permissions to "write?"  Each time I transfer a file to Ubuntu, the file will allow me to read but not write.  I have to manually change each file's permissions to write to move or change the file.

Thanks again.  :D

---

### Post by aysiu on 2006-01-15
[QUOTE=Cesium]Thanks much!  I suppose this means I can only read from the disk and not write to the disk.  Is there anyway that I can transfer files from the external hard drive to Ubuntu without having to change each file's permissions to "write?"  Each time I transfer a file to Ubuntu, the file will allow me to read but not write.  I have to manually change each file's permissions to write to move or change the file.[/QUOTE] Copy the files to a folder on your desktop called **backup**. Then, open up a terminal and type these commands: ```
sudo chmod -R 777 ~/Desktop/backup
```

---

### Post by RAOF on 2006-01-15
[QUOTE=aysiu]Copy the files to a folder on your desktop called **backup**. Then, open up a terminal and type these commands: ```
sudo chmod -R 777 ~/Desktop/backup
```[/QUOTE]
This will mark everything in backup with "read, write, execute" permissions for everyone.  If you only want to make them writeable, try
```
sudo chmod -R a+w ~/Desktop/backup
```

---

### Post by Cesium on 2006-01-15
Thanks for the replies.  I will probably end up using both sets of commands at one point or another.

---

