---
title: "usb hd disks not seen by Lubuntu, no sdb results"
date: 2015-01-31
forum: General Help
---

### Post by pagnes on 2015-01-31
hello, I have Lubuntu on an AMD Athlon 64 with 500 MB memory (is rather slow), with an USB hub. Problem: if I attach one of my external USB hard disks (they work well with other ubuntu pc-s) they are not recognized. Usb port is OK as if I attach to the same port a dvd reader, it is seen (and results in Disks). 
I have tried various advices on forums, including this, but they presume sdb results in list. 
If I give lsblk, no such device resuls: 

```
pc@pc-desktop:~$ lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                             8:0    0 152,7G  0 disk 
&#9500;&#9472;sda1                          8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                          8:2    0     1K  0 part 
&#9492;&#9472;sda5                          8:5    0 152,4G  0 part 
  &#9500;&#9472;lubuntu--vg-root (dm-0)   252:0    0   152G  0 lvm  /
  &#9492;&#9472;lubuntu--vg-swap_1 (dm-1) 252:1    0   512M  0 lvm  [SWAP]
sr0                            11:0    1  1024M  0 rom  
sr1                            11:1    1  1024M  0 rom  
zram0                         251:0    0 244,6M  0 disk [SWAP]
```


thank you in advance

---

### Post by ajgreeny on 2015-01-31
What does command **sudo fdisk -l** show you?

---

### Post by pagnes on 2015-01-31
```
pc@pc-desktop:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025e2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758   320172031   159835137    5  Extended
/dev/sda5          501760   320172031   159835136   8e  Linux LVM

Disk /dev/mapper/lubuntu--vg-root: 163.1 GB, 163133259776 bytes
255 heads, 63 sectors/track, 19833 cylinders, total 318619648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/lubuntu--vg-swap_1: 536 MB, 536870912 bytes
255 heads, 63 sectors/track, 65 cylinders, total 1048576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lubuntu--vg-swap_1 doesn't contain a valid partition table
pc@pc-desktop:~$ 


```

---

### Post by ajgreeny on 2015-02-01
Is that USB disk encrypted or also using lvm?

---

### Post by pagnes on 2015-02-01
> **ajgreeny said:**
> Is that USB disk encrypted or also using lvm?

the disks are not encrypted, one is WD 3200BMV 320GB. the other is WDC 180GB (recycled from my previous laptop). Both are recognized by the laptop acer aspire one with Ubuntu 14.04

I do not know about lvm

---

### Post by ajgreeny on 2015-02-01
Using the Acer Aspire One with Ubuntu 14.04 that does detect the USB disk run ```
sudo fdisk -l
``` again and report the output here.

That output in your problem machine ```
Disk /dev/mapper/lubuntu--vg-root: 163.1 GB, 163133259776 bytes
```is unusual and I am not sure why you're seeing that, so I want to see what happens on another machine.

---

### Post by pagnes on 2015-02-02
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes255 testine, 63 settori/tracce, 19457 cilindri, totale 312581808 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x97dfb8fa


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20980889    10490413+   2  XENIX root
/dev/sda2   *    20981760   194888006    86953123+   7  HPFS/NTFS/exFAT
/dev/sda3       194889726   312580095    58845185    5  Esteso
/dev/sda5       194889728   310505471    57807872   83  Linux
/dev/sda6       310507520   312580095     1036288   82  Linux swap / Solaris


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 testine, 63 settori/tracce, 19457 cilindri, totale 312581808 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x42224222


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   312576704   156280320    f  W95 Esteso (LBA)
/dev/sdb5           16128   312576704   156280288+   7  HPFS/NTFS/exFAT
norbi@norbi-Aspire-one:~$ 



```

---

### Post by ajgreeny on 2015-02-02
Not much help, I am afraid.
Was the disk in a raid array in the past as that is what usually shows the /dev/mapper name?

---

### Post by pagnes on 2015-02-03
no, I do not think so, as this one has been a laptop disk and after as simply a backup unit.  I do not know if there is any connection, but the PC has two dead CD-DVD units (I use an external one and it works anyway).

---

