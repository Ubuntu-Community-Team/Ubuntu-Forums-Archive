---
title: "[Ubuntu Server] Mount Drive, recovery mode"
date: 2014-04-28
forum: General Help
---

### Post by travis17 on 2014-04-28
I recently updated to 13.10 from 12.10. No problems. I then updated from 13.10 to 14.04. When waiting for the system to reboot it never completed. And then the system started a net-boot into recovery mode. In the recovery mode none of the drives are mounted so I have to do it manually. When trying to mount my drives I get.

```
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```


I'll provide some more system info:

```
root@rescue:~# sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1999.0 GB, 1998998994944 bytes
255 heads, 63 sectors/track, 243031 cylinders, total 3904294912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3904294911  1952147455+  ee  GPT
Partition 1 does not start on physical sector boundary.
```


```
root@rescue:~/media# sudo lshw -C disk
  *-disk:0
       description: SCSI Disk
       product: Logical Volume
       vendor: LSI
       physical id: 1.0.0
       bus info: scsi@0:1.0.0
       logical name: /dev/sda
       version: 3000
       serial: 853430924187016622
       size: 1861GiB (1998GB)
       capacity: 1861GiB (1998GB)
       capabilities: 15000rpm gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=c795e09f-5eaa-483b-83b0-34a3f74fea6b sectorsize=4096
  *-disk:1 UNCLAIMED
       description: ATA Disk
       product: HGST HUS724020AL
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       version: AA70
       serial: PN2134P6H0L7UP
       capacity: 1863GiB (2TB)
       capabilities: 15000rpm
       configuration: ansiversion=6
  *-disk:2 UNCLAIMED
       description: ATA Disk
       product: HGST HUS724020AL
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       version: AA70
       serial: PN2134P6H08A2P
       capacity: 1863GiB (2TB)
       capabilities: 15000rpm
       configuration: ansiversion=6

```

---

### Post by tfrue on 2014-04-29
I would like to see a boot-info because that would give a better picture of what's going on, so click on the link to take you to the boot-repair page:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could also click on the UEFI link in my signature and see what head way you can make there. 

Thanks, 
Chris

---

