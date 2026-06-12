---
title: "BCache setup fails with - Device or resource busy"
date: 2015-11-01
forum: General Help
---

### Post by Horatio on 2015-11-01
I installed the needed tools that are included in the repositories and a third party repository is not needed for Ubuntu 14.04.

$ sudo apt-get install bcache-tools

It's necessary to create the file system during the setup of the bcache. A existing file system cannot be converted with the standard utilities. A parition on the SSD and on the HDD will need to be created. My SSD is /dev/sda and a partion /dev/sda8, about 30 GB, is created to be used as the cache. I'll be using it to cache a 150 GB HDD, and I created the partition /dev/sdd1 for the actual storage. The following command will pair the two so that there will exist the needed block device, /dev/bcache0, for mounting the partion which gave me the message that explained exactly how to fix the issue.


$ sudo make-bcache -C /dev/sda8 -B /dev/sdd1
Device /dev/sda8 already has a non-bcache superblock, remove it using wipefs and wipefs -a

I followed the commands advice and repeated the original command to pair up the cache drive and storage drive.

$ sudo wipefs /dev/sda8
$ sudo wipefs -a /dev/sda8
2 bytes were erased at offset 0x438 (ext4)
they were: 53 ef


$ sudo make-bcache -C /dev/sda8 -B /dev/sdd1
UUID:                   a1dfe2f2-6e69-4e02-8c9c-0239711666fc
Set UUID:               5f01bbd3-c39c-4499-94d5-24f4197547e0
version:                0
nbuckets:               66140
block_size:             1
bucket_size:            1024
nr_in_set:              1
nr_this_dev:            0
first_bucket:           1
Device /dev/sdd1 already has a non-bcache superblock, remove it using wipefs and wipefs -a


I tried a few things but I'm still getting the same error and even after a reboot.

# dd if=/dev/zero of=/dev/sda8 bs=512 count=8
8+0 records in
8+0 records out
4096 bytes (4.1 kB) copied, 0.000331769 s, 12.3 MB/s
# dd if=/dev/zero of=/dev/sdd1 bs=512 count=8  
8+0 records in
8+0 records out
4096 bytes (4.1 kB) copied, 0.0115346 s, 355 kB/s
# 
# wipefs -a /dev/sda8                                
# wipefs -a /dev/sdd1


# make-bcache --wipe-bcache -C /dev/sda8 /dev/sdd1
Can't open dev /dev/sda8: Device or resource busy


And ignoring the message and looking for /dev/bcache* doesn't give any results. 

# ls /dev/bcache*
ls: cannot access /dev/bcache*: No such file or directory


So can on setup bcache with Ubuntu 14.04? Anyone see this before and know what's wrong with the steps taken, and if there is anyway to fix this?

Thx

---

### Post by Horatio on 2015-11-01
============= next ===============

Next since I could figure out why I couldn't restart from what I did previously, Iuse fdisk and delete the partition and REBOOT. So after the beboot recreate the sda8 partition with fdisk and see if this remove what ever is holding the device.

$ sudo wipefs  /dev/sda8
wipefs: error: /dev/sda8: probing initialization failed

$ sudo make-bcache -C /dev/sda8 -B /dev/sdd1
Error statting /dev/sda8: No such file or directory

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x851af7e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1742847      870400   83  Linux
/dev/sda2         1742848     3483647      870400   83  Linux
/dev/sda3         3483648     5224447      870400   83  Linux
/dev/sda4         5224448   234441647   114608600    5  Extended
/dev/sda5         5226496    13615103     4194304   82  Linux swap / Solaris
/dev/sda6        13617152    93308927    39845888   83  Linux
/dev/sda7        93310976   166711295    36700160   83  Linux
/dev/sda8       166713344   234441647    33864152   83  Linux


$ sudo partprobe /dev/sda
$ ls /dev/sda8
/dev/sda8

$ sudo wipefs -a /dev/sda8
$ sudo wipefs -a /dev/sdd1


$ sudo make-bcache -C /dev/sda8 -B /dev/sdd1
Can't open dev /dev/sda8: Device or resource busy


$ lsmod |grep bcache
bcache                229376  2 

$ sudo mkfs.ext3 /dev/sda8
mke2fs 1.42.9 (4-Feb-2014)
/dev/sda8 is apparently in use by the system; will not make a filesystem here!

$ sudo modprobe -r bcache
modprobe: FATAL: Module bcache is in use.


======= Why is all the above holding the device ======

-- There is no bcache device ---

$ ls /sys/block/
loop0  loop2  loop4  loop6  ram0  ram10  ram12  ram14  ram2  ram4  ram6  ram8  sda  sdc  sr0                                                    
loop1  loop3  loop5  loop7  ram1  ram11  ram13  ram15  ram3  ram5  ram7  ram9  sdb  sdd

-- But what is this, something bcache related --

$ ls /sys/block/sda/                                                                                                    
alignment_offset  dev                events             ext_range  power  removable  sda2  sda5  sda8    stat       uevent                      
bdi               device             events_async       holders    queue  ro         sda3  sda6  size    subsystem                              
capability        discard_alignment  events_poll_msecs  inflight   range  sda1       sda4  sda7  slaves  trace             

$ ls /sys/block/sda/sda8/
alignment_offset  bcache  dev  discard_alignment  holders  inflight  partition  power  ro  size  start  stat  subsystem  trace  uevent          
$ ls /sys/block/sda/sda8/bcache/                                                                                        
block_size     bucket_size               clear_stats  io_errors         nbuckets        set                                                     
btree_written  cache_replacement_policy  discard      metadata_written  priority_stats  written      

-- Nothing here bcache related - I'm just comparing a partition that shouldn't be part of bcache and it looks like it's not --

$ ls /sys/block/sda/sda1
alignment_offset  dev  discard_alignment  holders  inflight  partition  power  ro  size  start  stat  subsystem  trace  uevent  


====== Thinking about this. It seems It's not going past the cache creation with the previous command. So, I try to just create the back ====

$ sudo make-bcache -B /dev/sdd1
[sudo] password for thann: 
UUID:                   a9a5731c-bdb3-4b51-ac20-0e66491894aa
Set UUID:               5c2b9b0c-a13e-457e-a1d3-887636325dc7
version:                1
block_size:             1
data_offset:            16


$ ls /sys/block/sdd/sdd1/bcache/
attach       dirty_data                 sequential_cutoff  stats_total         writeback_percent              writeback_rate_update_seconds
cache_mode   label                      state              stop                writeback_rate                 writeback_running
clear_stats  partial_stripes_expensive  stats_day          stripe_size         writeback_rate_debug
detach       readahead                  stats_five_minute  writeback_delay     writeback_rate_d_term
dev          running                    stats_hour         writeback_metadata  writeback_rate_p_term_inverse

$ ls /sys/block/sda/sda8/bcache/
block_size     bucket_size               clear_stats  io_errors         nbuckets        set
btree_written  cache_replacement_policy  discard      metadata_written  priority_stats  written


O.o ~ o.O ~ O.o ~ O.o ~ Apparently that was it ~ o.O ~ O.o ~ O.o ~ o.O ~ O.o

$ ls /dev/bcache
bcache/  bcache0

---

### Post by Horatio on 2015-11-01
lsblk was not showing the bcache0 attached to both sda8 and sdd1. Actually, just sdd1 had bcache attached. But following these I found the answers to the rest of my issue. 

[https://wiki.ubuntu.com/ServerTeam/Bcache](https://wiki.ubuntu.com/ServerTeam/Bcache)
[https://www.kernel.org/doc/Documentation/bcache.txt](https://www.kernel.org/doc/Documentation/bcache.txt)

---

