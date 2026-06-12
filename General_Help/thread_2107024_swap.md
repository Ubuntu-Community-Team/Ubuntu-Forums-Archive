---
title: "swap"
date: 2013-01-20
forum: General Help
---

### Post by linuxyogi on 2013-01-20
Hi,

I while trying to install another distro on my hdd deleted & recreated the swap partition.

The installation of that distro didn't succeed coz its installer was buggy , so I rebooted & surprisingly Xubuntu booted fine despite the modification made to the partition table.

But I am not sure if Xubuntu is using swap anymore.

How to find out if Xubuntu is still utilizing swap ? If not how to restore swap ?

---

### Post by Bashing-om on 2013-01-20
linuxyogi; Hi to you too !

To see all partitions inclusive of swap one may run the terminal command:
```
sudo fdisk -l
```and to see memory usage:
```
free
```[INDENT][INDENT]just try'n to help 

[/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-01-21
To force swap on a drive/parition /dev/sdb5

```
sudo mkswap /dev/sdb5
sudo swapon /dev/sdb5
```

The first command is not needed if you already have a swap partition created and verified by the *fdisk -l* command in the previous post.

The second command is only needed if your swap is not showing up automatically using the *free* command.

Swap is helpful if you are short on RAM when installing, although it can slow the installation down to a crawl and you must be patient otherwise you will be reinstalling several times and not know what is going on.

---

### Post by linuxyogi on 2013-01-21
```
$ sudo fdisk -l
[sudo] password for tux: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   122882047    61337600    7  HPFS/NTFS/exFAT
/dev/sda3       122882048   130695167     3906560   82  Linux swap / Solaris
/dev/sda4       130695168   312578047    90941440   83  Linux
```


```
$ free
             total       used       free     shared    buffers     cached
Mem:       2050992     932360    1118632          0      52892     400876
-/+ buffers/cache:     478592    1572400
Swap:            0          0          0
```

```
$ sudo swapon /dev/sda3
swapon: /dev/sda3: read swap header failed: Invalid argument
```

---

### Post by SeijiSensei on 2013-01-21
Run "sudo mkswap /dev/sda3" and try again.

---

### Post by linuxyogi on 2013-01-21
Found the solution at [http://www.iloveubuntu.net/how-repair-swap-partition-ubuntu](http://www.iloveubuntu.net/how-repair-swap-partition-ubuntu)

---

### Post by tgalati4 on 2013-01-21
Sometimes swap partitions get messed up when mixing live distros 32-bit, 64-bit, and USB live boot.  All of these boot methods can use swap and sometime leave the swap partition in a state that can't be read by another distro.  It's rare, but it does happen.

---

