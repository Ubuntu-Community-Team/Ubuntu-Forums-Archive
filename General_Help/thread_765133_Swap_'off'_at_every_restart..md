---
title: "Swap 'off' at every restart."
date: 2008-04-24
forum: General Help
---

### Post by jldeshpande on 2008-04-24
Hi Noble Souls!
Linux Swap is 'Off' at every reboot of my PC. 
Since Feb'08, using Ubuntu Studio 7.10 + kde.
Before @ 10 days,resized swap from 737 MB to 2 GB.
When in gnome partition editor I make  'swapon', system monitor shows 2 GB. It remains so though i switch between Ubuntu & Kubuntu or restart x server, but not after restarting the PC.
Reformated it and made 'On' with gparted live cd v 0.3.4-0 from which i had resized it before @ 10 days,but in vain.
What more details should I submit?
:(

---

### Post by chrisccoulson on 2008-04-24
Can you post the output of:
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by jldeshpande on 2008-04-24
> **chrisccoulson said:**
> Can you post the output of:
```
cat /etc/fstab
sudo fdisk -l
```

Here it is pl.

j@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=710ab0af-d1a1-4d67-8bce-ca593aad369e / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb8
UUID=37336730-75be-43b5-a27d-c378da0f3887 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda5       /media/sda5 vfat iocharset=utf8,umask=000 0 0
/dev/sda6       /media/sda6 vfat iocharset=utf8,umask=000 0 0
/dev/sda7       /media/IMPDoc ntfs  defaults,umask=007,gid=46 0     1

j@ubuntu:~$ sudo fdisk -l
[sudo] password for j:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d081d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920    31487368+   7  HPFS/NTFS
/dev/sda2            3921       19457   124800952+   f  W95 Ext'd (LBA)
/dev/sda5            3921        7975    32571756    b  W95 FAT32
/dev/sda6            7976       12156    33583851    b  W95 FAT32
/dev/sda7           12157       16465    34612011    7  HPFS/NTFS
/dev/sda8           16466       19457    24033208+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3f3f3f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       17448       19457    16145325   83  Linux
/dev/sdb2               2       17447   140134995    f  W95 Ext'd (LBA)
/dev/sdb5            6542       11105    36660298+   7  HPFS/NTFS
/dev/sdb6               2        6541    52532487    7  HPFS/NTFS
/dev/sdb7           11106       17181    48805438+   7  HPFS/NTFS
/dev/sdb8           17182       17447     2136613+  82  Linux swap / Solaris

Partition table entries are not in disk order
j@ubuntu:~$

---

### Post by chrisccoulson on 2008-04-24
Could you also post the output of:
```
sudo blkid /dev/sdb8
```

---

### Post by b5baxter on 2008-04-24
I ran into the swap being turned off because fstab had the wrong UUID. Fixed based on instructions here: [http://ubuntuforums.org/showthread.php?p=3704872](http://ubuntuforums.org/showthread.php?p=3704872)

---

### Post by chrisccoulson on 2008-04-24
I suspect that is what is happening here as well, especially as the UUID will have changed after resizing the swap partition. I think the output of blkid will confirm it.

---

### Post by jldeshpande on 2008-04-25
> **chrisccoulson said:**
> Could you also post the output of:
```
sudo blkid /dev/sdb8
```

Sorry for delay,my [so called] broad band connection was not able  to post such a tinny reply.

j@ubuntu:~$ sudo blkid /dev/sdb8
[sudo] password for j:
/dev/sdb8: TYPE="swap" UUID="41a76ea5-64ee-4471-a29e-9672991dc439" 
j@ubuntu:~$ 

Thx

---

### Post by dcstar on 2008-04-25
> **jldeshpande said:**
> Sorry for delay,my [so called] broad band connection was not able  to post such a tinny reply.

j@ubuntu:~$ sudo blkid /dev/sdb8
[sudo] password for j:
/dev/sdb8: TYPE="swap" UUID="41a76ea5-64ee-4471-a29e-9672991dc439" 
j@ubuntu:~$ 

Thx

Change the relevant value - in a terminal - with this:

```
gksudo gedit /etc/fstab
```

---

### Post by jldeshpande on 2008-04-25
> **dcstar said:**
> Change the relevant value - in a terminal - with this:

```
gksudo gedit /etc/fstab
```

Thanks!
It seems it worked.
Just now restarted PC & system monitor is showing 2 GB swap available.
Thanks once again to all.

---

