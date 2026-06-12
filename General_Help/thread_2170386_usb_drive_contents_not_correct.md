---
title: "usb drive contents not correct"
date: 2013-08-26
forum: General Help
---

### Post by emerson1979 on 2013-08-26
Hello Everyone
                          I properly mounted a usb drive, but when I did the list commnad it only listed a lost&found  directory.  I know there are many other files present as I was in Windows and copied the files to the usb stick


Thank You

---

### Post by hg-knight on 2013-08-26
does the usb drive not show up in the file listing when you open the file folder.(home folder)
what distro you using ?

---

### Post by emerson1979 on 2013-08-26
no it doesn't show up. I'm runnibg ubuntu  12.04

---

### Post by Bashing-om on 2013-08-26
emerson1979; Hi !
With the usb drive plugged in, post the output of terminal commands (ctl+alt+t yields a terminal):
```

sudo blkid
sudo fdisk -lu

```shows the UUID assignments and the partitioning scheme.

[INDENT][INDENT]good place to start
[/INDENT][/INDENT]

---

### Post by emerson1979 on 2013-08-26
root@dan-MS-7369:~# blkid
/dev/sda3: UUID="97932ae7-97f5-478b-8f40-dd5e5967fdab" TYPE="ext4" 
/dev/sdb1: UUID="e2f08e61-9942-4b75-bd9f-9352c3510583" TYPE="ext4" 
/dev/sdb5: UUID="06bfc3f8-796d-4659-bd02-64a398fb7cfc" TYPE="swap" 
/dev/sdb6: UUID="25ca7960-4ca2-40b3-b5db-ea4a53980e19" TYPE="ext4" 
/dev/sdb7: UUID="0d64ec8d-327d-40cc-a573-71567d427ac4" TYPE="ext4" 
/dev/sdc1: UUID="5821c10e-32ff-49eb-a152-998115345784" TYPE="ext4" 
/dev/sdd1: LABEL="data" UUID="8fd68c34-251f-4b6d-bf6a-a0d8fe6a07bf" TYPE="ext4

dan@dan-MS-7369:~$ sudo -i
[sudo] password for dan: 
root@dan-MS-7369:~# blkid
/dev/sda3: UUID="97932ae7-97f5-478b-8f40-dd5e5967fdab" TYPE="ext4" 
/dev/sdb1: UUID="e2f08e61-9942-4b75-bd9f-9352c3510583" TYPE="ext4" 
/dev/sdb5: UUID="06bfc3f8-796d-4659-bd02-64a398fb7cfc" TYPE="swap" 
/dev/sdb6: UUID="25ca7960-4ca2-40b3-b5db-ea4a53980e19" TYPE="ext4" 
/dev/sdb7: UUID="0d64ec8d-327d-40cc-a573-71567d427ac4" TYPE="ext4" 
/dev/sdc1: UUID="5821c10e-32ff-49eb-a152-998115345784" TYPE="ext4" 
/dev/sdd1: LABEL="data" UUID="8fd68c34-251f-4b6d-bf6a-a0d8fe6a07bf" TYPE="ext4" 
root@dan-MS-7369:~# fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b7f7dab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3   *    69634048   488396799   209381376   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084bf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     9764863     4881408   83  Linux
/dev/sdb2         9766910   625141759   307687425    5  Extended
/dev/sdb5        97658880   107421695     4881408   82  Linux swap / Solaris
/dev/sdb6       107423744   625141759   258859008   83  Linux
/dev/sdb7         9766912    97656831    43944960   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe76f7e87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976773119   488385536   83  Linux

Disk /dev/sdd: 1031 MB, 1031798784 bytes
113 heads, 51 sectors/track, 349 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x004b0d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     2015231     1006592   83  Linux
root@dan-MS-7369:~# 


 sdd1 is my usb drive

---

### Post by Bashing-om on 2013-08-26
emerson1979; Hey !

this:
> 
present as I was in Windows and copied the files to the usb stick

and:
> 
/dev/sdd1: LABEL="data" UUID="8fd68c34-251f-4b6d-bf6a-a0d8fe6a07bf" TYPE="ext4
/dev/sdd1 2048 2015231 1006592 83 Linux

says you are attempting the not possible ... while ubuntu can read and write Windows. Windows can not even see a device formatted as ext4 (ubuntu).
To share files with between the 2 operating systems .. format the usb drive as "NTFS".

[INDENT][INDENT]there are solutions
[/INDENT][/INDENT]

---

