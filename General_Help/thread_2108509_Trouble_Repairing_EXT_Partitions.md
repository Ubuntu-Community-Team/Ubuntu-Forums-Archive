---
title: "Trouble Repairing EXT Partitions?"
date: 2013-01-24
forum: General Help
---

### Post by Xplorer4x4 on 2013-01-24
I have 2 separate issues here with 2 separate HDDs.

HDD 1. One HDD is reporting 0 space left in dolphin. However, I know I did not use up all the space, and KDE Partition Manager and Gparted show some free space as well. 

HDD 2. The other HDD refuses to mount in Kubuntu. It gives this error message when I try:
```
An error occurred while accessing 'Desktop', the system responded: The kernel driver for this filesystem type is not available.: Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,  missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so
```

dmesg | tail output is:
> xplorer4x4@xplorer4x4-MS-7673:~$ dmesg | tail 
[   20.069634] usb 2-1.5: Manufacturer: La-VIEW Technology
[   20.071514] input: La-VIEW Technology Naos 5000 Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input13
[   20.071770] hid-generic 0003:04B4:1224.0003: input,hiddev0,hidraw2: USB HID v1.00 Keyboard [La-VIEW Technology Naos 5000 Mouse] on usb-0000:00:1d.0-1.5/input0
[   37.277290] EXT4-fs (sdd1): ext4_check_descriptors: Checksum for group 3201 failed (45969!=38902)
[   37.277293] EXT4-fs (sdd1): group descriptors corrupted!
[  306.412413] EXT4-fs (sdc1): error count: 3
[  306.412418] EXT4-fs (sdc1): initial error at 1358560365: ext4_journal_start_sb:371
[  306.412421] EXT4-fs (sdc1): last error at 1358587789: ext4_put_super:887
[  891.420973] EXT4-fs (sdd1): ext4_check_descriptors: Checksum for group 3201 failed (45969!=38902)
[  891.420975] EXT4-fs (sdd1): group descriptors corrupted!


sdd1 is the partition that wont mount.
sdc1 is the partition that mounts but reports incorrect data usage.

I ran "sudo fsck.ext4 -v /dev/sd##" on both drives. 

HDD 1.It quickly claimed to have fixed sdc1 but after a reboot, the problem is still there.

HDD 2. It ran an operation, sorry I do not have th exact out put, forgot to copy and paste before a reboot, but I ran it from about 7PM last night, to 4PM today, and it was still not done, so I rebooted. Problem still exists.


After my initial repair attempts, I have done this:

```
xplorer4x4@xplorer4x4-MS-7673:~$ sudo fsck.ext4 -cDftty -C 0 /dev/sdb1
[sudo] password for xplorer4x4: 
e2fsck 1.42.5 (29-Jul-2012)
Checking for bad blocks (read-only test): done                                                 rors)
WD3: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
                                                                               
Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 73772: 400048627 400048628
Pass 1b: Memory used: 1564k/20016k (1374k/191k), time:  4.65/ 4.61/ 0.03
Pass 1b: I/O read: 163MB, write: 0MB, rate: 35.04MB/s
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1c: Memory used: 1564k/20016k (1374k/191k), time:  9.00/ 0.06/ 0.15
Pass 1c: I/O read: 133MB, write: 0MB, rate: 14.78MB/s
Pass 1D: Reconciling multiply-claimed blocks
(There are 1 inodes containing multiply-claimed blocks.)

File /UFC.on.FX.7.720p.HDTV.x264-KYR/ufc.on.fx.7.720p.hdtv.x264-kyr.r06 (inode #73772, mod time Sun Jan 20 10:21:02 2013) 
  has 2 multiply-claimed block(s), shared with 1 file(s):
        <The bad blocks inode> (inode #1, mod time Wed Jan 23 22:25:29 2013)
Clone multiply-claimed blocks? yes

Error reading block 400048627 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Error reading block 400048628 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Pass 1d: Memory used: 1564k/20016k (1377k/188k), time: 39.08/17.99/ 0.03
Pass 1d: I/O read: 1MB, write: 0MB, rate: 0.03MB/s
Pass 1: Memory used: 1564k/20016k (1330k/235k), time: 126.06/49.57/ 0.51
Pass 1: I/O read: 459MB, write: 1MB, rate: 3.64MB/s
Pass 2: Checking directory structure
Pass 2: Memory used: 2416k/36196k (1260k/1157k), time:  0.91/ 0.27/ 0.03                                                                                                                   
Pass 2: I/O read: 215MB, write: 1MB, rate: 237.20MB/s                                                                                                                                      
Pass 3: Checking directory connectivity                                                                                                                                                    
Peak memory: Memory used: 2416k/36196k (1260k/1157k), time: 19692.12/55.94/ 0.72                                                                                                           
Pass 3A: Optimizing directories                                                                                                                                                            
Pass 3A: Memory used: 3668k/36196k (1402k/2267k), time: 46.86/46.45/ 0.27                                                                                                                  
Pass 3A: I/O read: 145MB, write: 145MB, rate: 6.17MB/s                                                                                                                                     
Pass 3: Memory used: 3668k/35816k (1272k/2397k), time: 46.86/46.45/ 0.27                                                                                                                   
Pass 3: I/O read: 145MB, write: 145MB, rate: 6.17MB/s                                                                                                                                      
Pass 4: Checking reference counts                                                                                                                                                          
Pass 4: Memory used: 3668k/432k (923k/2746k), time:  5.60/ 5.55/ 0.04                                                                                                                      
Pass 4: I/O read: 0MB, write: 0MB, rate: 0.00MB/s                                                                                                                                          
Pass 5: Checking group summary information                                                                                                                                                 
Free blocks count wrong for group #10979 (435, counted=433).                                                                                                                               
Fix? yes                                                                                                                                                                                   
                                                                                                                                                                                           
Free blocks count wrong for group #12208 (65534, counted=0).                                                                                                                               
Fix? yes

Pass 5: Memory used: 3668k/432k (507k/3162k), time:  8.62/ 8.58/ 0.02          
Pass 5: I/O read: 0MB, write: 0MB, rate: 0.00MB/s

WD3: ***** FILE SYSTEM WAS MODIFIED *****
WD3: 380711/111616000 files (1.9% non-contiguous), 430786244/446432285 blocks
Memory used: 3668k/432k (507k/3162k), time: 19773.82/117.50/ 1.10
I/O read: 878MB, write: 197MB, rate: 0.05MB/s

```
Did not fix the 0 space left error. 


As for the other drive, I ran sudo fsck.ext4 -cDftty -C 0 /dev/sdb1 on it as well and it seems hung up on the same file for a few hours now and it is just a small mp3.

---

### Post by Bashing-om on 2013-01-24
Xplorer4x4; Hi ! Welcome to the forum.

You are not running the fsck utility while the partitions are mounted are you ?
Devices must be (un)mounted, simplest way to run fsck is from a liveCD.

Be aware if you run fsck on mounted devices a likely hood is further file system damage.

[INDENT][INDENT]best regards 

[/INDENT][/INDENT]

---

### Post by Xplorer4x4 on 2013-01-24
> **Bashing-om said:**
> Xplorer4x4; Hi ! Welcome to the forum.
Join Date: Feb 2009
I think you are a few years to late :p.

> You are not running the fsck utility while the partitions are mounted are you ?
Devices must be (un)mounted, simplest way to run fsck is from a liveCD.

Be aware if you run fsck on mounted devices a likely hood is further file system damage.


fsck will not let you run on a mounted partition these days. It gives an error message.

---

### Post by oldfred on 2013-01-24
You need to let fsck finish.

run this on both partition, each command.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
If the difference is less than 5%, it can just be that gparted shows the real use and dolphin shows the file use with the 5% reserved space. Normal system partition reserve 5% to prevent you from crashing system or so you start house cleaning before you run out. All systems need some room to work or they really start to slow down.

---

### Post by Xplorer4x4 on 2013-01-24
> **oldfred said:**
> If the difference is less than 5%, it can just be that gparted shows the real use and dolphin shows the file use with the 5% reserved space. Normal system partition reserve 5% to prevent you from crashing system or so you start house cleaning before you run out. All systems need some room to work or they really start to slow down.

Ok responding to this first, according to kde partition manager we are talking about almost 50GB. Math is not be strong point, but I have used up more then that last 50GB before, so this is not an issue. I believe KDE is irrelevant in this case.



> You need to let fsck finish.
It's been stuck on the same file for like 8 hours. I don't think it is going to finish.

> run this on both partition, each command.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Is there any reason I can't do this from in Kubuntu as long as I am sure the partitions are unmounted?? I can,t afford to have my rig down for that long(these are 3TB HDDs)?



Thank you guys for the super fast responses!

---

### Post by Xplorer4x4 on 2013-01-24
> **Bashing-om said:**
> 
Be aware if you run fsck on mounted devices a likely hood is further file system damage.

FYI:
```
xplorer4x4@xplorer4x4-MS-7673:~$ sudo fsck.ext4 -cDftty -C 0 /dev/sdb1
[sudo] password for xplorer4x4: 
e2fsck 1.42.5 (29-Jul-2012)
/dev/sdb1 is mounted.
e2fsck: Cannot continue, aborting.

```

---

### Post by Xplorer4x4 on 2013-01-24
Ok still showing 0 free space:
```

xplorer4x4@xplorer4x4-MS-7673:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
[sudo] password for xplorer4x4: 
                                                                               
      380624 inodes used (0.34%, out of 111616000)
        6946 non-contiguous files (1.8%)
         366 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 799/786/1
             Extent depth histogram: 317679/1740
   429787961 blocks used (96.27%, out of 446432285)
           2 bad blocks
          71 large files

      285606 regular files
       32214 directories
           0 character device files
           0 block device files
           2 fifos
           0 links
       62779 symbolic links (60263 fast symbolic links)
          14 sockets
------------
      380615 files
xplorer4x4@xplorer4x4-MS-7673:~$ sudo fsck.ext4 -v /dev/sdb1
e2fsck 1.42.5 (29-Jul-2012)
WD3: clean, 380624/111616000 files, 429787961/446432285 blocks

```


As for the other drive:
```

xplorer4x4@xplorer4x4-MS-7673:~$ sudo e2fsck -C0 -p -f -v /dev/sdd1
[sudo] password for xplorer4x4: 
Music3TB: One or more block group descriptor checksums are invalid.  FIXED.
Music3TB: Group descriptor 3201 checksum is 0x97f6, should be 0xb391.  

Music3TB: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)

```
I assume I have to run with out the -p and respond manually?

---

### Post by oldfred on 2013-01-24
If you have a 3TB drive then the 5% reserved should be more like 150GB. 

       Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
    
If it is just a data partition not a system partition then you can reduce the reserved space but are still responsible for managing it when you run low.

---

### Post by Xplorer4x4 on 2013-01-24
> **oldfred said:**
> If you have a 3TB drive then the 5% reserved should be more like 150GB. 

       Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
    
If it is just a data partition not a system partition then you can reduce the reserved space but are still responsible for managing it when you run low.
Sorry, it is actually a 2TB down sized to 1.66TB with 1.60 TB free. Now maybe I am misunderstanding the journaling function, but the thing is there was something like 20GB free, and then suddenly it was full. I tried removing some data before, and it was not adding free space. Based on your statement I did the math, and I decided to delete a bunch of old data that was ready for removal anyways. Now I see 33.5GB of space. I am confused though as I thought the journaling was reserved at the time of partitioning?


Now the other HDD. My system crashed during the fsck.ext4 check. So I am running "sudo e2fsck -C0 -p -f -v /dev/sdd1" but again it is spending hours on a single MP3 file. Obviously I can't access the HDD to see the exact size, but it's a single song and 320 Kbps quality, so I am guessing about 5-7MB. If it were a movie files that was a few GB in size, I could understand hours, but for a single MP3 it seems excessive. Any way to estimate how long this will take?

---

### Post by oldfred on 2013-01-25
Not sure why it would just stop on one file unless that file has some kind of major corruption that prevents it from going forward.

Space is use by both journal and the reserved which is adjustable. The reserved is not the journal.

---

### Post by Xplorer4x4 on 2013-01-25
Well form the looks of it, there is some major corruption. The system freeze/reboot probably did not help matters, but what can ya do? It is taking a noticeably long time to repair a number of MP3 files. It is not taking as long now, but still spending a few hours per MP3 and it is on the fourth MP3(partially because I have to hit 

y every time, and partially because the repairs are taking ages). I am not sure if it matters, but the MP3s it is trying to repair, are files I had tried to delete previously. Is there any way to end the repair so I can do some organizing of the drive? In this case, and some others, I want to permanently delete a few lossy albums that I now have in lossless format. the problem is, when I boot into Kubuntu, I can not even get the drive to mount via Dolphin as I normally can.

Anyway, thanks for the info. Guess I need a refresher on EXT file systems.

---

