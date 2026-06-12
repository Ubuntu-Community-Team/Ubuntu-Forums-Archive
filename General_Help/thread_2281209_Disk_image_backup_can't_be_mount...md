---
title: "Disk image backup can't be mount.."
date: 2015-06-05
forum: General Help
---

### Post by Aegedus on 2015-06-05
Hi,

Long time ago I created an image from a Sony Vaio laptop installed with windows8.
I'm trying to mount this image.

This is the command line I used to create the image :  

sudo dd if=/dev/sda bs=4k conv=notrunc | gzip > 20130226-vaio.image.gz
125026902+0 records in
125026902+0 records out
512110190592 bytes (512 GB) copied, 22039.5 s, 23.2 MB/s

So, I unzipped the image :
gunzip -c 20130226-vaio.image.gz > 20130226-vaio.image

When I try to mount it, the partition is not recognize :
```
sudo mount -t ntfs-3g -o loop ./20130226-vaio.image /mnt/Tmp1
NTFS signature is missing.
Failed to mount '/dev/loop0': Argument invalide
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

Ok, I tried to evaluate some information ... like where the partition start. And I get the information there a GPT partition table !!
```
sudo fdisk -lu 20130226-vaio.image

Attention : identifiant de table de partitions GPT (GUID) détecté sur « 20130226-vaio.image » ! L'utilitaire fdisk ne prend pas GPT en charge. Utilisez GNU Parted.


Disk 20130226-vaio.image: 89.1 GB, 89055731712 bytes
256 têtes, 63 secteurs/piste, 10784 cylindres, total 173936976 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x929594a5

      Périphérique Amorçage  Début         Fin      Blocs    Id. Système
20130226-vaio.image1               1  4294967295  2147483647+  ee  GPT


``` 


Well, using GParted gives :
```
sudo gparted 20130226-vaio.image
======================
libparted : 2.3
======================
fin de fichier atteinte en lisant Aucun fichier ou dossier de ce type

```

If I translate : "end of file accessed reading. No type of file or directory found."

mmhmm .... let's go with gdisk and "v" option !

```
Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 173936976 sectors, needs to be 1000215216 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Identified 5 problems!


```


Of course, the image file size  is 90Go ... and the original disk is 500Go. I think this is one of the main problem, don't you think ?
how to deal with this ???

Thanks in advance for your help.
Ag

---

