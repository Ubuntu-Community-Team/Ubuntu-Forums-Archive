---
title: "Recover deleted files from NAS"
date: 2016-05-15
forum: General Help
---

### Post by leoh on 2016-05-15
Hi everyone.
Somebody deleted some files from a WD My Book Live NAS and I need to recover them.
That NAS doesn't have a recycle bin.
I read somewhere that it uses ext4 in an internal drive (I am not 100% sure though).
So I removed the SATA drive and connected it to an Ubuntu computer.
However, I have no clue how to recover the files. I already read this:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I also tried extundelete with no luck.

I was not able to understand the partitions, what I am getting doesn't make much sense and I am confused:

```
root@molecula-P4M89-M7B:/home/molecula# fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 38,4 GiB, 41174138880 bytes, 80418240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xffd60e6d

Disposit.  Inicio    Start    Final Sectores  Size Id Tipo
/dev/sda1  *          2048 76359679 76357632 36,4G 83 Linux
/dev/sda2         76361726 80416767  4055042    2G  5 Extendida
/dev/sda5         76361728 80416767  4055040    2G 82 Linux swap / Solaris


Disk /dev/sdb: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0E818285-890D-C245-AAD2-FED0E388CBC7

Disposit.    Start      Final   Sectores  Size Tipo
/dev/sdb1    30832      30847         16    8K Linux swap
/dev/sdb2  9031680 3907028991 3897997312  1,8T Microsoft basic data
```

Look at gparted:
[ATTACH=CONFIG]269104[/ATTACH]

What is going on...?

---

### Post by leoh on 2016-05-16
Anyone...?

---

### Post by leoh on 2016-05-17
Any suggestion? Please? :confused:

---

### Post by steeldriver on 2016-05-17
Sometimes fdisk is misleading - try

```

sudo parted /dev/sdb print

sudo file -sL /dev/sdb2

```

---

### Post by leoh on 2016-05-18
For some reason, sometimes the NAS drive shows as /dev/sda and sometimes (after rebooting) it shows as /dev/sdb.
On this ocasion it is /dev/sda
Anyway, here's the output:

```
root@molecula-P4M89-M7B:/home/molecula# parted /dev/sda print
Modelo: ATA WDC WD20EFRX-68A (scsi)
Disco /dev/sda: 2000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones: gpt
Disk Flags: 

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre  Banderas
 1      15,8MB  15,8MB  8192B
 2      4624MB  2000GB  1996GB  ext4                         msftdata

```

And:

```
root@molecula-P4M89-M7B:/home/molecula# file -sL /dev/sda2
/dev/sda2: Linux rev 1.0 ext4 filesystem data, UUID=d461a5d6-6d48-46b6-aa32-83b3203d3827 (extents) (large files) (huge files)
```

What does this mean?

---

### Post by steeldriver on 2016-05-18
Have you tried mounting (what looks likely to be) the data partition? e.g.

```

sudo mkdir -p /mnt/nas

sudo mount -t ext4 -o ro /dev/sda2 /mnt/nas

ls /mnt/nas

```

---

### Post by leoh on 2016-05-19
No success :(

```
root@molecula-P4M89-M7B:/home/molecula# mount -t ext4 -o ro /dev/sda2 /mnt/nas
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

So:

```
root@molecula-P4M89-M7B:/home/molecula# dmesg | tail 
[   19.675000] audit: type=1400 audit(1463697887.966:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=561 comm="apparmor_parser"
[   20.062763] audit: type=1400 audit(1463697888.358:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app" pid=562 comm="apparmor_parser"
[   20.062792] audit: type=1400 audit(1463697888.358:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="webbrowser-app//oxide_helper" pid=562 comm="apparmor_parser"
[   20.226673] audit: type=1400 audit(1463697888.518:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=563 comm="apparmor_parser"
[   35.594627] IPv6: ADDRCONF(NETDEV_UP): enp0s18: link is not ready
[   35.595106] IPv6: ADDRCONF(NETDEV_UP): enp0s18: link is not ready
[  388.382681] perf interrupt took too long (2538 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  428.889042] perf interrupt took too long (5044 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 2477.710765] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s18: link becomes ready
[ 2599.939469] EXT4-fs (sda2): bad block size 65536

```

No idea what to do :(
I have no clue what the block size should be.

---

### Post by steeldriver on 2016-05-19
Ah - I thought that might happen

IIRC the 65536 block size is a thing used by ext4 on certain Sparc-based systems. I *think *it's still the case that it's not supported by the Linux ext2/3/4 kernel driver - but it should be by the FUSE (File System in User Space) ext2 module

```

sudo apt-get install fuseext2

```

Then replace the mount command with

```

fuseext2 -o ro -o sync_read /dev/sda2 /mnt/nas

```

See [http://unix.stackexchange.com/questions/73536/how-can-i-mount-filesystems-with-4kb-block-sizes](http://unix.stackexchange.com/questions/73536/how-can-i-mount-filesystems-with-4kb-block-sizes) or search out my previous threads on this forum

---

### Post by leoh on 2016-05-20
Great! Now I was able to mount it and see the content of the partition!
However, I still need to "undelete" the deleted files. Any clue on how to do that?

---

### Post by steeldriver on 2016-05-20
I don't have experience with extundelete, but I believe it has a -B blocksize parameter, so I'd suggest you go back to your original idea of using that but this time add 
```

-B 65536

```
to the command. You may need to unmount the partition first - I'm not sure.

---

### Post by leoh on 2016-06-14
Forgot to answer, thank you! Worked perfectly!!!!

---

