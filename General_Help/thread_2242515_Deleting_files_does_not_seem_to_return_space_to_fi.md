---
title: "Deleting files does not seem to return space to filesystem? (btrfs)"
date: 2014-09-02
forum: General Help
---

### Post by victorhooi on 2014-09-02
Hi,

This is going to sound strange, but I have a Ubuntu 14.04 box that doesn't seem to be releasing back the space when I delete files? Previously, I noticed that df and du were not agreeing - df was showing more space as being used than du.

```

$ sudo du -chs *
[sudo] password for victorhooi:
9.7M    bin
174M    boot
4.0K    dev
8.3M    etc
5.4G    home
4.0K    initrd.img
4.0K    initrd.img.old
1.2G    lib
4.0K    lib64
0       media
0       mnt
0       opt
du: cannot access ‘proc/7378/task/7378/fd/4’: No such file or directory
du: cannot access ‘proc/7378/task/7378/fdinfo/4’: No such file or directory
du: cannot access ‘proc/7378/fd/4’: No such file or directory
du: cannot access ‘proc/7378/fdinfo/4’: No such file or directory
0       proc
8.0K    root
1.4M    run
13M     sbin
32G     srv
0       sys
4.0K    system.properties
48K     tmp
1.5G    usr
27G     var
4.0K    vmlinuz
4.0K    vmlinuz.old
67G     total

```
```
$ df -h
Filesystem         Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p1  135G  122G   13G  91% /
none               4.0K     0  4.0K   0% /sys/fs/cgroup
udev               990M  4.0K  990M   1% /dev
tmpfs              200M  1.4M  199M   1% /run
none               5.0M     0  5.0M   0% /run/lock
none              1000M     0 1000M   0% /run/shm
none               100M     0  100M   0% /run/user
/dev/cciss/c0d0p1  135G  122G   13G  91% /home

```

And just now, I deleted a large .ISO file, and noticed that df didn't seem to show the space as being returned. lsof doesn't seem to show it as still being held.

I have also restarted the system, no change after a reboot either.

From what I can tell, the file system for / is btrfs.

This is the contents of my fstab:
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/cciss/c0d0p1 during installation
UUID=d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 /               btrfs   relatime,subvol=@ 0       1
# /home was on /dev/cciss/c0d0p1 during installation
UUID=d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 /home           btrfs   relatime,subvol=@home 0       2
# swap was on /dev/cciss/c0d0p5 during installation
UUID=119e00c3-6b4f-49aa-b5b0-4736d5398c28 none            swap    sw              0       0

```

This is the output from btrfs-show-super:
```
superblock: bytenr=65536, device=/dev/cciss/c0d0p1
---------------------------------------------------------
csum                    0x6906ce52 [match]
bytenr                  65536
flags                   0x1
magic                   _BHRfS_M [match]
fsid                    d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7
label
generation              435680
root                    409231360
sys_array_size          226
chunk_root_generation   435654
root_level              1
chunk_root              20975616
chunk_root_level        1
log_root                359743488
log_root_transid        0
log_root_level          0
total_bytes             144598630400
bytes_used              129997639680
sectorsize              4096
nodesize                4096
leafsize                4096
stripesize              4096
root_dir                6
num_devices             1
compat_flags            0x0
compat_ro_flags         0x0
incompat_flags          0x1
csum_type               0
csum_size               4
cache_generation        435680
uuid_tree_generation    242426
dev_item.uuid           d69676ea-b7c1-487a-a33c-5842ff26aa56
dev_item.fsid           d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 [match]
dev_item.type           0
dev_item.total_bytes    144598630400
dev_item.bytes_used     143919153152
dev_item.io_align       4096
dev_item.io_width       4096
dev_item.sector_size    4096
dev_item.devid          1
dev_item.dev_group      0
dev_item.seek_speed     0
dev_item.bandwidth      0
dev_item.generation     0

```

From my dmesg:
```

[   33.582866] Btrfs loaded
[   33.817432] btrfs: device fsid d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 devid 1 transid 434323 /dev/cciss/c0d0p1
[   33.927451] btrfs: device fsid d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 devid 1 transid 434323 /dev/disk/by-uuid/d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7
[   33.997228] btrfs: disk space caching is enabled
[   34.775178] random: nonblocking pool is initialized
[   60.641127] Adding 2094076k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:2094076k FS
[   60.800852] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.800862] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   60.882565] btrfs: disk space caching is enabled
[   60.940821] systemd-udevd[363]: starting version 204
[   61.037079] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   61.058117] btrfs: device fsid d1fac2b3-63dc-4b60-a8d2-1ac7a38187f7 devid 1 transid 434323 /dev/cciss/c0d0p1

```

I don't recognise what /dev/cciss/c0d0p1 is, but from Googling, it seems to be something to do with HP SmartArray RAID controllers - the machine is a HP DL360 G5.

I'm guessing I've probably missed something obvious - any thoughts?

Cheers,
Victor

---

### Post by dragonfly41 on 2014-09-02
Is the rubbish bin cleared?

---

### Post by ssam on 2014-09-05
Free space in BTRFS is quite different from older filesystems, so 'df' can't give a good answer.

```

btrfs fi df /home

```
will give a better answer.

see [https://btrfs.wiki.kernel.org/index.php/FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F](https://btrfs.wiki.kernel.org/index.php/FAQ#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F) for details

---

