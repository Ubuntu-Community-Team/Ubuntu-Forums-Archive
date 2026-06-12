---
title: "raid issues, mdadm not working for me..."
date: 2008-06-20
forum: General Help
---

### Post by Cr0n_J0b on 2008-06-20
I have a troubling problem.  I'm on Ubuntu 7.x and using the latest mdadm tools to create a software RAID array.  I had one array running for a few months with no issues, until i loaded VMware on the systems and started using that volume as my data store...not sure why, but when I installed an windows 2003 server client...it just broke.  What do I mean? 

Well, the install went fine, but then the system locked up.  I restarted and the device /dev/md0 would not mount.  I tried using mdadm -Q --detail /dev/md0, but it said it wansn't active.  I tried mdadm --run --force /dev/md0 and i get 

mdadm: failed to run array /dev/md0: Input/output error

So I tried breaking and resetting it, but could never get it running...I admit, that I'm not all that good at troubleshooting mdadm...so I decided to start fresh.

I got a new (brand new) set of matched 500GB SATA drives and created a new set using the full capacity of each.  This is a Raid 5 array.  I a command like this.

mdadm --create /dev/md0 --device-number=5 level=5 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

That worked great!  I had a new set running degraded.  I formatted for ext3 and all was good again.

until...i started vmware again and tried building my 2003 server client OS.  I got through the installation, but this morning I came in to a black screen and when I rebooted the system, the RAID array is no longer working.  

I can see all of the devices with fdisk and they are all in good shape, but I can't start the array.  I get an IO error.

Now I'm really worried about mdadm in general.  I can't find a way to recover the set, which is a bad thing considering that it's a protected RAID 5 array.  What's the point of using RAID if something like this can take me down completely?

I'm sure there is some function that I can use...or I hope there is...that will allow me to recover this array.  Any help would be appreciated.

thanks

---

### Post by Cr0n_J0b on 2008-06-20
here is some more info.  I ran mdadm -E /dev/sda1 and got

root@media/hdd1# mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 9532350e:f90a31b7:daac6dd9:19bc7f64 (local to host ip68-231-199-99)
  Creation Time : Thu Jun 19 15:48:45 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Fri Jun 20 07:09:39 2008
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : d9a4b64e - correct
         Events : 0.20457

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       0        0        3      faulty removed
   4     4       8       49        4      spare   /dev/sdd1

===============================================================
Now this looks really strange to me.  Why is it showing 5 devices?  I only ever had 4.  It looks like something got in and corrupted my raid config or something.  Any thoughts?

---

### Post by Cr0n_J0b on 2008-06-20
Well i eventually got this restarted.  I basically fdisked a few of the drives and rebooted.  then reassembled and it worked...not sure why...are really scared now that this can happen so easily.  We'll see if it happens again.

---

### Post by fjgaude on 2008-06-21
My experience with mdadm is good... to build a system here's what I do:

a) create partitions of preferably equal size (make sure the type is Linux Raid Autodetect, FD, for each drive)
b) sudo mdadm --create /dev/md[n] --level=N --raid-devices=N  /dev/sd[abc]n 
c) sudo mkfs -t ext3 /dev/md[n]
d) sudo watch cat /proc/mdstat  # ^C to exit
e) sudo mdadm --examine --scan --config=mdadm.conf >> mdadm.conf
f) sudo mount /dev/md64 /mnt/xx

Always make sure the array has finished with installing the filesystem before use. This is done with the watch command. Put the mdadm.conf file in the /etc/mdadm folder; by default it is in your home folder.

Another thing, to use a drive again in another array, umount the present array, stop it, then zero-superblock the drive.


Good luck from here on out.

---

