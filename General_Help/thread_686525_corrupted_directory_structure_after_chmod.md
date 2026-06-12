---
title: "corrupted directory structure after chmod"
date: 2008-02-03
forum: General Help
---

### Post by jurjen on 2008-02-03
hi guys,

did something (really) stupid, and now i ended up with 2 useless hd's with a lot of important data on it...

first of all, i configured my computer like this:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14679   117909036   83  Linux
/dev/sda2   *       14680       29644   120206362+   7  HPFS/NTFS
/dev/sda3           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8a1b8a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

```
where sda contains the os (ubuntu on sda1, winxp on sda2), either sdb1 or sdc1 is a xfs fs, the other an ext3 (changes every boot, the disks are mounted by ther uuid).

assume sdb1 is the ext3 mounted on /data, sdc1 the xfs, mounted on /multimedia
i tried to reset all the user permissions on the /data disk with the following command:

```
chmod -R 644 /data
```

and here it went wrong... first got a permissions denied error, after doing ls /data -l, i saw:
```

total 0
?--------- ? ? ? ?                ? /data/docs
?--------- ? ? ? ?                ? /data/downloads
?--------- ? ? ? ?                ? /data/dump
etc...

```
(note that the directory's are listed as /data/docs instead of /data, everything is a directory btw)

first i tried fsck:
```

jurjen@giorgio:/mnt$ sudo fsck -vC /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 4987/30539776 files, 42962052/61049000 blocks

jurjen@giorgio:/mnt$ sudo fsck -vCf /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
                                                                               
    4987 inodes used (0.02%)
     375 non-contiguous inodes (7.5%)
         # of inodes with ind/dind/tind blocks: 4311/2896/0
42962052 blocks used (70.37%)
       0 bad blocks
       2 large files

    4401 regular files
     577 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
    4978 files

```

tried testdisk, also didn't give back any errors, and in testdisk, all directory's were browsable.

it seems the 'root' directory file is corrupted. but i can't find of a way to repair/recover it... situation on the xfs disk is exactly the same.

does anyone has a hint? tx in advance!

---

### Post by jurjen on 2008-02-03
hell yeah! it's working again!

just had to do:
```

chmod +x /data

```

and the hd is working again :)

tx for your time anyway, hope this issue will be helpfull to others though

---

### Post by ellis rowell on 2008-02-03
I had a similar problem with an Ext HDD. One partition was corrupted and I couldn't find how to get it back. I eventually did so by booting with a Live CD when I found I could read it again. A second time I corrupted a folder and again booted with a Live CD and got it back. I traced the problem to accidentally having the cursor on ".." when I did a chmod in Gftp, so I am now very careful to make sure that the cursor/highlight is the file I wish to modify.

---

