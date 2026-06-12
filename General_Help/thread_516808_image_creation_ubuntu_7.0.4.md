---
title: "image creation ubuntu 7.0.4"
date: 2007-08-03
forum: General Help
---

### Post by piero1989 on 2007-08-03
I have problem with image  creation on ubuntu 7.04

I have tried with Norton ghost 2003 : unexpected packet error
G4L : freezing during the image creation
Partimage 0.64 :segmentation fault

Tested in clean system install +update 
Tested Italian language +EXT3 file system ad tested English language +EXT2 file system with the same results

Sincerely I don’t want use dd because the image it’s to big (partition of 25 GB)

Somebody can help  me ?

The system is 

Mather board gigabyte 7N400 pro2
AMD Athlon xp 3200+  
1GB ram 
Video nvidia 7600 GS 
Disk 
parallel ata Maxtor 160 GB
Serial Ata 6y120 120G
Linux in 25GB partition in serial ata disk



Thanks and regards

Piero

---

### Post by Technophobia on 2007-08-03
Maybe you hit the limit of an image size

---

### Post by piero1989 on 2007-08-04
Sorry I don’t understand your reply
To be more clear
Image source Linux ubuntu 7.04 in sda7 (partition in serial Ata disk)
Image destination in parallel Ata FAT 32 38GB (18 GB free) first partition (C:\ for windows)

Ghost 2003 create the file , but , during the verification of created image give error
G4L freeze at about 13 %
Partimage 0,64 give segmentation fault at about 13 -20 % 

regards

Piero

---

### Post by piero1989 on 2007-08-10
mayby it's a filesystem problem in ubuntu 7.04 ?

Partimage = segmentation fault
G4L =freeze

Backup with tar

sudo tar -cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /

stop with error after file crypto

somebady have try to make an image in Ubuntu 7.04 ??????

thanks and regards


Piero

---

### Post by piero1989 on 2007-08-13
with compression level = none it's work
With Gzip=default no work (segmentation fault)
With Bzip2 no work (segmentation fault)

I use partimage 0,64 from system recue cd 0,37

For the moment i work with no compression in the image files

thanks and regards

Piero

---

