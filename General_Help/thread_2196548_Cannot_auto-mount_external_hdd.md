---
title: "Cannot auto-mount external hdd"
date: 2013-12-30
forum: General Help
---

### Post by riccardo-nagar on 2013-12-30
I have a Maxell USB hard drive, but when I plug it in, I would want it to automount but it doesn't. I checked if it's recognized by the system and it does, even if it doesn't have a UUID. I installed the usbmount package.
Some results from the terminal:

sudo lsblk

```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0    20G  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part 
&#9500;&#9472;sda3   8:3    0   179G  0 part /media/windows7
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0 259,1G  0 part /
&#9492;&#9472;sda6   8:6    0   3,8G  0 part [SWAP]
sdb      8:16   0 465,8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465,8G  0 part 
sr0     11:0    1  1024M  0 rom  

```

So it is /dev/sdb1, but...

sudo blkid

```

/dev/sda1: LABEL="RECOVERY" UUID="DA90D71190D6F2CD" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM" UUID="5836D6F236D6D05C" TYPE="ntfs" 
/dev/sda3: UUID="0614D9B914D9AC45" TYPE="ntfs" 
/dev/sda5: UUID="fd4258c0-296b-42ea-ae96-1fd3081a02a9" TYPE="ext4" 
/dev/sda6: UUID="95a2c714-132c-46d7-b80c-7e4c460f6d0b" TYPE="swap" 

```

---

### Post by sudodus on 2014-01-03
Welcome to the Ubuntu Forums :-)

Have you tried the following commands?

```
sudo fdisk -lu
sudo parted -l
```
and to mount it manually with
```
sudo mount /dev/sdb1 /mnt
```
and check with
```
df
```

---

### Post by riccardo-nagar on 2014-01-03
Thank you for answering! :D[B]

sudo fdisk -lu[/B]

(I'm sorry, some words in the results are in italian...)
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xb6581ee0


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    41945087    20971520   27  Hidden NTFS WinRE
/dev/sda2   *    41945088    42149887      102400    7  HPFS/NTFS/exFAT
/dev/sda3        42149888   417540095   187695104    7  HPFS/NTFS/exFAT
/dev/sda4       417542142   968800255   275629057    5  Esteso
/dev/sda5       417542144   960835112   271646484+  83  Linux
/dev/sda6       960835584   968800255     3982336   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xf2928f49


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976768064   488383008+   c  W95 FAT32 (LBA)

```

**sudo parted -l**

```

Modello: ATA Hitachi HTS54505 (scsi)
Disco /dev/sda: 500GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos


Numero  Inizio  Fine    Dimensione  Tipo      File system     Flag
 1      1049kB  21,5GB  21,5GB      primary   ntfs            diag
 2      21,5GB  21,6GB  105MB       primary   ntfs            avvio
 3      21,6GB  214GB   192GB       primary   ntfs
 4      214GB   496GB   282GB       extended
 5      214GB   492GB   278GB       logical   ext4
 6      492GB   496GB   4078MB      logical   linux-swap(v1)




Modello: Maxell External USB 2.0 (scsi)
Disco /dev/sdb: 500GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos


Numero  Inizio  Fine   Dimensione  Tipo     File system  Flag
 1      1049kB  500GB  500GB       primary               lba

```


I actually can mount it manually - I had already tried mounting it on /media/hdd and it also appeared as a directory in Nautilus. Now I did as you said (**sudo mount /dev/sdb1 /mnt**) and I checked it with **df**:

```

File system    1K-blocchi     Usati Disponib. Uso% Montato su
/dev/sda5       267252244 132010056 121643484  53% /
none                    4         0         4   0% /sys/fs/cgroup
udev              1911184         4   1911180   1% /dev
tmpfs              384260      1152    383108   1% /run
none                 5120         0      5120   0% /run/lock
none              1921292       908   1920384   1% /run/shm
none               102400        36    102364   1% /run/user
/dev/sda3       187695100 136524924  51170176  73% /media/windows7
/dev/sdb1       488263616        32 488263584   1% /mnt

```

but this time it didn't appear as an external disk on the file manager.

---

### Post by deadflowr on 2014-01-03
> **riccardo-nagar said:**
> 
but this time it didn't appear as an external disk on the file manager.

That's because the file manager's devices listings are usually whatever is in the /media folder(directory)
You mounted this time inside the /mnt folder.

That said, I would look at the settings in system settings > details > removable media.
I don't know that this will help, though.

---

### Post by sudodus on 2014-01-03
> **riccardo-nagar said:**
> 
I actually can mount it manually - I had already tried mounting it on /media/hdd and it also appeared as a directory in Nautilus. Now I did as you said (**sudo mount /dev/sdb1 /mnt**) and I checked it with **df**:

```

File system    1K-blocchi     Usati Disponib. Uso% Montato su
/dev/sda5       267252244 132010056 121643484  53% /
none                    4         0         4   0% /sys/fs/cgroup
udev              1911184         4   1911180   1% /dev
tmpfs              384260      1152    383108   1% /run
none                 5120         0      5120   0% /run/lock
none              1921292       908   1920384   1% /run/shm
none               102400        36    102364   1% /run/user
/dev/sda3       187695100 136524924  51170176  73% /media/windows7
/dev/sdb1       488263616        32 488263584   1% /mnt

```

but this time it didn't appear as an external disk on the file manager.

> **deadflowr said:**
> That's because the file manager's devices listings are usually whatever is in the /media folder(directory)
You mounted this time inside the /mnt folder.

That said, I would look at the settings in system settings > details > removable media.
I don't know that this will help, though.

+1

I'm glad you can mount it manually. I have no solution to your problem to automount it. It is important? Could you use some kind of work-around, for example ***aliases*** or ***desktop launcher files*** for mounting and unmounting it easily? An alternative is to have the drive listed in **[FONT=courier new]/etc/fstab[/FONT]** with the ***noauto*** option, and give it a ***nice label***, so that it can be mounted easily referring to the label (for example mx)

```
sudo mount -L mx
```

---

### Post by riccardo-nagar on 2014-01-03
Ok it's not the biggest problem, but I just wondered how it's possible that this external drive doesn't auto-mount when plugged in like any other USB drive.

> **sudodus said:**
> 
An alternative is to have the drive listed in **[FONT=courier new]/etc/fstab[/FONT]** with the ***noauto*** option, and give it a ***nice label***, so that it can be mounted easily referring to the label (for example mx)


The fact is that I can't list it in /ect/fstab because apparently it has no UUID.

---

### Post by deadflowr on 2014-01-03
I'm not sure, but doesn't the LBA signify that it's an extended partition?
Meaning it's not really a partition like a true primary or logical partition would be.
I know my own extended partitions have no UUID's.
Just a guess, though.

---

### Post by sudodus on 2014-01-03
According to ***fdisk and parted*** it is a FAT32 primary partition and it should be possible to give it a label with ***gparted***. The lba flag does not change that. I think the label can be used to identify the device in /etc/fstab. It is good practice but not necessary to use UUID in fstab, see ```
man fstab
```

*Edit*: On the other hand, probably the drive is pre-partitioned from the factory. If it is new, and you have no data in it, you can try to repartition and reformat it with gparted. Chances are that you will get a better partition and file system. Then you can also consider what file system you want. NTFS is available from Windows and linux like FAT32, and also more stable (with journaling), and can have files larger than 4 GB (the max file size in FAT32). If you will not need access from Windows, it is better to use a linux file system, and I would recommend ext4.

---

### Post by riccardo-nagar on 2014-01-04
I think that I would have to store files larger than 4 GB, so I'm gonna try to format it as a NTFS. Gparted recognizes the device, but with "unknown" file system. The drive seems already pre-partitioned, with /dev/sdb1 that is the larger partition, and a "not allocated" partition with no other particular informations except for the dimension (2.49 MB). Can I remove the two partitions and format it NTFS all, without damaging anything?

---

### Post by sudodus on 2014-01-04
Yes, I think so. But I think the smart part (2.49 MB) is small enough to be left alone, particularly if it is at the beginning of the drive (at the left end of the graphical representation in Gparted). It might contain some firmware for the external drive system (I don't think it does, but we can never know for sure, there might be a reason why it is there).

---

### Post by riccardo-nagar on 2014-01-04
Ok now that I have formatted the bigger partition as NTFS, the system recognizes the external drive and mounts it when I plug it in. I think the problem is solved :)
Thanks for the help!!

---

### Post by sudodus on 2014-01-04
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

