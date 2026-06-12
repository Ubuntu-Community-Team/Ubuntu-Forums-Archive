---
title: "RAID5 with 6 HDD doesnt start any more"
date: 2016-03-28
forum: General Help
---

### Post by Stefan_Wegerer on 2016-03-28
Hello!

Today I got a Problem with my RAID5. When I have a look on cat /proc/mdstat my Raid in inactive.
I try to stop and assemble it. But it didn´t work and i do really have no idea what to do.
I think there is a Problem with /dev/sdi, but thats not the only one.
Please have a look on this.

thx
Stefan

```

sudo mdadm --assemble /dev/md1 /dev/sda1 /dev/sdb1 /dev/sde1 /dev/sdf1 /dev/sdj1 -v
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 5.
mdadm: /dev/sde1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdj1 is identified as a member of /dev/md1, slot 2.
mdadm: added /dev/sde1 to /dev/md1 as 0 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md1 as 1 (possibly out of date)
mdadm: no uptodate device for slot 3 of /dev/md1
mdadm: added /dev/sda1 to /dev/md1 as 4
mdadm: added /dev/sdb1 to /dev/md1 as 5
mdadm: added /dev/sdj1 to /dev/md1 as 2
mdadm: /dev/md1 assembled from 3 drives - not enough to start the array.



```

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 UUID=05aacc42:d01987b8:abcca14d:ebc488b1 name=SERVER:1
ARRAY /dev/md/0 metadata=1.2 UUID=b2df784a:5959762c:4aba9f58:6d1decff name=SERVER:0
ARRAY /dev/md/2 metadata=1.2 UUID=28edcf5d:cb3cdeab:ac8c3e28:e9a12bf5 name=SERVER:2

```

```

root@SERVER:~# sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 05aacc42:d01987b8:abcca14d:ebc488b1
           Name : SERVER:1  (local to host SERVER)
  Creation Time : Tue Feb 17 18:58:16 2015
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ad6a5887:1a1d7c13:a74d016e:75c20e14


    Update Time : Sun Mar 27 23:41:36 2016
       Checksum : ae593c28 - correct
         Events : 236380


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : ..AAAA ('A' == active, '.' == missing)










root@SERVER:~# sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 05aacc42:d01987b8:abcca14d:ebc488b1
           Name : SERVER:1  (local to host SERVER)
  Creation Time : Tue Feb 17 18:58:16 2015
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e034e1d7:93208cf1:f51c670a:b2f5c93d


    Update Time : Sun Mar 27 23:41:36 2016
       Checksum : a3130c62 - correct
         Events : 236380


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : ..AAAA ('A' == active, '.' == missing)










root@SERVER:~# sudo mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 05aacc42:d01987b8:abcca14d:ebc488b1
           Name : SERVER:1  (local to host SERVER)
  Creation Time : Tue Feb 17 18:58:16 2015
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 45e37cb0:e721d6af:0dd7ad63:7fe1a8d6


    Update Time : Sun Jan 10 15:13:24 2016
       Checksum : 2bba6b1b - correct
         Events : 233735


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAAA ('A' == active, '.' == missing)










root@SERVER:~# sudo mdadm --examine /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 05aacc42:d01987b8:abcca14d:ebc488b1
           Name : SERVER:1  (local to host SERVER)
  Creation Time : Tue Feb 17 18:58:16 2015
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : cc3cb4f6:740da5ff:a7b2bbc1:c151d0be


    Update Time : Sun Mar 27 21:51:15 2016
       Checksum : 85cd90a - correct
         Events : 236375


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : .AAAAA ('A' == active, '.' == missing)










root@SERVER:~# sudo mdadm --examine /dev/sdi1
mdadm: No md superblock detected on /dev/sdi1.










root@SERVER:~# sudo mdadm --examine /dev/sdj1
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 05aacc42:d01987b8:abcca14d:ebc488b1
           Name : SERVER:1  (local to host SERVER)
  Creation Time : Tue Feb 17 18:58:16 2015
     Raid Level : raid5
   Raid Devices : 6


 Avail Dev Size : 5860260785 (2794.39 GiB 3000.45 GB)
     Array Size : 14650649600 (13971.95 GiB 15002.27 GB)
  Used Dev Size : 5860259840 (2794.39 GiB 3000.45 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e865e00f:132b7e08:a56ad0a4:078829b9


    Update Time : Sun Mar 27 23:41:36 2016
       Checksum : 7cd27eb - correct
         Events : 236380


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : ..AAAA ('A' == active, '.' == missing)

```

---

### Post by frostschutz on 2016-03-29
Two disks failed / were kicked out of the RAID for some reason.

/dev/sde1 got kicked first (Update time: Sun Jan 10 15:13:24 2016), followed by /dev/sdf1 (Update time: Sun Mar 27 21:51:15 2016).

The huge discrepancy in time suggests that you ran in degraded state (as good as RAID-0) for months without noticing it. #-o

The other disks have (Update time: Sun Mar 27 23:41:36 2016) so my guess is your system crashed on Sunday 21:51:15 and the 23:41:36 is the time you actually noticed and tried to reboot the machine.

Leave out /dev/sde1 for now, outdated data is not useful for filesystem recovery. Check SMART data for all those disks (smartctl -a /dev/disk), if any disks have reallocated/pending/uncorrectable sectors you should ddrescue them to new disks.

You will have to try to assemble the RAID with /dev/sde1 missing. It might work with the --force option like such:

```
mdadm --assemble --force /dev/md42 /dev/sd[abfj]1
```

Don't use --create, it never works unless you really really know what you are doing. For --create you have to get all variables right (raid level, layout, chunk size, metadata version, data offset, disk order, ...). You can not rely on any default values.

EDIT:

Oh shoot, sdi is missing completely and doesn't even have metadata? What's wrong with your sdi? Chances of survival are dwindling into single-digits now.

---

### Post by Stefan_Wegerer on 2016-03-31
Hey frostschutz!

Thanks for your detailed answer!

The Raid runs and I can access my data :))
After some restarts sdi returns and I was able to assemble it with your recomendation (--force). I got info that the status of sde and sdf need to be updated and thats it... pretty easy :)
I checked the SMART Data of all HDD but they are ok ...only sdi is dead.
My mistake was to check only mdstat from time to time.

I don´t know if I can trust sde. Is there a possibility why sde got kicked out?

Thanks again 
Stefan

---

