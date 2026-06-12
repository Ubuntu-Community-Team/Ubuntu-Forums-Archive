---
title: "special character file seen after inserting brand new drive"
date: 2017-07-26
forum: General Help
---

### Post by viswesh2 on 2017-07-26
Hi,

I am using the following kernel in my server (4.4.0-31-generic) and i see the below issue, when i am replacing a drive.

I see the following character device file, after the new drive is inserted. I dont see this file,  when the old drive is removed. (I make sure all IOs to the drive is stopped, before i remove)

```
brw-rw---- 1 root disk 8, 128 Jul 24 19:07 /dev/sdi
cr-------- 1 root root 8, 129 Jul 15 23:50 /dev/sdi1
```     =====> (Who creates with this permissions, i have seen this only in pseudo terminals)

At the same time, i see entries for this partition in /proc/diskstats and /sys/class/block.

```
/proc/diskstats

   8     128 sdi 139089 4 2112504 37000 4473 31 312 9212 0 30764 46144
   8     129 sdi1 21056 0 241392 9308 0 0 0 0 0 8928 9292

```

```
cat /sys/class/block/sdi1/start 
2048
cat /sys/class/block/sdi1/size
15628048384

```


```
$ stat /dev/sdi1

  File: ‘/dev/sdi1’
  Size: 0             Blocks: 0          IO Block: 4096   character special file
Device: 6h/6d    Inode: 723         Links: 1     Device type: 8,81 
Access: (0400/cr--------)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2017-07-15 23:50:00.675853644 +0000
Modify: 2017-07-15 23:50:00.675853644 +0000
Change: 2017-07-15 23:50:00.675853644 +0000
 Birth: -
```


```
$ stat /dev/sdi

  File: ‘/dev/sdi’
  Size: 0             Blocks: 0          IO Block: 4096   block special file
Device: 6h/6d    Inode: 521         Links: 1     Device type: 8,80
Access: (0660/brw-rw----)  Uid: (    0/    root)   Gid: (    6/    disk)
Access: 2017-07-25 23:37:22.598418068 +0000
Modify: 2017-07-25 23:37:22.598418068 +0000
Change: 2017-07-25 23:37:22.598418068 +0000
 Birth: -
```


```
N: sdi
S: disk/by-path/pci-0000:09:00.0-sas-0x5000cca23bd280a5-lun-0
E: DEVNAME=/dev/sdi
E: DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:09:00.0/host0/port-0:0/expander-0:0/port-0:0:13/end_device-0:0:13/target0:0:13/0:0:13:0/block/sdi
E: DEVTYPE=disk
E: ID_BUS=scsi
E: ID_PART_TABLE_TYPE=gpt
E: ID_PATH=pci-0000:09:00.0-sas-0x5000cca23bd280a5-lun-0
E: ID_PATH_TAG=pci-0000_09_00_0-sas-0x5000cca23bd280a5-lun-0
E: ID_REVISION=A7D8
E: ID_SCSI=1
E: ID_SCSI_SERIAL=2EKRSUZV
E: ID_TYPE=disk
E: MAJOR=8
E: MINOR=128
E: SUBSYSTEM=block
E: USEC_INITIALIZED=4744118623
E: nomdmonddf=1
E: nomdmonisw=1
```


Has anyone seen something similar. Who could possibly have created such a file, with block attributes, but a character file.

---

### Post by QIII on 2017-07-26
Hello!

Please enclose all long text and terminal commands and their output in code tags. This will preserve formatting (for instance: you won't get smilies) and make your posts much easier to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. The square brackets are required. 

If you have already posted, you can click **Edit Post** and then **Go Advanced** to get to the # button later.

Cheers!

---

