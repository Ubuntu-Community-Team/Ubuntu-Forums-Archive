---
title: "Seemingly sporadic slow ZFS IO since 22.04"
date: 2023-11-28
forum: General Help
---

### Post by tkae-lp on 2023-11-28
Hi, 

I'm a long time Linux user, but still consider myself a total amateur so please excuse any blatant school boy errors and gaps in knowledge, I'm basically a hobbyist tinkerer ;)

I've recently moved my main media server from Bionic to Jammy - it seemed sensible enough skipping focal but I'm starting to wish I hadn't as a bit of googling seems to indicate that there could be some ZFS issues with jammy, although a lot of the posts I found were vague and/or unhelpful to my situation. I have no idea what it causing the issues I am seeing, so I would appreciate some help diagnosing it.

I have a ZFS array of 8 disks in ZRAID-2, the disks are a few years old, but show no SMART errors. They are aligned properly (as far as I can tell) with ashift=12. The main point is: In bionic, I had never an issue. Since moving to Jammy, I have experienced daily slow downs.

What is confusing me is that I have checked iotop and sysstat and I cannot find a process or application that is causing this. Ie. *it's not something that's caning the array or a scrub when the slow downs occur*.

For example:

```
dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 477.699 s, 13.5 MB/s

```

YUK! What the?!

I would normally expect speeds many times higher even under heavy use, or that's certainly what I have been seeing with this particular box on Bionic.

Yet iostat -d 2 shows this whilst writing the testfile:

```
Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
loop0             0.00         0.00         0.00         0.00          0          0          0
loop1             0.00         0.00         0.00         0.00          0          0          0
loop10            0.00         0.00         0.00         0.00          0          0          0
loop11            0.00         0.00         0.00         0.00          0          0          0
loop12            0.00         0.00         0.00         0.00          0          0          0
loop13            0.00         0.00         0.00         0.00          0          0          0
loop14            0.00         0.00         0.00         0.00          0          0          0
loop2             0.00         0.00         0.00         0.00          0          0          0
loop3             0.00         0.00         0.00         0.00          0          0          0
loop4             0.00         0.00         0.00         0.00          0          0          0
loop5             0.00         0.00         0.00         0.00          0          0          0
loop6             0.00         0.00         0.00         0.00          0          0          0
loop7             0.00         0.00         0.00         0.00          0          0          0
loop8             0.00         0.00         0.00         0.00          0          0          0
loop9             0.00         0.00         0.00         0.00          0          0          0
sda              10.50        22.00        46.00         0.00         44         92          0
sdb              14.50        10.00       114.00         0.00         20        228          0
sdc              10.00        10.00        46.00         0.00         20         92          0
sdd               9.00        22.00        42.00         0.00         44         84          0
sde               0.00         0.00         0.00         0.00          0          0          0
sdf               8.50        10.00        42.00         0.00         20         84          0
sdg              91.50         0.00       792.00         0.00          0       1584          0
sdh               0.00         0.00         0.00         0.00          0          0          0
sdi              12.00        10.00        56.00         0.00         20        112          0
sdj              11.50        22.00        52.00         0.00         44        104          0

```

Note: SDE and SDG are *NOT* part of the array.

And iotop -o shows only some docker apps and occasional journald. All processes of which were present in Bionic and didn't cause a problem. I have stopped the docker containers to confirm and the problem doesn't go away.

Here's it repeated 10 mins later:

```
rm  /mnt/Tank/testfile && dd if=/dev/zero  of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 39.5305 s, 163 MB/s
```

and again 10 mins later:

```
rm /mnt/Tank/testfile && dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 28.5787 s, 225 MB/s

```

So here's the interesting bit. If I reboot - no change. If I export the pool and re-import, I get "up to a day" of good performance again.

The tank is a fair way used but not critically full, fragged, unhealthy etc:

```
zpool get capacity,size,health,fragmentation
NAME       PROPERTY       VALUE     SOURCE
Tank  capacity       67%       -
Tank  size           29T       -
Tank  health         ONLINE    -
Tank  fragmentation  2%        -

```

There are no snaps. Box has plenty of free memory and an E5 Xeon. I'm really scratching my head here. Hoping this is something really silly I've done, because I'm considering testing the array with Focal if I can't get this sorted. Any help greatly appreciated!

---

### Post by MAFoElffen on 2023-11-28
I have 4 systems here as Ubuntu 22.04 and ZFS-On-Root.

Please show the output of these within CODE Tags:
```

sudo zpool -v status <your_raidz_poolname> # Post the ouput of this within CODE Tags
arc_summary > ./arc_summary.txt # Attach this to a post

```
Then in terminal, change directory in the filesystem to where you inside that pool, then do
```

sudo apt update
sudo apt install fio
# navigate to where you want the benchmark to test. Make sure you have at least 2GB free space.
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
Here is the results of that on one of mine in a 5 disk RAIDZ2...
```

mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3678515: Tue Nov 28 09:46:11 2023
  write: IOPS=1032, BW=1033MiB/s (1083MB/s)(10.0GiB/9917msec); 0 zone resets
    slat (usec): min=115, max=9460, avg=486.33, stdev=526.56
    clat (nsec): min=1329, max=4938.7M, avg=29869302.58, stdev=270328002.16
     lat (usec): min=150, max=4940.0k, avg=30355.88, stdev=270371.59
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    6], 20.00th=[    6],
     | 30.00th=[    6], 40.00th=[    6], 50.00th=[    8], 60.00th=[   10],
     | 70.00th=[   12], 80.00th=[   32], 90.00th=[   35], 95.00th=[   53],
     | 99.00th=[   74], 99.50th=[   78], 99.90th=[ 4933], 99.95th=[ 4933],
     | 99.99th=[ 4933]
   bw (  MiB/s): min=  452, max= 5082, per=100.00%, avg=1993.80, stdev=1665.68, samples=10
   iops        : min=  452, max= 5082, avg=1993.80, stdev=1665.68, samples=10
  lat (usec)   : 2=0.02%, 4=0.02%, 50=0.01%, 250=0.02%, 500=0.05%
  lat (usec)   : 750=0.04%, 1000=0.06%
  lat (msec)   : 2=0.17%, 4=0.35%, 10=62.03%, 20=12.71%, 50=18.79%
  lat (msec)   : 100=5.43%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=523, max=523, avg=523.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  524],  5.00th=[  524], 10.00th=[  524], 20.00th=[  524],
     | 30.00th=[  524], 40.00th=[  524], 50.00th=[  524], 60.00th=[  524],
     | 70.00th=[  524], 80.00th=[  524], 90.00th=[  524], 95.00th=[  524],
     | 99.00th=[  524], 99.50th=[  524], 99.90th=[  524], 99.95th=[  524],
     | 99.99th=[  524]
  cpu          : usr=4.03%, sys=28.00%, ctx=25070, majf=14, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

[COLOR=#ff0000]Run status group 0 (all jobs):
  WRITE: bw=1033MiB/s (1083MB/s), 1033MiB/s-1033MiB/s (1083MB/s-1083MB/s), io=10.0GiB (10.7GB), run=9917-9917msec[/COLOR]

mafoelffen@Mikes-B460M:/data$ sudo zpool status -v datapool
[sudo] password for mafoelffen:
  pool: datapool
 state: ONLINE
status: One or more devices has experienced an unrecoverable error.  An
    attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
    using 'zpool clear' or replace the device with 'zpool replace'.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P
  scan: scrub repaired 0B in 00:20:08 with 0 errors on Wed Nov 22 08:44:43 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     6     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

```
Dang. (Doing a Scrub on that pool now...)

EDIT: Scrub done. Reran benchmark. Same test results (same speed).

---

### Post by tkae-lp on 2023-11-28
Hi, 

Thanks for the comprehensive reply. Yeah this is an odd one. I've been using ZFS on Ubuntu for years and have never had any issues until now, not even the slightest blip.

As requested:

```
sudo zpool status -v Tank
  pool: Tank
 state: ONLINE
  scan: scrub repaired 0B in 10:00:01 with 0 errors on Mon Nov 13 23:01:24 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    Tank                                  ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300XXXX  ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX  ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0

errors: No known data errors

```

arc_summary: [https://pastebin.ubuntu.com/p/5ZDtsNzX7v/](https://pastebin.ubuntu.com/p/5ZDtsNzX7v/)

FIO:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write  --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio  --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60  --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][46.7%][w=274MiB/s][w=274 IOPS][eta 00m:08s]
Jobs: 1 (f=1): [W(1)][65.0%][w=392MiB/s][w=392 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [W(1)][73.1%][w=40.0MiB/s][w=40 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [W(1)][73.5%][w=63.0MiB/s][w=63 IOPS][eta 00m:09s] 
Jobs: 1 (f=1): [W(1)][83.8%][w=289MiB/s][w=289 IOPS][eta 00m:06s] 
Jobs: 1 (f=1): [W(1)][97.4%][w=232MiB/s][w=232 IOPS][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][97.7%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][97.8%][eta 00m:01s]
TEST: (groupid=0, jobs=1): err= 0: pid=1241014: Tue Nov 28 23:44:29 2023
  write: IOPS=235, BW=235MiB/s (247MB/s)(10.0GiB/43556msec); 0 zone resets
    slat (usec): min=252, max=53915, avg=3569.49, stdev=4839.84
    clat (usec): min=3, max=7052.4k, avg=131421.17, stdev=405561.87
     lat (usec): min=313, max=7056.0k, avg=134991.41, stdev=407262.28
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   16], 20.00th=[   21],
     | 30.00th=[   63], 40.00th=[   72], 50.00th=[   81], 60.00th=[   88],
     | 70.00th=[   99], 80.00th=[  120], 90.00th=[  207], 95.00th=[  426],
     | 99.00th=[  944], 99.50th=[ 1028], 99.90th=[ 7013], 99.95th=[ 7013],
     | 99.99th=[ 7080]
   bw (  KiB/s): min=28672, max=2134016, per=100.00%, avg=280756.99, stdev=332876.74, samples=74
   iops        : min=   28, max= 2084, avg=274.18, stdev=325.08, samples=74
  lat (usec)   : 4=0.02%, 10=0.03%, 500=0.02%, 1000=0.01%
  lat (msec)   : 2=0.05%, 4=0.13%, 10=0.63%, 20=18.89%, 50=7.08%
  lat (msec)   : 100=43.91%, 250=21.15%, 500=4.10%, 750=2.07%, 1000=1.32%
  lat (msec)   : 2000=0.29%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1223, max=1223, avg=1223.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1224],  5.00th=[ 1224], 10.00th=[ 1224], 20.00th=[ 1224],
     | 30.00th=[ 1224], 40.00th=[ 1224], 50.00th=[ 1224], 60.00th=[ 1224],
     | 70.00th=[ 1224], 80.00th=[ 1224], 90.00th=[ 1224], 95.00th=[ 1224],
     | 99.00th=[ 1224], 99.50th=[ 1224], 99.90th=[ 1224], 99.95th=[ 1224],
     | 99.99th=[ 1224]
  cpu          : usr=1.68%, sys=10.99%, ctx=76215, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=235MiB/s (247MB/s), 235MiB/s-235MiB/s (247MB/s-247MB/s), io=10.0GiB (10.7GB), run=43556-43556msec


```

and again 10 mins later:

```
fio --name TEST  --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g  --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32  --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][11.7%][eta 00m:53s]
Jobs: 1 (f=1): [W(1)][20.0%][w=3072KiB/s][w=3 IOPS][eta 00m:48s]
Jobs: 1 (f=1): [W(1)][30.0%][w=3075KiB/s][w=3 IOPS][eta 00m:42s] 
Jobs: 1 (f=1): [W(1)][40.0%][w=4096KiB/s][w=4 IOPS][eta 00m:36s] 
Jobs: 1 (f=1): [W(1)][50.0%][w=4100KiB/s][w=4 IOPS][eta 00m:30s] 
Jobs: 1 (f=1): [W(1)][60.0%][w=3072KiB/s][w=3 IOPS][eta 00m:24s] 
Jobs: 1 (f=1): [W(1)][70.0%][w=2050KiB/s][w=2 IOPS][eta 00m:18s] 
Jobs: 1 (f=1): [W(1)][80.0%][w=2048KiB/s][w=2 IOPS][eta 00m:12s] 
Jobs: 1 (f=1): [W(1)][90.0%][w=3072KiB/s][w=3 IOPS][eta 00m:06s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=3075KiB/s][w=3 IOPS][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][1.4%][w=3072KiB/s][w=3 IOPS][eta 01h:10m:46s]
TEST: (groupid=0, jobs=1): err= 0: pid=1368279: Tue Nov 28 23:53:39 2023
  write: IOPS=2, BW=3003KiB/s (3075kB/s)(177MiB/60356msec); 0 zone resets
    slat (msec): min=221, max=660, avg=340.97, stdev=83.41
    clat (usec): min=13, max=14102k, avg=9758855.47, stdev=3033929.82
     lat (msec): min=363, max=14413, avg=10099.83, stdev=3058.23
    clat percentiles (msec):
     |  1.00th=[  363],  5.00th=[ 2567], 10.00th=[ 5470], 20.00th=[ 8221],
     | 30.00th=[ 8792], 40.00th=[ 9597], 50.00th=[10268], 60.00th=[10671],
     | 70.00th=[11073], 80.00th=[12281], 90.00th=[13355], 95.00th=[13758],
     | 99.00th=[14026], 99.50th=[14160], 99.90th=[14160], 99.95th=[14160],
     | 99.99th=[14160]
   bw (  KiB/s): min= 2048, max= 4104, per=99.90%, avg=3000.53, stdev=1026.58, samples=99
   iops        : min=    2, max=    4, avg= 2.93, stdev= 1.00, samples=99
  lat (usec)   : 20=0.56%
  lat (msec)   : 500=0.56%, 750=0.56%, 1000=0.56%, 2000=1.69%, >=2000=96.05%
  cpu          : usr=0.03%, sys=0.28%, ctx=1432, majf=0, minf=10
  IO depths    : 1=0.6%, 2=1.1%, 4=2.3%, 8=4.5%, 16=9.0%, 32=82.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.3%, 8=0.0%, 16=0.0%, 32=0.7%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,177,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3003KiB/s (3075kB/s), 3003KiB/s-3003KiB/s (3075kB/s-3075kB/s), io=177MiB (186MB), run=60356-60356msec

```

But if I use my previous testing method as something to measure against, I don't appear to be in a massive slow down right now:

```
dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync 
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 56.0559 s, 115 MB/s
```

I  may have to monitor this for a couple of days and re-run fio when I see  things drop to the abysmal 35MB/s... unless anything stands out to you?  Nothing on a physical level has changed since Bionic. This has to be  some sort of config issue?


Edit: here's another one:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][23.3%][w=134MiB/s][w=134 IOPS][eta 00m:23s]
Jobs: 1 (f=1): [W(1)][35.1%][w=188MiB/s][w=188 IOPS][eta 00m:24s] 
Jobs: 1 (f=1): [W(1)][44.2%][w=167MiB/s][w=167 IOPS][eta 00m:24s] 
Jobs: 1 (f=1): [W(1)][49.0%][eta 00m:26s]                         
Jobs: 1 (f=1): [W(1)][51.7%][eta 00m:29s]                       
Jobs: 1 (f=1): [W(1)][61.7%][w=4100KiB/s][w=4 IOPS][eta 00m:23s] 
Jobs: 1 (f=1): [W(1)][71.7%][eta 00m:17s]                        
Jobs: 1 (f=1): [W(1)][81.7%][w=180MiB/s][w=180 IOPS][eta 00m:11s]
Jobs: 1 (f=1): [W(1)][91.7%][eta 00m:05s]                        
Jobs: 1 (f=1): [W(1)][100.0%][w=5120KiB/s][w=5 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1759323: Wed Nov 29 00:20:56 2023
  write: IOPS=100, BW=101MiB/s (106MB/s)(6076MiB/60205msec); 0 zone resets
    slat (usec): min=49, max=6932.0k, avg=9330.20, stdev=147502.33
    clat (msec): min=2, max=11969, avg=307.67, stdev=1279.78
     lat (msec): min=2, max=11969, avg=317.00, stdev=1303.51
    clat percentiles (msec):
     |  1.00th=[   39],  5.00th=[   57], 10.00th=[   65], 20.00th=[   65],
     | 30.00th=[   69], 40.00th=[   77], 50.00th=[   80], 60.00th=[  124],
     | 70.00th=[  167], 80.00th=[  186], 90.00th=[  262], 95.00th=[  472],
     | 99.00th=[10000], 99.50th=[11208], 99.90th=[12013], 99.95th=[12013],
     | 99.99th=[12013]
   bw (  KiB/s): min= 2048, max=466944, per=100.00%, avg=179392.93, stdev=151093.97, samples=69
   iops        : min=    2, max=  456, avg=175.19, stdev=147.55, samples=69
  lat (msec)   : 4=0.03%, 10=0.07%, 20=0.28%, 50=0.87%, 100=53.83%
  lat (msec)   : 250=34.53%, 500=5.74%, 750=1.10%, 1000=1.04%, 2000=0.64%
  lat (msec)   : >=2000=1.86%
  cpu          : usr=0.60%, sys=0.72%, ctx=2228, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,6076,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=101MiB/s (106MB/s), 101MiB/s-101MiB/s (106MB/s-106MB/s), io=6076MiB (6371MB), run=60205-60205msec

Disk stats (read/write):
  sdg: ios=153/12344, merge=59/268, ticks=133897/2984697, in_queue=3133595, util=98.20%

```

---

### Post by tkae-lp on 2023-11-28
This one could be of interest. I was trying to watch a 4K film and it kept buffering:

```
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 166.54 s, 38.7 MB/s

```

FIO:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][46.7%][w=544MiB/s][w=543 IOPS][eta 00m:08s]
Jobs: 1 (f=1): [W(1)][81.2%][w=539MiB/s][w=538 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][97.4%][eta 00m:01s]  
Jobs: 1 (f=1): [W(1)][97.7%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.0%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.2%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.4%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.5%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.6%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][97.5%][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][97.6%][eta 00m:02s] 
TEST: (groupid=0, jobs=1): err= 0: pid=2088223: Wed Nov 29 03:39:02 2023
  write: IOPS=123, BW=123MiB/s (129MB/s)(9.77GiB/81154msec); 0 zone resets
    slat (usec): min=330, max=2347, avg=1662.85, stdev=375.10
    clat (usec): min=8, max=64494k, avg=251199.55, stdev=3581236.17
     lat (usec): min=1764, max=64496k, avg=252863.29, stdev=3581238.17
    clat percentiles (msec):
     |  1.00th=[   16],  5.00th=[   29], 10.00th=[   30], 20.00th=[   44],
     | 30.00th=[   55], 40.00th=[   57], 50.00th=[   57], 60.00th=[   59],
     | 70.00th=[   59], 80.00th=[   59], 90.00th=[   59], 95.00th=[   59],
     | 99.00th=[   64], 99.50th=[   66], 99.90th=[17113], 99.95th=[17113],
     | 99.99th=[17113]
   bw (  KiB/s): min=241664, max=1162986, per=100.00%, avg=600417.24, stdev=172620.70, samples=34
   iops        : min=  236, max= 1135, avg=586.32, stdev=168.50, samples=34
  lat (usec)   : 10=0.04%
  lat (msec)   : 2=0.03%, 4=0.04%, 10=0.12%, 20=1.00%, 50=18.98%
  lat (msec)   : 100=79.48%, >=2000=0.31%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=2055, max=2055, avg=2055.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 2064],  5.00th=[ 2064], 10.00th=[ 2064], 20.00th=[ 2064],
     | 30.00th=[ 2064], 40.00th=[ 2064], 50.00th=[ 2064], 60.00th=[ 2064],
     | 70.00th=[ 2064], 80.00th=[ 2064], 90.00th=[ 2064], 95.00th=[ 2064],
     | 99.00th=[ 2064], 99.50th=[ 2064], 99.90th=[ 2064], 99.95th=[ 2064],
     | 99.99th=[ 2064]
  cpu          : usr=0.79%, sys=7.03%, ctx=66585, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10000,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=123MiB/s (129MB/s), 123MiB/s-123MiB/s (129MB/s-129MB/s), io=9.77GiB (10.5GB), run=81154-81154msec

```

The job percentages are very different this time.

---

### Post by MAFoElffen on 2023-11-29
That is crazy how much difference there is in this:
```

WRITE: bw=235MiB/s (247MB/s), 235MiB/s-235MiB/s (247MB/s-247MB/s), io=10.0GiB (10.7GB), run=43556-43556msec
WRITE: bw=3003KiB/s (3075kB/s), 3003KiB/s-3003KiB/s (3075kB/s-3075kB/s), io=177MiB (186MB), run=60356-60356msec
WRITE: bw=101MiB/s (106MB/s), 101MiB/s-101MiB/s (106MB/s-106MB/s), io=6076MiB (6371MB), run=60205-60205msec

```
The drives alone are rated at 180MB/s for each drive. You have my interest and curiosity.

Please post the output of these:
```

sudo zpool list -o name,free,cap,frag,ashift tank
sudo zfs list -r -o name,used,usedbydataset,avail,compressratio,recordsize,mounted tank

```
Then run the 'system-info' script in my signature line... But before you run the script, run it with this startup option
```

./system-info --details

```
That will turn on more details about the storage controllers and the ZFS filesystems for the report. Please choose to upload it to a pastebin and poet the URL to it.

---

### Post by tkae-lp on 2023-11-29
I had considered faulty hardware such as SATA cables, but the issue occurred exactly at the point of moving to Jammy.

```
sudo zpool list -o name,free,cap,frag,ashift Tank 
NAME        FREE    CAP   FRAG  ASHIFT
Tank       9.29T    67%     2%      12
```


```
sudo zfs list -r -o name,used,usedbydataset,avail,compressratio,recordsize,mounted Tank 
NAME                USED  USEDDS  AVAIL  RATIO  RECSIZE  MOUNTED
Tank               14.0T   14.0T  6.36T  1.00x     128K  yes
Tank/Docker        14.2G   14.2G  6.36T  1.10x     128K  yes
Tank/Backups       15.5G   15.5G  6.36T  1.05x     128K  yes

```

Script output: [https://paste.ubuntu.com/p/96zC2YWRCG/](https://paste.ubuntu.com/p/96zC2YWRCG/)

---

### Post by #&amp;thj^% on 2023-11-29
> **MAFoElffen said:**
> That is crazy how much difference there is in this:

My Interest as well:
```
Run status group 0 (all jobs):
  WRITE: bw=1788MiB/s (1875MB/s), 1788MiB/s-1788MiB/s (1875MB/s-1875MB/s), io=10.0GiB (10.7GB), run=5728-5728msec

```
Your Cap may come in to play mine:
```
&#9492;&#9472;> sudo zpool list -o name,free,cap,frag,ashift rpool
NAME    FREE    CAP   FRAG  ASHIFT
rpool   222G     4%     1%      12
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo zpool list -o name,free,cap,frag,ashift bpool
NAME    FREE    CAP   FRAG  ASHIFT
bpool  1.75G     6%     0%      12

```

---

### Post by MAFoElffen on 2023-11-29
I see yo have 11 SATA'a with the OS being on SSD. 

I'm seeing a NVidia GPU, which is probable in Slot 6.

I see 6 SATA slots on the mainboard, with another SATA HBA (possibly) in slot #5(?) 

Which of those disks are on the mainboard and which are on the HBA?

---

### Post by MAFoElffen on 2023-11-29
Dang. was writing this and accidentally closed the tab. Ouch. Writing this again. LOL

I see 32GB of memory. 21TB of zpool. 8GB + (1BG/TBx21TB=21GB) = 29GB just for ZFS... Leaving 3GB. ARC is going to take up to 10.5GB...

If you are watching movies when this happens, then it is doing reads, and using ARC... 

Next time it does that, try this:
```

RESET=$(grep . /sys/module/zfs/parameters/zfs_arc_shrinker_limit)
sudo echo 0 > /sys/module/zfs/parameters/zfs_arc_shrinker_limit
sudo echo 3 > /proc/sys/vm/drop_caches

```
See if that improves that, that will clear the ARC caches, as if you had exported & imported the zpool... That would free up about 8GB of memory...

Then later do
```

sudo echo $RESET > /sys/module/zfs/parameters/zfs_arc_shrinker_limit

```
That will reset it back to it's default of 10000. If that solves it, then I'll describes how to reset the ARC size a bit lower. Or, do you have any free SATA slot left?

Another thing I saw is that you have an NVidia Card & 11 SATA's. There is 6 SATA port on the mainboard. I'm assuming that you have the NVidia card in Slot 6? The other SATA HBA in Slot 5?

Slot 6 is Gen 3.0 and Slot 5 is Gen 2....
```

PCI Express: Unidirectional Bandwidth in x1 and x16 Configurations

Generation     Year of Release     Data Transfer Rate     Bandwidth x1     Bandwidth x16
PCIe 1.0       2003                2.5 GT/s               250 MB/s         4.0 GB/s
PCIe 2.0       2007                5.0 GT/s               500 MB/s         8.0 GB/s
PCIe 3.0       2010                8.0 GT/s               1 GB/s           16 GB/s
PCIe 4.0       2017                16 GT/s                2 GB/s           32 GB/s
PCIe 5.0       2019                32 GT/s                4 GB/s           64 GB/s
PCIe 6.0       2021                64 GT/s                8 GB/s           128 GB/s

```
You could try swaying the GPU card and the HBA...

---

### Post by tkae-lp on 2023-11-30
> **1fallen said:**
> Your Cap may come in to play

I had wondered this, but my limited knowledge of ZFS is that the performance shouldn't degrade by any meaningful amount until about 80%? And why not on Bionic?

> **MAFoElffen said:**
> Or, do you have any free SATA slot left?

There is an unused NMVe slot, are you thinking I should throw something in there for arc and logs? (Edit:  And, to be honest, along with the NMVe, probably time to drop some more memory in?)

> **MAFoElffen said:**
> Another thing I saw is that you have an NVidia Card & 11 SATA's. There is 6 SATA port on the mainboard. I'm assuming that you have the NVidia card in Slot 6? The other SATA HBA in Slot 5?

No, there are 10 on board SATA slots the board is a beast (or was at the time!) - I don't have an HBA card. 8 x 4TB SATA disks for the array, 1 x 500GB SATA for downloads (torrents/nzb so it doesn't cane the array) 1 x SATA SSD for OS... all on main board.

GPU is in slot 5, I think? IIRC this is because it touches the Noctua CPU heat sink if in slot 6.

Here is the board: [https://www.asrock.com/mb/Intel/X99%20WS/](https://www.asrock.com/mb/Intel/X99%20WS/) it's from the workstation line.

The only thing I miss is IPMI, but we got it cheap and it supports ECC so that's what we ended up with.

> **MAFoElffen said:**
> Next time it does that, try this

Thanks - watch this space.. I'll report back asap.

Edit: If the ARC is the issue, and more memory is required, what I don't get is how significantly different Jammy is to Bionic. I always start off with minimal server for my installs, and then because I do like a GUI do a bare minimum xfce install without using group packages wherever possible. Is Jammy really using that much more memory than Bionic?!

---

### Post by MAFoElffen on 2023-11-30
> **tkae-lp said:**
> I had wondered this, but my limited knowledge of ZFS is that the performance shouldn't degrade by any meaningful amount until about 80%? And why not on Bionic?

There is an unused NMVe slot, are you thinking I should throw something in there for arc and logs? (Edit:  And, to be honest, along with the NMVe, probably time to drop some more memory in?)

No, there are 10 on board SATA slots the board is a beast (or was at the time!) - I don't have an HBA card. 8 x 4TB SATA disks for the array, 1 x 500GB SATA for downloads (torrents/nzb so it doesn't cane the array) 1 x SATA SSD for OS... all on main board.

GPU is in slot 5, I think? IIRC this is because it touches the Noctua CPU heat sink if in slot 6.

Here is the board: [https://www.asrock.com/mb/Intel/X99%20WS/](https://www.asrock.com/mb/Intel/X99%20WS/) it's from the workstation line.

The only thing I miss is IPMI, but we got it cheap and it supports ECC so that's what we ended up with.

Thanks - watch this space.. I'll report back asap.

Edit: If the ARC is the issue, and more memory is required, what I don't get is how significantly different Jammy is to Bionic. I always start off with minimal server for my installs, and then because I do like a GUI do a bare minimum xfce install without using group packages wherever possible. Is Jammy really using that much more memory than Bionic?!
RE: [https://ubuntuforums.org/showthread.php?t=2486010](https://ubuntuforums.org/showthread.php?t=2486010)

That is a thread 1fallen and I helped a user with where we dove deeply  into ZFS RAIDZ performance, with hardware SLOG and L2ARC caches. (It was  a lot of fun!!!) That was also about the time I was upgrading my server  and workstation. The result we found from that, drove what I did for  them. 

As you can see, both 1fallen and I are not afraid to go outside the norms to test things. Some times what they tell us are assumptions. Many times, I know I might break things by trying things that they tell us will not work. I'll try them to see if they work or not... and if it doesn't what it actually does when it blows up. That is what I found there in those tests with disk caches.

I have been using ZFS since 2005 with OpenSolaris. I started testing ZFS  for Linux since Ubuntu 12.04... Then the builds from FreeBSD. I didn't  see any hit in performance from 18.04 through 22.04. Actually the  opposite.

18.04 used 0.7.5, we are currently at, testing and verifying 2.2.1 from Noble proposed.

These are from my notes from 20.04 to 22.04:
> 
Performance
[LIST]
[*]    Improved performance for interactive I/O. #11166 #11116 
[*]    Optimized prefetch for parallel workloads. #11652 
[*]    Improved scalability by reduced contention on locks and atomics. #11288 #12172 #12145 #11904 
[*]    Reduced pool import time. #11470 #11502 #11469 #11467 #11467 
[*]    Reduced fragmentation from ZIL blocks. #11389 
[*]    Improved zfs receive performance with lightweight write. #11105 
[*]    Improved memory management. #12152 #11429 #11574 #12150 
[*]    Improved module load time. #11282 
[/LIST]

I'm guilty of challenging 1fallen to try, learn and use ZFS... LOL. 

1fallen tells me that he notices on his, that he starts noticeably seeing performance changes at about 65%. ZFS does use a lot of memory. Ubuntu says you need 4GB for Ubuntu. Since 20.04, I see pegging 4GB's during an install of Server. ZFS needs at least 8GB to run. Then 1 GB for each TB of storage. Both my Server and Workstation have 132GB of Gaming memory. 

But on the other end of that, my Old Lenovo ThinkPad T520 Laptop is maxed out at 16G RAM, and has 6TB SSD storage. For that much ZFS storage it should have 18GB RAM. I tuned it by limiting the ARC, to where it performs it's best. It runs great.

It doesn't cost me anything but time, to play with things, and make them run well.

Your's is very much "a curiosity" to me, as playing movies is just a read. My stored media for my media server is just on HDD. I run mine on my workstation, and notice nothing while my wife watches movies, and I am running my tests, thrashing that machine doing other things. Media services doesn't take much. My son runs his off of a Rasp Pi4, running Ubuntu Server and USB attached storage.

Yours is very strange in that it is intermittent. We can see your "best case" performance, but that does not explain what is going on when it is dragging down slow. <-- We have not found what is dragging that system down. We have not found the "cause". It could be something with ZFS, or something else that is dragging down ZFS performance with it. That is what my curiosity is.

The fio command I gave you was for writes, which would be slower than reads. Just change "write'" to "read" and that will test your reads.

---

### Post by tkae-lp on 2023-11-30
That linked thread is very interesting - I'm all up for doing things outside the norms or recommended ways if it works ;) I only care about results. I love ZFS so I will try anything and persevere ;) Haven't had a 'blip' in my FLAC collection since... well, using ZFS! <3

> **MAFoElffen said:**
> That would free up about 8GB of memory...

Wow... actually it freed up nearer 18GB :shock:

So after clearing ARC caches I get: 

```
dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 226.487 s, 28.4 MB/s

```

and:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [R(1)][100.0%][r=3094MiB/s][r=3094 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1512586: Fri Dec  1 01:26:23 2023
  read: IOPS=2869, BW=2870MiB/s (3009MB/s)(10.0GiB/3568msec)
    slat (usec): min=178, max=1970, avg=345.04, stdev=110.20
    clat (usec): min=3, max=49773, avg=10664.54, stdev=3102.23
     lat (usec): min=192, max=50837, avg=11010.13, stdev=3203.26
    clat percentiles (usec):
     |  1.00th=[ 3851],  5.00th=[ 5932], 10.00th=[ 5997], 20.00th=[ 6325],
     | 30.00th=[11207], 40.00th=[11338], 50.00th=[11338], 60.00th=[11469],
     | 70.00th=[11600], 80.00th=[11600], 90.00th=[13435], 95.00th=[13566],
     | 99.00th=[16712], 99.50th=[19530], 99.90th=[44827], 99.95th=[48497],
     | 99.99th=[49546]
   bw (  MiB/s): min= 1968, max= 3102, per=98.28%, avg=2820.57, stdev=394.85, samples=7
   iops        : min= 1968, max= 3102, avg=2820.57, stdev=394.85, samples=7
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.05%, 1000=0.09%
  lat (msec)   : 2=0.25%, 4=0.49%, 10=20.02%, 20=78.52%, 50=0.44%
  cpu          : usr=1.01%, sys=98.68%, ctx=36, majf=0, minf=8206
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2870MiB/s (3009MB/s), 2870MiB/s-2870MiB/s (3009MB/s-3009MB/s), io=10.0GiB (10.7GB), run=3568-3568msec

```

Whilst doing the above read, I see: 

```
Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
loop0             0.00         0.00         0.00         0.00          0          0          0
loop1             0.00         0.00         0.00         0.00          0          0          0
loop10            0.00         0.00         0.00         0.00          0          0          0
loop11            0.00         0.00         0.00         0.00          0          0          0
loop12            0.00         0.00         0.00         0.00          0          0          0
loop13            0.00         0.00         0.00         0.00          0          0          0
loop14            0.00         0.00         0.00         0.00          0          0          0
loop2             0.00         0.00         0.00         0.00          0          0          0
loop3             0.00         0.00         0.00         0.00          0          0          0
loop4             0.00         0.00         0.00         0.00          0          0          0
loop5             0.00         0.00         0.00         0.00          0          0          0
loop6             0.00         0.00         0.00         0.00          0          0          0
loop7             0.00         0.00         0.00         0.00          0          0          0
loop8             0.00         0.00         0.00         0.00          0          0          0
loop9             0.00         0.00         0.00         0.00          0          0          0
sda              16.50         0.00      1030.00         0.00          0       2060          0
sdb              12.50         0.00      1030.00         0.00          0       2060          0
sdc              19.00         0.00      1028.00         0.00          0       2056          0
sdd              20.00         0.00      1026.00         0.00          0       2052          0
sde               0.00         0.00         0.00         0.00          0          0          0
sdf              19.00         0.00      1030.00         0.00          0       2060          0
sdg               0.00         0.00         0.00         0.00          0          0          0
sdh               6.00         0.00      1044.00         0.00          0       2088          0
sdi              18.00         0.00      1032.00         0.00          0       2064          0
sdj              18.50         0.00      1030.00         0.00          0       2060          0


```

(presumably the above is whilst it writes the file first to read back, but it's SLOW... took 5 mins or so)

And at the same time, a 1080p film froze and my whole XFCE environment got very sluggish :(

Then after: 

```
sudo echo $RESET > /sys/module/zfs/parameters/zfs_arc_shrinker_limit
```

I see and increase in mem usage by about 2-3GB within a minute or so and then: 

```
dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 21.0576 s, 306 MB/s

```

and

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [R(1)][80.0%][r=2721MiB/s][r=2721 IOPS][eta 00m:01s]
TEST: (groupid=0, jobs=1): err= 0: pid=1520710: Fri Dec  1 01:31:49 2023
  read: IOPS=2699, BW=2700MiB/s (2831MB/s)(10.0GiB/3793msec)
    slat (usec): min=303, max=885, avg=367.12, stdev=31.61
    clat (usec): min=3, max=25151, avg=11375.32, stdev=1025.73
     lat (usec): min=348, max=26038, avg=11742.93, stdev=1040.92
    clat percentiles (usec):
     |  1.00th=[ 7308],  5.00th=[11207], 10.00th=[11207], 20.00th=[11338],
     | 30.00th=[11338], 40.00th=[11338], 50.00th=[11338], 60.00th=[11338],
     | 70.00th=[11469], 80.00th=[11469], 90.00th=[11600], 95.00th=[11731],
     | 99.00th=[13566], 99.50th=[13566], 99.90th=[21627], 99.95th=[23462],
     | 99.99th=[24773]
   bw (  MiB/s): min= 2464, max= 2752, per=99.69%, avg=2691.43, stdev=100.89, samples=7
   iops        : min= 2464, max= 2752, avg=2691.43, stdev=100.89, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.26%, 10=0.81%, 20=98.50%, 50=0.14%
  cpu          : usr=1.56%, sys=98.36%, ctx=5, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2700MiB/s (2831MB/s), 2700MiB/s-2700MiB/s (2831MB/s-2831MB/s), io=10.0GiB (10.7GB), run=3793-3793msec

```

The above completed quickly (less than 20 seconds?). Please excuse the rough time estimates. It's nearly 2.30am here and I need to turn in. ;)

Memory usage still climbing by another 3GB after several minutes.

At this point, movie watching is nice and snappy again. You can skip forwards/backwards by an hour and it's instant. I know the dd command I am using isn't ideal, but it's still certainly slower than I would have hoped.

So I guess the obvious next question is: where do I go from here? I'm quite happy to get an NMVe and more RAM. Right time of year to be grabbing stuff. I have a 512GB NMVe spare here, but I am happy to grab a 1TB or 2TB. 

More memory is always good but unfortunately the board is 128GB max, so I could grab 2 x 64GB modules but it's a waste of the existing 16s. I currently have 2 x Micron 36ASF2G72PZ-2G1A2 modules in there and Micron 64s seem to be about £154 each new... I know it's not ideal having mismatched brands and sizes but I could get 2 x 32GB SK-Hynix modules for £80 preowned, giving me 96GB for not a lot of money. This seems like the logical choice to me.

1TB crucial NMVe is ~£53 a 2TB is ~£87. I don't mind spending if needed but also have to bear in mind Christmas is round the corner. What would you guys do? At the end of the day I just want it to work, so if I have to spend £167 on it, then it is what it is.

 I said in my original post that there was plenty of free memory, but I have been watching it, and there's actually not a lot... I must have had a brain fart. I think at the very least memory is on the cards. (I still don't understand why I didn't encounter this in Bionic though)

Edit: I could also look at having a little box set prune to get cap down, but again Bionic was fine and cap has not changed at all. It literally happened as soon as Jammy was installed!

Edit2: The cause couldn't be something to do with ksplice could it? I've been trying to think about any possible differences and that is the only one I can think of.... but:

```
uptrack-show                                                                          
Installed updates:
[r9hrmw28] Enablement update for live patching.
[qeibbp29] Provide an interface to freeze tasks.
[5r11iivt] Denial-of-service when checking if an address is a jump label.

Effective kernel version is 5.15.0-89.99

```

I don't see anything there that could affect this.

(Cheers Oracle for the Ubuntu exclusive free live patching btw <3)

Edit3: Actually suggesting the above is really stupid. If it was a kernel patch it wouldn't come and go... I need to go to bed! :D will pick this up again tomorrow!

---

### Post by MAFoElffen on 2023-12-01
Yes, continued tomorrow. I spent a long day getting around a recent update bug with zfs-dkms. I think this last update was "evil" vs 6.2 kernels. 

Bringing up ksplice is something I didn't think about until you brought it up... It does the updates, applies it, but it all exists in memory until the next reboot, then goes as physical. (and frees up that memory)...

Dang, let me sleep on that.

---

### Post by tkae-lp on 2023-12-01
About ksplice, can't imagine that's it then, as the problem has been seen directly after a reboot.

[COLOR=#a9a9a9]I may have hit a snag in my memory master plan. 

1. That preowned memory for £80 has been snapped up
2. The manual for the board here: [/COLOR][[COLOR=#a9a9a9]https://download.asrock.com/Manual/X99%20WS.pdf[/COLOR]]("https://download.asrock.com/Manual/X99%20WS.pdf")[COLOR=#a9a9a9] on page 16 says modules have to be identical for quad channel, but doesn't say if they have to be for triple, presumably not.
3. According to the system info script, my memory is Micron 36ASF2G72PZ-2G1A2, which Micron's site gives info about here: [/COLOR][[COLOR=#a9a9a9]https://www.micron.com/products/dram-modules/rdimm/part-catalog/mta36asf2g72pz-2g1[/COLOR]]("https://www.micron.com/products/dram-modules/rdimm/part-catalog/mta36asf2g72pz-2g1")[COLOR=#a9a9a9] but all the modules for sale appear to be different: [/COLOR][[COLOR=#a9a9a9]https://uk.crucial.com/compatible-upgrade-for/asrock/x99-ws#memory?module-type(-)RDIMM[/COLOR]]("https://uk.crucial.com/compatible-upgrade-for/asrock/x99-ws#memory?module-type(-)RDIMM")[COLOR=#a9a9a9]
4. There is a list of compatible board modules here: [/COLOR][[COLOR=#a9a9a9]https://www.asrock.com/mb/Intel/X99%20WS/#Memory[/COLOR]]("https://www.asrock.com/mb/Intel/X99%20WS/#Memory")[COLOR=#a9a9a9] but there's one 32GB listed and I am not even sure if that is an RDIMM.
5. The manual doesn't specify module size limit per memory type (for example, I know some mobos that can take RDIMMs and LRDIMMs can take larger LRDIMM sizes per slot - I bet that Crucial 32GB is a UDIMM)

Looks like I could very well be limited to using the more expensive option of 2 x 16GB modules and sacrificing such a jump in memory and quad channel. Bummer :(

Edit: Actually all might not be lost - the manual says: for quad channel configuration, you always need to install identical (the same
brand, speed, size and chip-type) DDR4 _**DIMM pairs.**_

 So maybe two of these would do it: [/COLOR][[COLOR=#a9a9a9]https://www.ebay.co.uk/itm/402574671972[/COLOR]]("https://www.ebay.co.uk/itm/402574671972")[COLOR=#a9a9a9] and I can look at another 2/4 down the line. But 64GB of memory will give the array more breathing room.

Edit2: Wow.. this is a learning curve. Just read you can't mix rank configs. So ebay listing is no good as they are 2Rx8. Looks like mine are:


[/COLOR][TABLE="class: parts"]
[TR]
[TD][COLOR=#a9a9a9]
[/COLOR][/TD]
[TD][COLOR=#a9a9a9]DDR4-MODULE ORG. (PACKAGE RANKS  DEVICE WIDTH)[/COLOR][/TD]
[TD][COLOR=#a9a9a9]08[/COLOR][/TD]
[/TR]
[/TABLE]
[COLOR=#a9a9a9]
Presumably this means 1Rx8, so I would need these: [/COLOR][URL="https://uk.crucial.com/memory/server-ddr4/mta9asf2g72pz-3g2r/"][COLOR=#a9a9a9]https://uk.crucial.com/memory/server-ddr4/mta9asf2g72pz-3g2r/
[/COLOR][/URL]
Edit 3: Right, Couldn't find a strike through button so ignore everything in grey above - it was easier just to shut the machine down and take a stick out. The exact PN is: [SIZE=2]MTA36ASF2G72PZ-2G1A2IG
[/SIZE]
Note the IG at the end.I find it frustrating that Micron do not list these variant part numbers... BUT the fantastic news is I found an ebay seller with two sticks for £31, so next week I'll have 64GB of RAM. I can also find another seller that has TONS of [SIZE=2]MTA36ASF2G72PZ-2G1A2IJ (J at end)[/SIZE]

So I have emailed them to ask what the difference is between that and IG, because it turns out that this stuff is actually dirt cheap. They're selling 8 x 16GB modules for £144 or best offer! Have just ordered a 2TB NMVe for ARC and logs too. Now I just need to fix this slow down issue. In the middle of having a little box set prune as we speak.

---

### Post by #&amp;thj^% on 2023-12-01
My NMVe Drives, all have differences ie:
```
/dev/nvme0n1 vendor: Western Digital model: WD Blue SN570 500GB

```
It's a cheaper WD NMVE drive, and my speeds are much slower on write speed.
```
Run status group 0 (all jobs):
  WRITE: bw=642MiB/s (674MB/s), 642MiB/s-642MiB/s (674MB/s-674MB/s), io=10.0GiB (10.7GB), run=15942-15942msec

```
The read speed is decent, not great:
```
Run status group 0 (all jobs):
   READ: bw=2985MiB/s (3130MB/s), 2985MiB/s-2985MiB/s (3130MB/s-3130MB/s), io=10.0GiB (10.7GB), run=3431-3431msec

```
 MAFoElffen will remember when I added a SSD drive for additional swap, but, it was still very slow for my liking.
I'm waiting for a HBA card before I go crazy on tweaking my performance. (Note I'm on Noble 24.04 Testing)
I'm now looking at your link for " compatible board modules "
And My Memory are "DDR4	Crucial	2666	8GB" X2
```
Memory:
  System RAM: total: 16 GiB available: 15.46 GiB used: 7.17 GiB (46.4%)
  Array-1: capacity: 32 GiB slots: 2 modules: 2 EC: None
  Device-1: DIMM 0 type: DDR4 size: 8 GiB speed: 3200 MT/s
  Device-2: DIMM 0 type: DDR4 size: 8 GiB speed: 3200 MT/s

```

---

### Post by tkae-lp on 2023-12-01
I went against what I said yesterday and didn't totally cheap out on the NMVe. I went for the old reliable Sammy 980 Pro because I have it in my Thinkpad and it's a great unit. Should be able to max out the M.2 Ultra port (in theory). I'll post what it benches at when I get it. IIRC it disables lane 3 but there's nothing in it.

When I got the 980 Pro for my Thinkpad it was....... a LOT more... I'm  embarrassed to say how much I paid for that when it was released :redface:

That ASRock page was a PITA... why go to all that effort to list that info and not list some part numbers or DIMM types?! :roll:

---

### Post by #&amp;thj^% on 2023-12-01
Complete information regarding to hardware, will always be lacking. :(
You chose wisely. :)
Please keep us updated, it helps others like myself for one, when considering new zfs hardware

---

### Post by MAFoElffen on 2023-12-01
Strike through bbcodes are like this [noparse][s] Text[/s][/noparse]... Will show up like this: [s]Text[/s]

Yes. I remember when TheFu got his mother board (new), he shopped around and did his homework. He finally ordered a match set of two RAM sticks (at first), then months later made sure that he ordered "the same memory" from "the same vendor"... 

He was so P'ed off when his system RAM slowed down about 20-30% just by adding those additional two chips in. Sometimes that just doesn't make sense.

---

### Post by tkae-lp on 2023-12-01
> **1fallen said:**
> You chose wisely. :smile:

[IMG]https://i.ibb.co/cxgjf3J/chosewisely.jpg[/IMG]

Sorry, couldn't resist :D

> **1fallen said:**
> Please keep us updated, it helps others like myself for one, when considering new zfs hardware

Thanks, will do. :)

> **MAFoElffen said:**
> Strike through bbcodes are like this [noparse][s] Text[/s][/noparse]... Will show up like this: [s]Text[/s] Ah, ok!

> **MAFoElffen said:**
> Yes. I remember when TheFu got his mother board (new), he shopped around and did his homework. He finally ordered a match set of two RAM sticks (at first), then months later made sure that he ordered "the same memory" from "the same vendor"... 

He was so P'ed off when his system RAM slowed down about 20-30% just by adding those additional two chips in. Sometimes that just doesn't make sense.

Well... I'm no expert but just based on what I've recently learned that usually boils down to (in no real order):

1. The mobo is a poor design
2. The position of the memory was incorrect (not optimal)
3. The memory was different (different PN)
4. The memory was a different type

A friend of mine used to work for a small business that refurbed tape drives. The dodgy guy who owned it would print his own PN labels..... yup, you read that right.... he said it used to frustrate the boss that the unit was 'identical' but because the part number was 1 digit different (like a slightly older hw rev.), they would not be able to shift certain things.. so he'd remove the PN label and put their own on. Dodgy dodgy ******* business...... I never saw any of these labels, but they were doing it for years before the business folded (for an entirely different, but equally dodgy reason) so they must have been at least half convincing, I think they were quite well known as well, as a business I mean.. they did a lot of trade. I'm not saying this was the case with TheFu, but it can/does happen. For example, I'm sure that IJ memory will work just fine in my board if it's all the IJ stuff. As will all the ones listed on Crucial if it's all that PN. But the ones on Crucial for example will definitely slow my board down if I mix them, even though they work. Could even be that the label only showed the main part of the PN.. like dmidecode only showed 36ASF2G72PZ-2G1A2 but there seem to be 2 variants of this (IG and IJ) as well as a 36ASF2G72PZ-2G1**B**2.

So at the moment:

```
free -m
               total        used        free      shared  buff/cache   available
Mem:           32010        9999       13893          61        8117       21480
Swap:          12286           0       12286

```

and I get:

```
rm /mnt/Tank/testfile && dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 10.3578 s, 622 MB/s

```

and:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=484MiB/s][w=484 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][86.7%][w=525MiB/s][w=525 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=446642: Sat Dec  2 00:04:32 2023
  write: IOPS=473, BW=473MiB/s (496MB/s)(10.0GiB/21639msec); 0 zone resets
    slat (usec): min=233, max=3623, avg=1521.72, stdev=671.83
    clat (usec): min=3, max=6053.1k, avg=65226.74, stdev=329496.49
     lat (usec): min=329, max=6054.9k, avg=66749.10, stdev=329553.81
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   12], 10.00th=[   13], 20.00th=[   16],
     | 30.00th=[   50], 40.00th=[   51], 50.00th=[   55], 60.00th=[   57],
     | 70.00th=[   59], 80.00th=[   63], 90.00th=[   67], 95.00th=[   77],
     | 99.00th=[   88], 99.50th=[   94], 99.90th=[ 6007], 99.95th=[ 6074],
     | 99.99th=[ 6074]
   bw (  KiB/s): min=51200, max=2265088, per=100.00%, avg=638016.00, stdev=400354.97, samples=32
   iops        : min=   50, max= 2212, avg=623.06, stdev=390.97, samples=32
  lat (usec)   : 4=0.01%, 10=0.04%, 500=0.02%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.08%, 4=0.15%, 10=0.65%, 20=21.60%, 50=16.66%
  lat (msec)   : 100=60.46%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1353, max=1353, avg=1353.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1352],  5.00th=[ 1352], 10.00th=[ 1352], 20.00th=[ 1352],
     | 30.00th=[ 1352], 40.00th=[ 1352], 50.00th=[ 1352], 60.00th=[ 1352],
     | 70.00th=[ 1352], 80.00th=[ 1352], 90.00th=[ 1352], 95.00th=[ 1352],
     | 99.00th=[ 1352], 99.50th=[ 1352], 99.90th=[ 1352], 99.95th=[ 1352],
     | 99.99th=[ 1352]
  cpu          : usr=3.15%, sys=19.69%, ctx=75103, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=473MiB/s (496MB/s), 473MiB/s-473MiB/s (496MB/s-496MB/s), io=10.0GiB (10.7GB), run=21639-21639msec
```

and:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3020MiB/s][r=3020 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=515253: Sat Dec  2 00:05:26 2023
  read: IOPS=2920, BW=2921MiB/s (3063MB/s)(10.0GiB/3506msec)
    slat (usec): min=273, max=1151, avg=339.36, stdev=47.28
    clat (usec): min=3, max=31257, avg=10501.61, stdev=1305.05
     lat (usec): min=324, max=32409, avg=10841.35, stdev=1340.08
    clat percentiles (usec):
     |  1.00th=[ 6718],  5.00th=[10159], 10.00th=[10159], 20.00th=[10159],
     | 30.00th=[10159], 40.00th=[10290], 50.00th=[10290], 60.00th=[10290],
     | 70.00th=[10421], 80.00th=[10552], 90.00th=[12125], 95.00th=[12125],
     | 99.00th=[13698], 99.50th=[15270], 99.90th=[26346], 99.95th=[28705],
     | 99.99th=[30802]
   bw (  MiB/s): min= 2344, max= 3040, per=99.76%, avg=2913.71, stdev=252.00, samples=7
   iops        : min= 2344, max= 3040, avg=2913.71, stdev=252.00, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.02%
  lat (msec)   : 2=0.13%, 4=0.31%, 10=0.96%, 20=98.21%, 50=0.22%
  cpu          : usr=0.54%, sys=99.43%, ctx=12, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2921MiB/s (3063MB/s), 2921MiB/s-2921MiB/s (3063MB/s-3063MB/s), io=10.0GiB (10.7GB), run=3506-3506msec
```

During each job, memory usage climbs by a few gigs then drops back down again. Looks like I'm in a reasonable patch at the moment.

But again 5 mins later:

```
rm /mnt/Tank/testfile && dd if=/dev/zero of=/mnt/Tank/testfile bs=1G count=6 oflag=dsync
6+0 records in
6+0 records out
6442450944 bytes (6.4 GB, 6.0 GiB) copied, 72.1945 s, 89.2 MB/s
```

and: 

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=593MiB/s][w=593 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][72.2%][w=123MiB/s][w=123 IOPS][eta 00m:05s] 
Jobs: 1 (f=1): [W(1)][76.0%][w=31.0MiB/s][w=31 IOPS][eta 00m:06s] 
Jobs: 1 (f=1): [W(1)][75.8%][w=10.0MiB/s][w=10 IOPS][eta 00m:08s] 
Jobs: 1 (f=1): [W(1)][75.6%][w=2050KiB/s][w=2 IOPS][eta 00m:10s] 
Jobs: 1 (f=1): [W(1)][80.4%][w=133MiB/s][w=133 IOPS][eta 00m:09s]
Jobs: 1 (f=1): [W(1)][97.7%][w=148MiB/s][w=148 IOPS][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.0%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.1%][eta 00m:01s] 
TEST: (groupid=0, jobs=1): err= 0: pid=520493: Sat Dec  2 00:11:57 2023
  write: IOPS=199, BW=199MiB/s (209MB/s)(10.0GiB/51363msec); 0 zone resets
    slat (usec): min=295, max=1187.2k, avg=4112.57, stdev=17844.91
    clat (usec): min=3, max=9229.9k, avg=154951.33, stdev=640495.91
     lat (usec): min=348, max=9231.6k, avg=159064.75, stdev=647743.56
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   23], 10.00th=[   27], 20.00th=[   29],
     | 30.00th=[   49], 40.00th=[   53], 50.00th=[   54], 60.00th=[   56],
     | 70.00th=[   56], 80.00th=[   78], 90.00th=[  201], 95.00th=[  426],
     | 99.00th=[ 2265], 99.50th=[ 5000], 99.90th=[ 9194], 99.95th=[ 9194],
     | 99.99th=[ 9194]
   bw (  KiB/s): min= 2048, max=1263616, per=100.00%, avg=245982.07, stdev=305800.34, samples=83
   iops        : min=    2, max= 1234, avg=240.22, stdev=298.63, samples=83
  lat (usec)   : 4=0.02%, 10=0.02%, 20=0.01%, 500=0.01%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.06%, 4=0.09%, 10=0.63%, 20=2.89%, 50=34.20%
  lat (msec)   : 100=43.91%, 250=10.29%, 500=3.43%, 750=1.62%, 1000=0.98%
  lat (msec)   : 2000=0.74%, >=2000=1.08%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1345, max=1345, avg=1345.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1352],  5.00th=[ 1352], 10.00th=[ 1352], 20.00th=[ 1352],
     | 30.00th=[ 1352], 40.00th=[ 1352], 50.00th=[ 1352], 60.00th=[ 1352],
     | 70.00th=[ 1352], 80.00th=[ 1352], 90.00th=[ 1352], 95.00th=[ 1352],
     | 99.00th=[ 1352], 99.50th=[ 1352], 99.90th=[ 1352], 99.95th=[ 1352],
     | 99.99th=[ 1352]
  cpu          : usr=1.32%, sys=10.72%, ctx=70195, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=199MiB/s (209MB/s), 199MiB/s-199MiB/s (209MB/s-209MB/s), io=10.0GiB (10.7GB), run=51363-51363msec

```

and: 

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2833MiB/s][r=2833 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=559190: Sat Dec  2 00:13:26 2023
  read: IOPS=2754, BW=2755MiB/s (2889MB/s)(10.0GiB/3717msec)
    slat (usec): min=290, max=1156, avg=359.97, stdev=47.84
    clat (usec): min=2, max=32686, avg=11134.73, stdev=1355.69
     lat (usec): min=337, max=33843, avg=11495.11, stdev=1391.41
    clat percentiles (usec):
     |  1.00th=[ 7111],  5.00th=[10814], 10.00th=[10814], 20.00th=[10814],
     | 30.00th=[10945], 40.00th=[10945], 50.00th=[10945], 60.00th=[10945],
     | 70.00th=[10945], 80.00th=[11076], 90.00th=[12911], 95.00th=[12911],
     | 99.00th=[14091], 99.50th=[16057], 99.90th=[27919], 99.95th=[30278],
     | 99.99th=[32375]
   bw (  MiB/s): min= 2192, max= 2846, per=99.54%, avg=2742.29, stdev=242.91, samples=7
   iops        : min= 2192, max= 2846, avg=2742.29, stdev=242.91, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.83%, 20=98.33%, 50=0.25%
  cpu          : usr=1.26%, sys=98.68%, ctx=5, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2755MiB/s (2889MB/s), 2755MiB/s-2755MiB/s (2889MB/s-2889MB/s), io=10.0GiB (10.7GB), run=3717-3717msec
```

Memory usage seemed heavier this time. Used more like 5-6gigs and only dropped back down to: 

```
free -m
               total        used        free      shared  buff/cache   available
Mem:           32010       10180       13712          60        8117       21301
Swap:          12286           0       12286

```

But this does seem to solve part of the riddle... it's nothing to do with running out of memory.

---

### Post by MAFoElffen on 2023-12-01
Ready to try a test on the cheap, without spending any money yet?

This is the entries I want you to change, noted from my /etc/modprobe.d/zfs.conf file:
```

mafoelffen@Mikes-B460M:~$ grep zfs_arc_ /etc/modprobe.d/zfs.conf
# This is the default for mine, which is half the total memory (set to 67GB). Yours will be about 16GB... 
options zfs zfs_arc_max=68719476736
# The default for minimum is about 1GB
options zfs zfs_arc_min=1073741824

```
Try editing your and set to 4GB. It is in bytes, so 4x1024x10000=40960000...

Then update the intramfs image to take that change
```

sudo update-intramfs -c -k all

```
You said Samsung 980 pro right... What about 1TB? Pop that in. Give it a a GPT partition table, and 2 partitions of 512GB... Type BF07.

Do
```

ls -l /dev/disk/by-id/

```
To get the unique_diskid... then
```

#Set variable for the NVme disk's Ubique_DiskID
DISK=/dev/disk/bi-id/<unique_diskid>
## Adding L2ARC
# tank
sudo zpool add tank cache $DISK-part1
## Add single SLOG
sudo zpool add -f tank log $DISK-part2

```
After you add it in, test.

Since this is disk caches for HHD vdev's, even using an SSD would help. But yes, I use NVMe for mine also:
```

mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:18:49 with 0 errors on Tue Nov 28 12:13:28 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

```

---

### Post by tkae-lp on 2023-12-01
> **MAFoElffen said:**
> Ready to try a test on the cheap, without spending any money yet?

Yes :D I've already bought the memory and NMVe though. NMVe isn't here yet. Should be here Monday. It's the 2TB module.

> **MAFoElffen said:**
> This is the entries I want you to change, noted from my /etc/modprobe.d/zfs.conf file:
```

mafoelffen@Mikes-B460M:~$ grep zfs_arc_ /etc/modprobe.d/zfs.conf
# This is the default for mine, which is half the total memory (set to 67GB). Yours will be about 16GB... 
options zfs zfs_arc_max=68719476736
# The default for minimum is about 1GB
options zfs zfs_arc_min=1073741824

```
Try editing your and set to 4GB. It is in bytes, so 4x1024x10000=40960000...


Is zfs.conf definitely meant to always be present? Because I do not have it on my installation....

```
/etc/modprobe.d # ls zfs.conf
ls: cannot access 'zfs.conf': No such file or directory
```

Or did you mean just create it? If it's meant to always be there, we may have discovered the problem! :biggrin:

Edit: I think the memory is a worthwhile upgrade. I could cancel the NMVe, but then it'll only improve things so I'm not opposed to spending a bit on it. We'll call it my server's Christmas present, and I'll provide benchmarks for you guys :)

---

### Post by tkae-lp on 2023-12-01
If this file is indeed meant to be always present, we could knock this one on the head for future with something added to your sys info script:

```
#!/bin/bash
if [ -e /etc/modprobe.d/zfs.conf ]
then
    echo "ZFS: Modprobe conf file is present."
else
    echo "ZFS: Modprobe conf file is missing!"
fi

```

Edit: Still.. makes me wonder why on earth it's not there?! I certainly didn't remove it!

---

### Post by tkae-lp on 2023-12-01
I've got to hit the sack, it's nearly 3am. I've created the conf file with just the min and max value, updated initramfs and rebooted. I'll report back tomorrow (today!)

---

### Post by tkae-lp on 2023-12-01
Ok, so curiosity got me... it hasn't helped. Here's fio write performed again and again. Mem usage fluctuated between 7GB-9.5GB used. It degrades as each subsequent test is performed, then suddenly increases to about 505MB/s again :-S

Really hitting the sack now. Until tomorrow....

```
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=485MiB/s][w=485 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][81.2%][w=565MiB/s][w=565 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=218196: Sat Dec  2 03:39:44 2023
  write: IOPS=518, BW=519MiB/s (544MB/s)(10.0GiB/19739msec); 0 zone resets
    slat (usec): min=223, max=5441, avg=1577.67, stdev=657.74
    clat (usec): min=3, max=3579.9k, avg=59445.30, stdev=193945.51
     lat (usec): min=325, max=3581.7k, avg=61023.68, stdev=194025.35
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   14], 20.00th=[   22],
     | 30.00th=[   50], 40.00th=[   51], 50.00th=[   56], 60.00th=[   57],
     | 70.00th=[   59], 80.00th=[   64], 90.00th=[   70], 95.00th=[   78],
     | 99.00th=[   88], 99.50th=[  101], 99.90th=[ 3574], 99.95th=[ 3574],
     | 99.99th=[ 3574]
   bw (  KiB/s): min=131072, max=2045952, per=100.00%, avg=618682.18, stdev=346402.86, samples=33
   iops        : min=  128, max= 1998, avg=604.18, stdev=338.28, samples=33
  lat (usec)   : 4=0.02%, 10=0.02%, 20=0.01%, 500=0.02%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.07%, 4=0.15%, 10=0.46%, 20=18.67%, 50=18.09%
  lat (msec)   : 100=61.96%, 250=0.21%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1326, max=1326, avg=1326.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1320],  5.00th=[ 1320], 10.00th=[ 1320], 20.00th=[ 1320],
     | 30.00th=[ 1320], 40.00th=[ 1320], 50.00th=[ 1320], 60.00th=[ 1320],
     | 70.00th=[ 1320], 80.00th=[ 1320], 90.00th=[ 1320], 95.00th=[ 1320],
     | 99.00th=[ 1320], 99.50th=[ 1320], 99.90th=[ 1320], 99.95th=[ 1320],
     | 99.99th=[ 1320]
  cpu          : usr=3.83%, sys=20.61%, ctx=68366, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=519MiB/s (544MB/s), 519MiB/s-519MiB/s (544MB/s-544MB/s), io=10.0GiB (10.7GB), run=19739-19739msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=422MiB/s][w=422 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][76.5%][w=237MiB/s][w=237 IOPS][eta 00m:04s] 
Jobs: 1 (f=1): [W(1)][95.0%][w=479MiB/s][w=479 IOPS][eta 00m:01s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                         
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=282657: Sat Dec  2 03:40:25 2023
  write: IOPS=389, BW=389MiB/s (408MB/s)(10.0GiB/26298msec); 0 zone resets
    slat (usec): min=235, max=2469.9k, avg=1863.58, stdev=28206.96
    clat (usec): min=3, max=7211.0k, avg=79337.13, stdev=422662.74
     lat (usec): min=286, max=7212.5k, avg=81201.28, stdev=423608.56
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   12], 10.00th=[   13], 20.00th=[   15],
     | 30.00th=[   28], 40.00th=[   50], 50.00th=[   52], 60.00th=[   55],
     | 70.00th=[   59], 80.00th=[   68], 90.00th=[   79], 95.00th=[   85],
     | 99.00th=[   95], 99.50th=[ 2500], 99.90th=[ 7215], 99.95th=[ 7215],
     | 99.99th=[ 7215]
   bw (  KiB/s): min=51200, max=2254848, per=100.00%, avg=618546.73, stdev=427097.25, samples=33
   iops        : min=   50, max= 2202, avg=604.03, stdev=417.09, samples=33
  lat (usec)   : 4=0.03%, 10=0.02%, 500=0.02%, 750=0.01%, 1000=0.02%
  lat (msec)   : 2=0.08%, 4=0.15%, 10=0.51%, 20=26.19%, 50=18.09%
  lat (msec)   : 100=53.98%, 2000=0.30%, >=2000=0.61%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1210, max=1210, avg=1210.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1208],  5.00th=[ 1208], 10.00th=[ 1208], 20.00th=[ 1208],
     | 30.00th=[ 1208], 40.00th=[ 1208], 50.00th=[ 1208], 60.00th=[ 1208],
     | 70.00th=[ 1208], 80.00th=[ 1208], 90.00th=[ 1208], 95.00th=[ 1208],
     | 99.00th=[ 1208], 99.50th=[ 1208], 99.90th=[ 1208], 99.95th=[ 1208],
     | 99.99th=[ 1208]
  cpu          : usr=2.10%, sys=16.31%, ctx=60150, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=389MiB/s (408MB/s), 389MiB/s-389MiB/s (408MB/s-408MB/s), io=10.0GiB (10.7GB), run=26298-26298msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][58.3%][w=573MiB/s][w=573 IOPS][eta 00m:05s]
Jobs: 1 (f=1): [W(1)][81.2%][eta 00m:03s]                         
Jobs: 1 (f=1): [W(1)][90.5%][eta 00m:02s]                         
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                         
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=386756: Sat Dec  2 03:41:04 2023
  write: IOPS=362, BW=362MiB/s (380MB/s)(10.0GiB/28270msec); 0 zone resets
    slat (usec): min=209, max=3544.7k, avg=1909.22, stdev=37972.15
    clat (usec): min=3, max=8709.7k, avg=85298.83, stdev=519900.81
     lat (usec): min=298, max=8710.8k, avg=87208.59, stdev=521282.88
    clat percentiles (msec):
     |  1.00th=[   10],  5.00th=[   12], 10.00th=[   12], 20.00th=[   14],
     | 30.00th=[   20], 40.00th=[   49], 50.00th=[   52], 60.00th=[   56],
     | 70.00th=[   60], 80.00th=[   63], 90.00th=[   71], 95.00th=[   77],
     | 99.00th=[   89], 99.50th=[ 3574], 99.90th=[ 8658], 99.95th=[ 8658],
     | 99.99th=[ 8658]
   bw (  KiB/s): min=12288, max=2347008, per=100.00%, avg=638016.00, stdev=482903.71, samples=32
   iops        : min=   12, max= 2292, avg=623.06, stdev=471.59, samples=32
  lat (usec)   : 4=0.03%, 10=0.02%, 500=0.02%, 750=0.01%, 1000=0.02%
  lat (msec)   : 2=0.07%, 4=0.12%, 10=0.76%, 20=29.00%, 50=14.66%
  lat (msec)   : 100=54.38%, 2000=0.30%, >=2000=0.61%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1240, max=1240, avg=1240.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1240],  5.00th=[ 1240], 10.00th=[ 1240], 20.00th=[ 1240],
     | 30.00th=[ 1240], 40.00th=[ 1240], 50.00th=[ 1240], 60.00th=[ 1240],
     | 70.00th=[ 1240], 80.00th=[ 1240], 90.00th=[ 1240], 95.00th=[ 1240],
     | 99.00th=[ 1240], 99.50th=[ 1240], 99.90th=[ 1240], 99.95th=[ 1240],
     | 99.99th=[ 1240]
  cpu          : usr=2.14%, sys=14.95%, ctx=58856, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=362MiB/s (380MB/s), 362MiB/s-362MiB/s (380MB/s-380MB/s), io=10.0GiB (10.7GB), run=28270-28270msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][38.9%][w=310MiB/s][w=310 IOPS][eta 00m:11s]
Jobs: 1 (f=1): [W(1)][65.0%][w=409MiB/s][w=409 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [W(1)][95.0%][w=497MiB/s][w=497 IOPS][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                         
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=221MiB/s][w=221 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=493848: Sat Dec  2 03:41:39 2023
  write: IOPS=321, BW=321MiB/s (337MB/s)(10.0GiB/31858msec); 0 zone resets
    slat (usec): min=240, max=6105, avg=1925.09, stdev=995.47
    clat (usec): min=4, max=12154k, avg=96014.61, stdev=663816.93
     lat (usec): min=378, max=12156k, avg=97940.44, stdev=663882.41
    clat percentiles (msec):
     |  1.00th=[   10],  5.00th=[   11], 10.00th=[   19], 20.00th=[   31],
     | 30.00th=[   51], 40.00th=[   52], 50.00th=[   57], 60.00th=[   61],
     | 70.00th=[   68], 80.00th=[   79], 90.00th=[  101], 95.00th=[  117],
     | 99.00th=[  174], 99.50th=[  178], 99.90th=[12147], 99.95th=[12147],
     | 99.99th=[12147]
   bw (  KiB/s): min=126976, max=2115584, per=100.00%, avg=510384.47, stdev=320831.75, samples=40
   iops        : min=  124, max= 2066, avg=498.40, stdev=313.31, samples=40
  lat (usec)   : 10=0.05%, 500=0.01%, 1000=0.01%
  lat (msec)   : 2=0.06%, 4=0.09%, 10=4.80%, 20=5.86%, 50=18.38%
  lat (msec)   : 100=60.69%, 250=9.75%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1304, max=1304, avg=1304.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1304],  5.00th=[ 1304], 10.00th=[ 1304], 20.00th=[ 1304],
     | 30.00th=[ 1304], 40.00th=[ 1304], 50.00th=[ 1304], 60.00th=[ 1304],
     | 70.00th=[ 1304], 80.00th=[ 1304], 90.00th=[ 1304], 95.00th=[ 1304],
     | 99.00th=[ 1304], 99.50th=[ 1304], 99.90th=[ 1304], 99.95th=[ 1304],
     | 99.99th=[ 1304]
  cpu          : usr=1.69%, sys=16.58%, ctx=70160, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=321MiB/s (337MB/s), 321MiB/s-321MiB/s (337MB/s-337MB/s), io=10.0GiB (10.7GB), run=31858-31858msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=425MiB/s][w=425 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][81.2%][w=313MiB/s][w=313 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][90.5%][w=119MiB/s][w=119 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=112MiB/s][w=112 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=578729: Sat Dec  2 03:42:19 2023
  write: IOPS=277, BW=278MiB/s (291MB/s)(10.0GiB/36890msec); 0 zone resets
    slat (usec): min=273, max=22967, avg=2274.51, stdev=2123.06
    clat (usec): min=3, max=13585k, avg=111322.53, stdev=744421.43
     lat (usec): min=333, max=13587k, avg=113597.80, stdev=744580.40
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   14], 20.00th=[   17],
     | 30.00th=[   50], 40.00th=[   54], 50.00th=[   56], 60.00th=[   58],
     | 70.00th=[   66], 80.00th=[   75], 90.00th=[  174], 95.00th=[  243],
     | 99.00th=[  321], 99.50th=[  330], 99.90th=[13624], 99.95th=[13624],
     | 99.99th=[13624]
   bw (  KiB/s): min=96256, max=2224128, per=100.00%, avg=434393.87, stdev=425821.34, samples=47
   iops        : min=   94, max= 2172, avg=424.21, stdev=415.84, samples=47
  lat (usec)   : 4=0.01%, 10=0.04%, 500=0.01%, 750=0.02%
  lat (msec)   : 2=0.07%, 4=0.12%, 10=0.35%, 20=23.37%, 50=7.84%
  lat (msec)   : 100=52.45%, 250=11.36%, 500=4.06%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1621, max=1621, avg=1621.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1624],  5.00th=[ 1624], 10.00th=[ 1624], 20.00th=[ 1624],
     | 30.00th=[ 1624], 40.00th=[ 1624], 50.00th=[ 1624], 60.00th=[ 1624],
     | 70.00th=[ 1624], 80.00th=[ 1624], 90.00th=[ 1624], 95.00th=[ 1624],
     | 99.00th=[ 1624], 99.50th=[ 1624], 99.90th=[ 1624], 99.95th=[ 1624],
     | 99.99th=[ 1624]
  cpu          : usr=1.62%, sys=14.02%, ctx=79482, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=278MiB/s (291MB/s), 278MiB/s-278MiB/s (291MB/s-291MB/s), io=10.0GiB (10.7GB), run=36890-36890msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=166MiB/s][w=166 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][54.2%][w=50.0MiB/s][w=50 IOPS][eta 00m:11s] 
Jobs: 1 (f=1): [W(1)][63.3%][w=303MiB/s][w=303 IOPS][eta 00m:11s] 
Jobs: 1 (f=1): [W(1)][89.3%][w=493MiB/s][w=493 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][97.7%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.0%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.2%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][98.5%][eta 00m:01s] 
Jobs: 1 (f=1): [W(1)][98.6%][eta 00m:01s] 
TEST: (groupid=0, jobs=1): err= 0: pid=654785: Sat Dec  2 03:43:30 2023
  write: IOPS=146, BW=147MiB/s (154MB/s)(9.77GiB/68196msec); 0 zone resets
    slat (usec): min=278, max=33423, avg=2604.53, stdev=3357.37
    clat (usec): min=3, max=42142k, avg=211033.60, stdev=2339285.11
     lat (usec): min=670, max=42144k, avg=213638.72, stdev=2339378.36
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   13], 10.00th=[   14], 20.00th=[   21],
     | 30.00th=[   50], 40.00th=[   51], 50.00th=[   53], 60.00th=[   61],
     | 70.00th=[   65], 80.00th=[   89], 90.00th=[  153], 95.00th=[  279],
     | 99.00th=[  667], 99.50th=[  760], 99.90th=[17113], 99.95th=[17113],
     | 99.99th=[17113]
   bw (  KiB/s): min=40960, max=2269184, per=100.00%, avg=385217.21, stdev=411038.22, samples=53
   iops        : min=   40, max= 2216, avg=376.19, stdev=401.40, samples=53
  lat (usec)   : 4=0.01%, 10=0.02%, 20=0.01%, 750=0.01%
  lat (msec)   : 2=0.03%, 4=0.06%, 10=0.19%, 20=19.65%, 50=22.10%
  lat (msec)   : 100=40.69%, 250=11.16%, 500=3.97%, 750=1.55%, 1000=0.24%
  lat (msec)   : >=2000=0.31%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=2011, max=2011, avg=2011.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 2008],  5.00th=[ 2008], 10.00th=[ 2008], 20.00th=[ 2008],
     | 30.00th=[ 2008], 40.00th=[ 2008], 50.00th=[ 2008], 60.00th=[ 2008],
     | 70.00th=[ 2008], 80.00th=[ 2008], 90.00th=[ 2008], 95.00th=[ 2008],
     | 99.00th=[ 2008], 99.50th=[ 2008], 99.90th=[ 2008], 99.95th=[ 2008],
     | 99.99th=[ 2008]
  cpu          : usr=0.85%, sys=6.88%, ctx=79480, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10000,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=147MiB/s (154MB/s), 147MiB/s-147MiB/s (154MB/s-154MB/s), io=9.77GiB (10.5GB), run=68196-68196msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=254MiB/s][w=254 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][76.5%][w=562MiB/s][w=561 IOPS][eta 00m:04s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=260MiB/s][w=260 IOPS][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=742479: Sat Dec  2 03:43:55 2023
  write: IOPS=481, BW=482MiB/s (505MB/s)(10.0GiB/21261msec); 0 zone resets
    slat (usec): min=263, max=27187, avg=1687.74, stdev=993.41
    clat (usec): min=4, max=3965.2k, avg=64055.65, stdev=215970.10
     lat (usec): min=346, max=3966.7k, avg=65744.08, stdev=216092.80
    clat percentiles (msec):
     |  1.00th=[   10],  5.00th=[   11], 10.00th=[   12], 20.00th=[   16],
     | 30.00th=[   47], 40.00th=[   54], 50.00th=[   57], 60.00th=[   59],
     | 70.00th=[   65], 80.00th=[   69], 90.00th=[   80], 95.00th=[  109],
     | 99.00th=[  146], 99.50th=[  153], 99.90th=[ 3943], 99.95th=[ 3943],
     | 99.99th=[ 3977]
   bw (  KiB/s): min=233472, max=2215936, per=100.00%, avg=583203.51, stdev=433588.73, samples=35
   iops        : min=  228, max= 2164, avg=569.51, stdev=423.43, samples=35
  lat (usec)   : 10=0.05%, 500=0.02%, 750=0.01%, 1000=0.02%
  lat (msec)   : 2=0.06%, 4=0.13%, 10=1.00%, 20=24.64%, 50=8.89%
  lat (msec)   : 100=59.00%, 250=5.89%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1371, max=1371, avg=1371.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1368],  5.00th=[ 1368], 10.00th=[ 1368], 20.00th=[ 1368],
     | 30.00th=[ 1368], 40.00th=[ 1368], 50.00th=[ 1368], 60.00th=[ 1368],
     | 70.00th=[ 1368], 80.00th=[ 1368], 90.00th=[ 1368], 95.00th=[ 1368],
     | 99.00th=[ 1368], 99.50th=[ 1368], 99.90th=[ 1368], 99.95th=[ 1368],
     | 99.99th=[ 1368]
  cpu          : usr=2.66%, sys=21.11%, ctx=66517, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=482MiB/s (505MB/s), 482MiB/s-482MiB/s (505MB/s-505MB/s), io=10.0GiB (10.7GB), run=21261-21261msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=400MiB/s][w=400 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][81.2%][w=442MiB/s][w=442 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=126MiB/s][w=126 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=803014: Sat Dec  2 03:44:38 2023
  write: IOPS=380, BW=381MiB/s (399MB/s)(10.0GiB/26884msec); 0 zone resets
    slat (usec): min=243, max=3653, avg=1620.77, stdev=745.03
    clat (usec): min=3, max=10294k, avg=81065.23, stdev=561997.91
     lat (usec): min=350, max=10295k, avg=82686.66, stdev=562052.66
    clat percentiles (msec):
     |  1.00th=[   11],  5.00th=[   12], 10.00th=[   13], 20.00th=[   16],
     | 30.00th=[   50], 40.00th=[   55], 50.00th=[   57], 60.00th=[   59],
     | 70.00th=[   65], 80.00th=[   69], 90.00th=[   74], 95.00th=[   82],
     | 99.00th=[   95], 99.50th=[  100], 99.90th=[10268], 99.95th=[10268],
     | 99.99th=[10268]
   bw (  KiB/s): min=40960, max=2252800, per=100.00%, avg=600485.65, stdev=402828.38, samples=34
   iops        : min=   40, max= 2200, avg=586.41, stdev=393.39, samples=34
  lat (usec)   : 4=0.02%, 10=0.03%, 500=0.02%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.06%, 4=0.14%, 10=0.66%, 20=21.55%, 50=8.54%
  lat (msec)   : 100=68.49%, 250=0.17%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1287, max=1287, avg=1287.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1288],  5.00th=[ 1288], 10.00th=[ 1288], 20.00th=[ 1288],
     | 30.00th=[ 1288], 40.00th=[ 1288], 50.00th=[ 1288], 60.00th=[ 1288],
     | 70.00th=[ 1288], 80.00th=[ 1288], 90.00th=[ 1288], 95.00th=[ 1288],
     | 99.00th=[ 1288], 99.50th=[ 1288], 99.90th=[ 1288], 99.95th=[ 1288],
     | 99.99th=[ 1288]
  cpu          : usr=2.48%, sys=16.26%, ctx=64841, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=381MiB/s (399MB/s), 381MiB/s-381MiB/s (399MB/s-399MB/s), io=10.0GiB (10.7GB), run=26884-26884msec
--------------------------------------------------------------------------------
/mnt/Tank #   

```

---

### Post by MAFoElffen on 2023-12-01
> **tkae-lp said:**
> If this file is indeed meant to be always present, we could knock this one on the head [COLOR=#ff0000]for future with something added to your sys info script:[/COLOR]

```
#!/bin/bash
if [ -e /etc/modprobe.d/zfs.conf ]
then
    echo "ZFS: Modprobe conf file is present."
else
    echo "ZFS: Modprobe conf file is missing!"
fi

```
Edit: Still.. makes me wonder why on earth it's not there?! I certainly didn't remove it!
It isn't there by default unless you add it to make adjustments to ARC... Or other adjustment to the kernel 'zfs' module. Here is mine:
```

mafoelffen@Mikes-B460M:~$ grep . /etc/modprobe.d/zfs.conf
# ARC tuning
# Setting up ZFS ARC size on Ubuntu as per my needs
# Balanced with my system needs for KVM
# Set Max ARC size => 32GB == 34359738368 Bytes
# Set Max ARC size => 64GB == 68719476736 Bytes
options zfs zfs_arc_max=68719476736
 
# Set Min ARC size => 2GB == 2147483648 Bytes
options zfs zfs_arc_min=1073741824

```
I remember it from OpenSolaric & Solaris, pre- Oracle.
RE: [https://docs.oracle.com/cd/E26505_01/html/E37386/chapterzfs-3.html](https://docs.oracle.com/cd/E26505_01/html/E37386/chapterzfs-3.html)
Yes, I've been around awhile. If you read through the old doc's, It says it could possibly take **all the available memory**, and you should cap it at 80%... When you talk to the FreeBSM people, they think it stops at 50%, LOL. You saw that with those commands that I gave you to drop the caches, showed you just how much memory it can chew up. (And how much can be freed up.)

Back in 2005, memory was more costly and had smaller limits. So we "had" to make adjustments, that was sometimes like a balancing act. The old Solaris Administrator Docs still have a lot of information. (1fallen tells me they make his head swim. LOL) So do the docs at OpenZFS: [https://openzfs.github.io/openzfs-docs/man/index.html](https://openzfs.github.io/openzfs-docs/man/index.html)

Then I came across it again with this: [https://www.cyberciti.biz/faq/how-to-set-up-zfs-arc-size-on-ubuntu-debian-linux/](https://www.cyberciti.biz/faq/how-to-set-up-zfs-arc-size-on-ubuntu-debian-linux/)

L2ARC (2nd Level Adaptive Replacement Cache), is a hardware read cache... Which adding that increases your read cache, while reducing the need to have it all in memory. So you can use less RAM. RE: [https://docs.oracle.com/cd/E27998_01/html/E48490/analytics__statistics__cache_l2arc_accesses.html](https://docs.oracle.com/cd/E27998_01/html/E48490/analytics__statistics__cache_l2arc_accesses.html)

Going to add it in tomorrow to the script tomorrow... But differently. If it exists, print out the values. With a note, to remind people that if it exits, if they change the size of their RAM, to reevaluate their ARC settings... ARC is a read cache. Sort of like the Intel RST was about (but failed). I thik about 512GB is a good for those. At least in our tests.

SLOG is the write cache. Most people say that a hardware SLOG should be about 10-16GB, and not over... No one seemed to know why that number, or what would happen if it got bigger. Some say that if it is bigger, that ZFS does not and will not use it. So, I ignored that it our benchmarks to see what happens... Sometimes I have to see things for myself to confirm that. Go big or go broke right? LOL. The performance kept climbing until about 1TB. It definitely can use over 16GB's and be happy with it. If I made SLOG bigger than 1TG though, then the performance started dropping off again. So 1TB was the sweet spot in our tests.

---

### Post by tkae-lp on 2023-12-02
> **MAFoElffen said:**
> It isn't there by default unless you add it to make adjustments to ARC... Or other adjustment to the kernel 'zfs' module. 

Gotcha, makes sense! Would have been good if that was the solution, but never mind :)

> **MAFoElffen said:**
> 
I remember it from OpenSolaric & Solaris, pre- Oracle.
RE: [https://docs.oracle.com/cd/E26505_01/html/E37386/chapterzfs-3.html](https://docs.oracle.com/cd/E26505_01/html/E37386/chapterzfs-3.html)
Yes, I've been around awhile. If you read through the old doc's, It says it could possibly take **all the available memory**, and you should cap it at 80%... 

I only had a brief flicker with OpenSolaris because someone had mentioned ZFS and it intrigued me, but I had only in the recent months played with YellowDog and Ximian Gnome (IIRC, could be wrong about that) but I was a total nix noob so it was very alien to me. I ended up back with Win. To be fair, I still use Windows, I just love my Ubuntu servers :) I started using Debian probably about the time of the first RasPi (that might have literally been because of the Pi), then moved to Open Media Vault on a different ARM box, but wanted more power and better storage, so ZFS and Xeons came into play. Then after a time because Canonical make it SO DAMN EASY (Thanks guys!) to use ZFS, it became the no brainer. I never have to worry about jumping a kernel version and backports not having caught up. Love it.

> **MAFoElffen said:**
> 
When you talk to the FreeBSM people, they think it stops at 50%, LOL. You saw that with those commands that I gave you to drop the caches, showed you just how much memory it can chew up. (And how much can be freed up.

Well, no disrespect to different communities but I toyed with FreeNAS/TrueNAS for a time when looking at ZFS, and I read some very bizarre things on those forums. I don't remember which forum it was, but one subject that always perplexed me was around the use of ECC. Was it essential or even needed? There were obviously louder voices than others, but I'm not entirely sure that all the advice was totally sound :-s I think it boiled down to confusion between: Will it run without it? vs But should you? I just felt a company that sold products that use that sort of tech shouldn't really be saying it's ok not to use ECC, even if it does work without it (albeit with less benefits). I certainly haven't come across anyone in a production setting use it without <--- this could be a political firestorm ;D

> **MAFoElffen said:**
> Back in 2005, memory was more costly and had smaller limits. So we "had" to make adjustments, that was sometimes like a balancing act. The old Solaris Administrator Docs still have a lot of information. (1fallen tells me they make his head swim. LOL) So do the docs at OpenZFS: [https://openzfs.github.io/openzfs-docs/man/index.html](https://openzfs.github.io/openzfs-docs/man/index.html) Mine too, since you mention it, hence going back to Windows. I haven't looked much at OpenZFS but I don't care too much for Oracle's docs either - probably because they're copy/pasted from Solaris. I actually find a quick Google and some well know tutorial blog way more informative! Such as the below link.

> **MAFoElffen said:**
> 
Then I came across it again with this: [https://www.cyberciti.biz/faq/how-to-set-up-zfs-arc-size-on-ubuntu-debian-linux/](https://www.cyberciti.biz/faq/how-to-set-up-zfs-arc-size-on-ubuntu-debian-linux/)

L2ARC (2nd Level Adaptive Replacement Cache), is a hardware read cache... Which adding that increases your read cache, while reducing the need to have it all in memory. So you can use less RAM. RE: [https://docs.oracle.com/cd/E27998_01/html/E48490/analytics__statistics__cache_l2arc_accesses.html](https://docs.oracle.com/cd/E27998_01/html/E48490/analytics__statistics__cache_l2arc_accesses.html)

I found that article very interesting. I have been playing with ARC size this morning and I am currently trialing 16GB as per your setup (half RAM). So far it seems quite good. No buffering watching movies yet! I thought it was originally 16GB anyway? But then I noticed something:

```
arcstat
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
05:10:50     0     0      0     0    0     0    0     0    0  6.7G  6.7G    12G

```

I may have messed up my bytes calculation though, I thought I had done 16GB or maybe I've worked out 16GiB.... so it's actually 12GB

```
options zfs zfs_arc_min=1073741824
options zfs zfs_arc_max=7179869184

```

Regardless, this does seem better.

> **MAFoElffen said:**
> 
Going to add it in tomorrow to the script tomorrow... But differently. If it exists, print out the values. With a note, to remind people that if it exits, if they change the size of their RAM, to reevaluate their ARC settings... ARC is a read cache. Sort of like the Intel RST was about (but failed).

Nice one :)

> **MAFoElffen said:**
> 
 I thik about 512GB is a good for those. At least in our tests.

SLOG is the write cache. Most people say that a hardware SLOG should be about 10-16GB, and not over... No one seemed to know why that number, or what would happen if it got bigger. Some say that if it is bigger, that ZFS does not and will not use it. So, I ignored that it our benchmarks to see what happens... Sometimes I have to see things for myself to confirm that. Go big or go broke right? LOL. The performance kept climbing until about 1TB. It definitely can use over 16GB's and be happy with it. If I made SLOG bigger than 1TG though, then the performance started dropping off again. So 1TB was the sweet spot in our tests.

Do you think I've overshot it a bit getting the 2TB then? To be fair the  1TB wasn't much cheaper - but it hasn't dispatched yet, so I can change  the order. But if you think the 2TB is beneficial I will keep it. The other option is ... I do also have a 1TB in a tiny enclosure I carry with my laptop. It would be minimal effort to copy contents to the 2TB that's coming and I could use that.

So what are your thoughts at this point? Why has this happened? Do we still not know or is it that I probably should have had L2ARC and SLOGs on an NMVe from day 1 and I just 'somehow' never noticed a problem in Bionic? I'm totally perplexed how I've never had a problem until now. If each drive is rated at 180MB/sec, isn't that sufficient? This is what I don't understand! I have no doubt that the NMVe will improve things, but if there's still an underlying issue there it'd be great to know. It would be a huge PITA, but I had considered just throwing Bionic on a spare SSD and seeing if the problems disappeared.

---

### Post by MAFoElffen on 2023-12-02
This is what I would do... Like I instructed, allocate 2 partitions. 512GB to 1TB for L2ARC cache, 1TB for SLOG. The thing is since one is read, and the other write, and it is SSD tech, they do pretty well, even though on the same physical disk.

I don't always allocate all my storage. Since mine is almost all ZFS pools (or if you had LVM somewhere there), then having extra, is always there for an emergency where you are tight on space. You could then add wherever you needed it. Or just a partition to use to rsync to for things...

About the highest I would suspect with your being HDD is 550 GB/s to 750 GB/s. I think I remember getting my old workstation up to 850GB/s with HDD pool and NVMe disk caches.

---

### Post by tkae-lp on 2023-12-02
Brilliant, thanks. The NMVe arrives Monday and I do have some free time that day so we shall see soon enough what magic that creates ;) I'll probably just split it 50/50 between L2ARC and SLOG. This machine backs up any important stuff that's not the array (basically docker config) to a Microserver, so I can't actually think I would use any spare space in that 2TB.

I've also heard back from the seller with about 700 of those [SIZE=2]MTA36ASF2G72PZ-2G1A2I**J**[/SIZE] modules and they are telling me that they are compatible with the [SIZE=2]MTA36ASF2G72PZ-2G1A2I**G**[/SIZE] modules, they say they are the same and it's just a part number (reminds me of what my friend said about his dodgy boss!). This is great, because I could max out the board for another £72 and have the full 128GB of memory. We'll see what the CC balance looks like when the Christmas shopping is finished! 8-[

---

### Post by tkae-lp on 2023-12-02
I got an itchy trigger finger and offered £60 for 4 of the [SIZE=2]MTA36ASF2G72PZ-2G1A2I**J**'s and they accepted. [/SIZE]\\:D/

So at some point next week I'll be maxed out on RAM and have the NMVe. If that doesn't do it....! 

I know I said I wasn't going to but, wth. I'll just have to get my bum in gear and get some stuff on Gumtree! ;) I've spent £230 on a server that hasn't had anything spent on it for over 5 years.

---

### Post by MAFoElffen on 2023-12-02
Yes. 2 days.

I think your calc on your max is off. Isn't 16GiB = 16000000000 bytes? I think you only set it to around 7GB...

---

### Post by tkae-lp on 2023-12-02
> **MAFoElffen said:**
> Yes. 2 days.

I'm not patient once I've hit the button on something ;) for the NMVe 2 days yes, but the RAM is two different eBay sellers not Amazon so I'm at the mercy of their dispatch attentiveness and Royal Mail.

> **MAFoElffen said:**
> I think your calc on your max is off. Isn't 16GiB = 16000000000 bytes? I think you only set it to around 7GB...

:lolflag: you're absolutely right, good spot! I was reading something about it in a blog and it listed the values for various configs. So this morning when I set 16GB (or thought I was) I was referring to:

```
16GB=17179869184, 8GB=8589934592, 4GB=4294967296, 2GB=2147483648, 1GB=1073741824
```

And as you have noticed:

```
options zfs zfs_arc_min=1073741824
options zfs zfs_arc_max=7179869184

```

I missed the leading 1 when I copy/pasted! :redface:

Corrected now!

```
options zfs zfs_arc_min=1073741824
options zfs zfs_arc_max=17179869184

```

I did wonder why memory usage was lower than usual. Specifying even 7179869184 has given me the best day I've had in weeks though, so we're heading in the right direction :D

---

### Post by #&amp;thj^% on 2023-12-02
Ok lets talk Drive's again....:D
```
Run status group 0 (all jobs):
  WRITE: bw=2318MiB/s (2431MB/s), 2318MiB/s-2318MiB/s (2431MB/s-2431MB/s), io=10.0GiB (10.7GB), run=4417-4417msec

```
Big Difference ;)
```
Drives:
  Local Storage: total: raw: 5.06 TiB usable: 5.02 TiB used: 13.84 GiB (0.3%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 980 PRO 1TB size: 931.51 GiB

```
I hope yours has a satisfactory ending.as well.

---

### Post by tkae-lp on 2023-12-02
> **1fallen said:**
> Ok lets talk Drive's again....:D

Sorry you may have mentioned this a way back in the thread, but what are your other drives? You mentioned the WD blue for L2ARC and SLOGs, are your others SSDs or HDDs? [s]Just wondering how you're getting that result[/s] Edit: LOL, thought this was your array performance. Having re-read this morning, I've just realised it's the NMVe bench, which you did post a while back. I get sleep issues so am often up to the early hours - but probably not the best time to be looking at numbers :)

Gotta turn in, it's past 3am. Will pick up again tomorrow.

Edit2: As soon as mine is here I will share the results!

---

### Post by tkae-lp on 2023-12-03
It arrived early ;) it's not all rainbows and sunshine though :(

So NVMe is in:

```
zpool status
  pool: Tank
 state: ONLINE
  scan: scrub repaired 0B in 10:00:01 with 0 errors on Mon Nov 13 23:01:24 2023
config:

    NAME                                                                STATE     READ WRITE CKSUM
    Tank                                                                ONLINE       0     0     0
      raidz2-0                                                          ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W53XXXX-part2  ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W53XXXX-part1  ONLINE       0     0     0

errors: No known data errors
```

But there still seems to be quite a lot of fluctuation, and perofrmance is not as good as I would have expected..... Movies are snappier though:

```
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][35.0%][w=498MiB/s][w=498 IOPS][eta 00m:13s]
Jobs: 1 (f=1): [W(1)][65.0%][w=345MiB/s][w=345 IOPS][eta 00m:07s] 
Jobs: 1 (f=1): [W(1)][79.2%][w=492MiB/s][w=492 IOPS][eta 00m:05s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
Jobs: 1 (f=0): [f(1)][100.0%][w=271MiB/s][w=271 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=266993: Mon Dec  4 02:49:09 2023
  write: IOPS=397, BW=397MiB/s (416MB/s)(10.0GiB/25784msec); 0 zone resets
    slat (usec): min=248, max=17985, avg=2188.59, stdev=1462.81
    clat (usec): min=4, max=3376.2k, avg=77616.88, stdev=187185.64
     lat (usec): min=1640, max=3377.8k, avg=79806.00, stdev=187507.94
    clat percentiles (msec):
     |  1.00th=[   10],  5.00th=[   15], 10.00th=[   18], 20.00th=[   48],
     | 30.00th=[   49], 40.00th=[   52], 50.00th=[   52], 60.00th=[   56],
     | 70.00th=[   72], 80.00th=[   96], 90.00th=[  136], 95.00th=[  169],
     | 99.00th=[  220], 99.50th=[  236], 99.90th=[ 3373], 99.95th=[ 3373],
     | 99.99th=[ 3373]
   bw (  KiB/s): min=137216, max=2140160, per=100.00%, avg=460390.40, stdev=350853.49, samples=45
   iops        : min=  134, max= 2090, avg=449.60, stdev=342.63, samples=45
  lat (usec)   : 10=0.05%
  lat (msec)   : 2=0.02%, 4=0.05%, 10=3.47%, 20=12.74%, 50=18.92%
  lat (msec)   : 100=45.32%, 250=19.13%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1080, max=1080, avg=1080.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1080],  5.00th=[ 1080], 10.00th=[ 1080], 20.00th=[ 1080],
     | 30.00th=[ 1080], 40.00th=[ 1080], 50.00th=[ 1080], 60.00th=[ 1080],
     | 70.00th=[ 1080], 80.00th=[ 1080], 90.00th=[ 1080], 95.00th=[ 1080],
     | 99.00th=[ 1080], 99.50th=[ 1080], 99.90th=[ 1080], 99.95th=[ 1080],
     | 99.99th=[ 1080]
  cpu          : usr=2.18%, sys=26.02%, ctx=71826, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=397MiB/s (416MB/s), 397MiB/s-397MiB/s (416MB/s-416MB/s), io=10.0GiB (10.7GB), run=25784-25784msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][-.-%][r=3937MiB/s][r=3936 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=307629: Mon Dec  4 02:49:30 2023
  read: IOPS=3826, BW=3827MiB/s (4012MB/s)(10.0GiB/2676msec)
    slat (usec): min=174, max=1009, avg=258.50, stdev=145.75
    clat (usec): min=2, max=26948, avg=7982.63, stdev=4280.07
     lat (usec): min=181, max=27951, avg=8241.47, stdev=4416.80
    clat percentiles (usec):
     |  1.00th=[ 3818],  5.00th=[ 5800], 10.00th=[ 5800], 20.00th=[ 5866],
     | 30.00th=[ 5997], 40.00th=[ 5997], 50.00th=[ 6063], 60.00th=[ 6194],
     | 70.00th=[ 6259], 80.00th=[10814], 90.00th=[12256], 95.00th=[19530],
     | 99.00th=[22414], 99.50th=[22676], 99.90th=[22938], 99.95th=[24773],
     | 99.99th=[26608]
   bw (  MiB/s): min= 1754, max= 4748, per=97.17%, avg=3718.40, stdev=1353.35, samples=5
   iops        : min= 1754, max= 4748, avg=3718.40, stdev=1353.35, samples=5
  lat (usec)   : 4=0.05%, 250=0.05%, 500=0.05%, 750=0.08%, 1000=0.06%
  lat (msec)   : 2=0.24%, 4=0.52%, 10=77.15%, 20=17.30%, 50=4.50%
  cpu          : usr=1.31%, sys=88.07%, ctx=1538, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3827MiB/s (4012MB/s), 3827MiB/s-3827MiB/s (4012MB/s-4012MB/s), io=10.0GiB (10.7GB), run=2676-2676msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=475MiB/s][w=475 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][76.5%][w=137MiB/s][w=137 IOPS][eta 00m:04s] 
Jobs: 1 (f=1): [W(1)][90.5%][w=410MiB/s][w=410 IOPS][eta 00m:02s] 
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                        
TEST: (groupid=0, jobs=1): err= 0: pid=334563: Mon Dec  4 02:50:04 2023
  write: IOPS=456, BW=457MiB/s (479MB/s)(10.0GiB/22429msec); 0 zone resets
    slat (usec): min=227, max=111811, avg=1994.58, stdev=2098.70
    clat (usec): min=3, max=2008.2k, avg=67553.89, stdev=118485.07
     lat (usec): min=284, max=2009.9k, avg=69548.96, stdev=119234.16
    clat percentiles (msec):
     |  1.00th=[    9],  5.00th=[    9], 10.00th=[   12], 20.00th=[   16],
     | 30.00th=[   47], 40.00th=[   48], 50.00th=[   53], 60.00th=[   58],
     | 70.00th=[   63], 80.00th=[   75], 90.00th=[  113], 95.00th=[  184],
     | 99.00th=[  309], 99.50th=[  338], 99.90th=[ 1989], 99.95th=[ 2005],
     | 99.99th=[ 2005]
   bw (  KiB/s): min=92160, max=2594816, per=100.00%, avg=497963.71, stdev=447542.73, samples=41
   iops        : min=   90, max= 2534, avg=486.29, stdev=437.05, samples=41
  lat (usec)   : 4=0.02%, 10=0.03%, 500=0.01%, 750=0.02%, 1000=0.01%
  lat (msec)   : 2=0.07%, 4=0.16%, 10=7.78%, 20=14.80%, 50=20.62%
  lat (msec)   : 100=44.93%, 250=9.29%, 500=1.96%, 2000=0.23%, >=2000=0.07%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1320, max=1320, avg=1320.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1320],  5.00th=[ 1320], 10.00th=[ 1320], 20.00th=[ 1320],
     | 30.00th=[ 1320], 40.00th=[ 1320], 50.00th=[ 1320], 60.00th=[ 1320],
     | 70.00th=[ 1320], 80.00th=[ 1320], 90.00th=[ 1320], 95.00th=[ 1320],
     | 99.00th=[ 1320], 99.50th=[ 1320], 99.90th=[ 1320], 99.95th=[ 1320],
     | 99.99th=[ 1320]
  cpu          : usr=2.56%, sys=23.95%, ctx=66043, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=457MiB/s (479MB/s), 457MiB/s-457MiB/s (479MB/s-479MB/s), io=10.0GiB (10.7GB), run=22429-22429msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2752MiB/s][r=2752 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=417205: Mon Dec  4 02:50:13 2023
  read: IOPS=2721, BW=2722MiB/s (2854MB/s)(10.0GiB/3762msec)
    slat (usec): min=308, max=1025, avg=364.47, stdev=32.71
    clat (usec): min=3, max=27352, avg=11278.54, stdev=1011.09
     lat (usec): min=360, max=28208, avg=11643.38, stdev=1026.37
    clat percentiles (usec):
     |  1.00th=[ 7242],  5.00th=[11207], 10.00th=[11207], 20.00th=[11207],
     | 30.00th=[11207], 40.00th=[11207], 50.00th=[11207], 60.00th=[11338],
     | 70.00th=[11338], 80.00th=[11338], 90.00th=[11731], 95.00th=[11731],
     | 99.00th=[11994], 99.50th=[12780], 99.90th=[22938], 99.95th=[25035],
     | 99.99th=[26870]
   bw (  MiB/s): min= 2484, max= 2754, per=99.69%, avg=2713.43, stdev=101.18, samples=7
   iops        : min= 2484, max= 2754, avg=2713.43, stdev=101.18, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.04%, 1000=0.01%
  lat (msec)   : 2=0.15%, 4=0.26%, 10=0.81%, 20=98.47%, 50=0.17%
  cpu          : usr=1.25%, sys=98.64%, ctx=11, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2722MiB/s (2854MB/s), 2722MiB/s-2722MiB/s (2854MB/s-2854MB/s), io=10.0GiB (10.7GB), run=3762-3762msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][50.0%][w=344MiB/s][w=344 IOPS][eta 00m:07s]
Jobs: 1 (f=1): [W(1)][81.2%][w=329MiB/s][w=329 IOPS][eta 00m:03s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=408MiB/s][w=408 IOPS][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=417553: Mon Dec  4 02:50:40 2023
  write: IOPS=477, BW=478MiB/s (501MB/s)(10.0GiB/21442msec); 0 zone resets
    slat (usec): min=228, max=5360, avg=1811.29, stdev=960.33
    clat (usec): min=3, max=2891.3k, avg=64485.53, stdev=157705.98
     lat (usec): min=396, max=2892.8k, avg=66297.42, stdev=157867.23
    clat percentiles (msec):
     |  1.00th=[    9],  5.00th=[   12], 10.00th=[   15], 20.00th=[   20],
     | 30.00th=[   48], 40.00th=[   52], 50.00th=[   58], 60.00th=[   66],
     | 70.00th=[   71], 80.00th=[   81], 90.00th=[   91], 95.00th=[  103],
     | 99.00th=[  140], 99.50th=[  148], 99.90th=[ 2869], 99.95th=[ 2903],
     | 99.99th=[ 2903]
   bw (  KiB/s): min=16384, max=2220032, per=100.00%, avg=537276.63, stdev=392435.49, samples=38
   iops        : min=   16, max= 2168, avg=524.68, stdev=383.24, samples=38
  lat (usec)   : 4=0.01%, 10=0.04%, 500=0.01%, 750=0.02%, 1000=0.02%
  lat (msec)   : 2=0.05%, 4=0.14%, 10=2.79%, 20=18.78%, 50=16.38%
  lat (msec)   : 100=56.35%, 250=5.12%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=791, max=791, avg=791.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  788],  5.00th=[  788], 10.00th=[  788], 20.00th=[  788],
     | 30.00th=[  788], 40.00th=[  788], 50.00th=[  788], 60.00th=[  788],
     | 70.00th=[  788], 80.00th=[  788], 90.00th=[  788], 95.00th=[  788],
     | 99.00th=[  788], 99.50th=[  788], 99.90th=[  788], 99.95th=[  788],
     | 99.99th=[  788]
  cpu          : usr=2.61%, sys=28.97%, ctx=65408, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=478MiB/s (501MB/s), 478MiB/s-478MiB/s (501MB/s-501MB/s), io=10.0GiB (10.7GB), run=21442-21442msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][-.-%][r=2236MiB/s][r=2236 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=504277: Mon Dec  4 02:50:52 2023
  read: IOPS=2809, BW=2809MiB/s (2946MB/s)(10.0GiB/3645msec)
    slat (usec): min=301, max=826, avg=353.16, stdev=27.27
    clat (usec): min=3, max=24458, avg=10931.36, stdev=948.03
     lat (usec): min=347, max=25285, avg=11284.82, stdev=960.59
    clat percentiles (usec):
     |  1.00th=[ 7046],  5.00th=[10814], 10.00th=[10814], 20.00th=[10945],
     | 30.00th=[10945], 40.00th=[10945], 50.00th=[10945], 60.00th=[10945],
     | 70.00th=[10945], 80.00th=[10945], 90.00th=[11338], 95.00th=[11469],
     | 99.00th=[12125], 99.50th=[12649], 99.90th=[20579], 99.95th=[22676],
     | 99.99th=[23987]
   bw (  MiB/s): min= 2588, max= 2842, per=99.70%, avg=2800.86, stdev=94.09, samples=7
   iops        : min= 2588, max= 2842, avg=2800.86, stdev=94.09, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.83%, 20=98.47%, 50=0.12%
  cpu          : usr=0.85%, sys=99.12%, ctx=13, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2809MiB/s (2946MB/s), 2809MiB/s-2809MiB/s (2946MB/s-2946MB/s), io=10.0GiB (10.7GB), run=3645-3645msec
--------------------------------------------------------------------------------
/mnt/Tank #   
```

I think I'm going to replace the SATA cables next. A friend has some premium corsair ones he isn't using from an 8 bay. I can use those for the array.

It still doesn't look like the underlying problem has gone away.

I shouldn't be getting 1/4 of the write speed 1fallen has with a 980 Pro when he's using a WD Blue. Unless I have missed something here??

Did all 10 SATA cables suddenly fail when I moved to Jammy? Nah. This is just naff. I am so tempted to move 'on to' Focal or back to Bionic just to test when I get a couple of hours.

Edit: you guys are both on Noble, even Noble testing sounds good at this point.

Edit2: Sorry, I'm just totally frustrated at this point. I've never had a single issue with ZFS on Ubuntu until Jammy. I feel like the NVMe has only helped mask the problem.

---

### Post by MAFoElffen on 2023-12-03
Sorry, have been frustrated myself with Launchpad, related to reported ZFS Issues, and bug reports.

I felt sorry for other Users affected and created this, so I cn start documenting things for supporting Users:
[https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin](https://github.com/Mafoelffen1/OpenZFS-Ubuntu-Admin)

You readjusted you ARC max setting to half your new RAM now, and redid your update-initramfs again, right? Just making sure that isn't still at 16GB...

Well heck. Dumping the caches and freeing up memory had helped, so sort of pointed to increasing memory and adding caches. 

I think what may help and what that is pointing to now is the need to audit what else is going on, when that slowdown occurs. If the caches and memory is not the answer, then something else is dragging it down intermittently.

That is the "key", and what is making that hard to pin down. It's an intermittent problem.

EDIT: Divng deeper to confirm if the SATA ports on that board are SATA III, and the drive specs. Something... I don't see what is going on there.

---

### Post by MAFoElffen on 2023-12-04
Dang. LMFAO!!! I could swear you posted a link to you rMB's manual. I loked for what seemed like forever... I found it in the greyed out text in tha one post you edited...

Then... My head was swimming trying to figure out all the variations and conditions of that manual. I feel your pain, and what you meant by the memory caveats. The storage section is the same!
> 
Storage &#8226; 10 x SATA3 6.0 Gb/s Connectors, support RAID (RAID
0, RAID 1, RAID 5, RAID 10 and Intel Rapid Storage 13),
NCQ, AHCI, Hot Plug and ASRock HDD Saver Technology
(S_SATA3_3 connector is shared with the eSATA port)
(S_SATA3_2 connector is shared with Ultra M.2 Socket)
* RAID is supported on SATA3_0 ~ SATA3_5 ports only.
&#8226; 1 x eSATA Connector, supports NCQ, AHCI and Hot Plug
&#8226; 1 x Ultra M.2 Socket, supports M.2 SATA3 6.0 Gb/s module
and M.2 PCI Express module up to Gen3 x4 (32 Gb/s)

Your HHD's are all SATA III 6GB/s. You rSATA ports are all SATA III 6GB/s.

Has 10 SATA ports but... S_SATA3_3 is hared with eSATA port, and S_SATA3_@ i shared with the M.2 Ultra port... Being shared on that Bus, that usually means that an shared on that M.2 port only supports 6GB/s SATA, not an M.2 PCIe card. BUT elsewhere:
> 
The Ultra M.2 Socket (M2_1) can accommodate either a M.2 SATA3 6.0 Gb/s module or a M.2 PCI
Express module up to Gen3 x4 (32 Gb/s). 

Please be noted that the Ultra M.2 Socket (M2_1) is shared with the S_SATA3_2 connector; you can only choose either the Ultra M.2 Socket
(M2_1) or the S_SATA3_2 connector to use.

* If M.2 PCI Express module is installed, PCIE3 will be disabled.

So if I am reading that right... If you use M.2 slot one, it disables both the SATA port S_SATA3_2 & PCIe slot 3? 

Then out of 6 PCIe x16 slots, 2 are x16 lane, 3 are 8 lane, and 1 is 4 lane?

Wow. I typed that all out and my head is still spinning. LOL

---

### Post by tkae-lp on 2023-12-04
> **MAFoElffen said:**
> My head was swimming trying to figure out all the variations and  conditions of that manual. I feel your pain, and what you meant by the  memory caveats. The storage section is the same!

Yeah, it's not been fun getting through that manual lol. Good spot on that SATA port getting disabled, I didn't even notice that! I only noticed that PCIe slot 3 would be disabled.... on page 22 it also says that if I use eSATA at rear, I lose S_SATA3_3:

```
These ten SATA3
connectors support SATA
data cables for internal
storage devices with up
to 6.0 Gb/s data transfer
rate. If the eSATA port
on the rear I/O has been
connected, the internal
S_SATA3_3 will not
function. If the Ultra M.2
Socket has been occupied,
the internal S_SATA3_2
will not function.
```


I suppose there are a LOT of ports... they can only accommodate so much for a £200 mobo ;D What I don't understand is..... with the NVMe in place, S_SATA3_2 doesn't appear to be disabled?! I mean, my entire array is still there:


```
  pool: Tank
 state: ONLINE
  scan: scrub repaired 0B in 10:00:01 with 0 errors on Mon Nov 13 23:01:24 2023
config:

    NAME                                                                STATE     READ WRITE CKSUM
    Tank                                                                ONLINE       0     0     0
      raidz2-0                                                          ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W538XXXX-part2  ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W538XXXX-part1  ONLINE       0     0     0
```

I show 11 drives connected:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293154&stc=1[/IMG]

Perhaps a firmware update since the manual was printed allows them to run at a reduced rate? Regardless, let's not leave the NVMe in that slot. 

The manual says:

```
PCIE1 (PCIe 3.0 x16 slot) is used for PCI Express x16 lane width graphics cards.
PCIE2 (PCIe 3.0 x16 slot) is used for PCI Express x8 lane width graphics cards.
PCIE3 (PCIe 3.0 x16 slot) is used for PCI Express x8 lane width graphics cards.
PCIE4 (PCIe 3.0 x16 slot) is used for PCI Express x16 lane width graphics cards.
PCIE5 (PCIe 2.0 x16 slot) is used for PCI Express x4 lane width graphics cards.
PCIE6 (PCIe 3.0 x16 slot) is used for PCI Express x8 lane width graphics cards.
```

This slot is free: **PCIE4 (PCIe 3.0 x16 slot) is used for PCI Express x16 lane width graphics cards. (See Roadmap below)**


No I haven't adjusted my ARC yet, because I don't actually have any of the RAM - It's all been dispatched, I'm just waiting for it. I'm still on 32GB. Hopefully by the end of this week I'll be on 128GB.

So here's my sort of roadmap thinking before we dig deeper:

1. Grab those SATA cables from my mate, eliminate aged copper wiring
2. Wait for the RAM to arrive, max it out, set arc to 64GB
3. Grab this: [https://amzn.eu/d/he4RABR](https://amzn.eu/d/he4RABR)  and move the NVMe to to Slot 4 - I know x16 is way overkill but lets eliminate as much as we can.

The NVMe to PCIe adapter will arrive tomorrow - I'll remove the ARC and SLOGs from the array and test just the speed of the Samsung 980 Pro in the M.2 Ultra slot where it is now before I move it over, then test again once it's moved to PCIe Slot 4.

> **MAFoElffen said:**
> Wow. I typed that all out and my head is still spinning. LOL

Mine too, this whole thing has been a bit of a 'deep end' learning curve for me, but it's been fun (except that manual! lol) and I *have learned a lot.*

---

### Post by MAFoElffen on 2023-12-04
Both my servers have a PCIe Quad m.2 adapters with onboard bifurcation... This is the card I use for that (and I am very happy with): 
[M.2 Key SSD Expansion Card ANM24PE16 4-Port PCIe3.0 X16 With PLX8748 Controller]("https://www.aliexpress.us/item/3256801158360351.html?spm=a2g0o.order_list.order_list_main.11.54a0180248brsl&gatewayAdapt=glo2usa") On my server, I have 4xNVMe RAIDZ2 array on it's card.

On one of those, my server, I also have two of these... [https://www.amazon.com/ACTIMED-Power...09FLGR1X9?th=1](https://www.amazon.com/ACTIMED-Power...09FLGR1X9?th=1) That is only x1, because I had two x1 PCIe slot open on it. That is actually what I have my disk caches in, for my SSD 5xSSD RAIDZ2 array. They have x4 lane cards that would have been faster. I liked that both came with heat sinks.

---

### Post by tkae-lp on 2023-12-04
I've saved that first one you linked in my Ali cart, but the second link doesn't work.

If I understand it correctly, the main advantage of that ANM24PE16 card is that it allows multiple NVMes _even if your motherboard doesn't support PCIe bifurcation_?

Do you think what I grabbed on Amazon is total rubbish? (genuinely interested in your opinion!) my thinking was for a single NVMe, it's a straight through connection so wouldn't matter (nothing to go wrong and nothing to deal with traffic for more than 1 NVMe) There's no components to get hot either, the components that appear to get hot are on the cards that *don't* *require *your mobo to have bifurcation because they're doing the work on board. Eg. If I look at something like this: [https://amzn.eu/d/gP2jhjR](https://amzn.eu/d/gP2jhjR) it clearly states bifurcation support is needed but doesn't have a heat sink because there's not much to it. Even something more expensive like this: [https://amzn.eu/d/isaN3WK](https://amzn.eu/d/isaN3WK) the cooling seems to be for the NVMes themselves, not the device circuitry (presumably because it's not dealing with the bifurcation).

In any case, I checked my mobo manual and I do not have support for bifurcation (at  least a search shows the word doesn't appear in the entire thing). So unless you think what I've ordered is utter crap, I'll see how that goes for now and then maybe grab one of those cards you linked to on Ali in the new year for future expansions.

---

### Post by tkae-lp on 2023-12-05
UPGRADE TIME!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293161&stc=1[/IMG]


Here's the benches for just the NVMe in the M.2 slot on the mobo - ext4 fs:

```
/mnt/Tank # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting 
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 1 (f=1): [W(1)][-.-%][w=3236MiB/s][w=3236 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3475938: Tue Dec  5 17:10:43 2023
  write: IOPS=3217, BW=3217MiB/s (3373MB/s)(10.0GiB/3183msec); 0 zone resets
    slat (usec): min=32, max=229, avg=83.12, stdev=18.04
    clat (usec): min=2023, max=25077, avg=9835.94, stdev=1441.38
     lat (usec): min=2090, max=25185, avg=9919.39, stdev=1441.26
    clat percentiles (usec):
     |  1.00th=[ 4146],  5.00th=[ 9503], 10.00th=[ 9503], 20.00th=[ 9503],
     | 30.00th=[ 9503], 40.00th=[ 9503], 50.00th=[ 9634], 60.00th=[ 9634],
     | 70.00th=[10028], 80.00th=[10159], 90.00th=[10159], 95.00th=[10421],
     | 99.00th=[14484], 99.50th=[17695], 99.90th=[23462], 99.95th=[24249],
     | 99.99th=[24773]
   bw (  MiB/s): min= 3204, max= 3242, per=100.00%, avg=3223.67, stdev=16.17, samples=6
   iops        : min= 3204, max= 3242, avg=3223.67, stdev=16.17, samples=6
  lat (msec)   : 4=0.97%, 10=66.02%, 20=32.73%, 50=0.28%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=754, max=754, avg=754.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  756],  5.00th=[  756], 10.00th=[  756], 20.00th=[  756],
     | 30.00th=[  756], 40.00th=[  756], 50.00th=[  756], 60.00th=[  756],
     | 70.00th=[  756], 80.00th=[  756], 90.00th=[  756], 95.00th=[  756],
     | 99.00th=[  756], 99.50th=[  756], 99.90th=[  756], 99.95th=[  756],
     | 99.99th=[  756]
  cpu          : usr=15.24%, sys=13.89%, ctx=10212, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3217MiB/s (3373MB/s), 3217MiB/s-3217MiB/s (3373MB/s-3373MB/s), io=10.0GiB (10.7GB), run=3183-3183msec

Disk stats (read/write):
  nvme0n1: ios=0/24092, merge=0/50, ticks=0/232564, in_queue=232578, util=96.88%
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][w=3226MiB/s][w=3226 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3476169: Tue Dec  5 17:10:51 2023
  write: IOPS=3217, BW=3217MiB/s (3373MB/s)(10.0GiB/3183msec); 0 zone resets
    slat (usec): min=28, max=6077, avg=85.47, stdev=63.53
    clat (usec): min=1909, max=29194, avg=9831.99, stdev=1622.54
     lat (usec): min=1963, max=29289, avg=9917.81, stdev=1621.38
    clat percentiles (usec):
     |  1.00th=[ 4047],  5.00th=[ 9372], 10.00th=[ 9503], 20.00th=[ 9503],
     | 30.00th=[ 9503], 40.00th=[ 9503], 50.00th=[ 9503], 60.00th=[ 9634],
     | 70.00th=[10028], 80.00th=[10028], 90.00th=[10159], 95.00th=[10290],
     | 99.00th=[15401], 99.50th=[17957], 99.90th=[27395], 99.95th=[28181],
     | 99.99th=[28967]
   bw (  MiB/s): min= 3170, max= 3254, per=100.00%, avg=3227.67, stdev=34.00, samples=6
   iops        : min= 3170, max= 3254, avg=3227.67, stdev=34.00, samples=6
  lat (msec)   : 2=0.10%, 4=0.89%, 10=66.72%, 20=31.99%, 50=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=794, max=794, avg=794.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  796],  5.00th=[  796], 10.00th=[  796], 20.00th=[  796],
     | 30.00th=[  796], 40.00th=[  796], 50.00th=[  796], 60.00th=[  796],
     | 70.00th=[  796], 80.00th=[  796], 90.00th=[  796], 95.00th=[  796],
     | 99.00th=[  796], 99.50th=[  796], 99.90th=[  796], 99.95th=[  796],
     | 99.99th=[  796]
  cpu          : usr=15.24%, sys=14.36%, ctx=10215, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3217MiB/s (3373MB/s), 3217MiB/s-3217MiB/s (3373MB/s-3373MB/s), io=10.0GiB (10.7GB), run=3183-3183msec

Disk stats (read/write):
  nvme0n1: ios=0/21901, merge=0/8, ticks=0/210619, in_queue=210632, util=96.82%
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3399MiB/s][r=3399 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3476732: Tue Dec  5 17:11:09 2023
  read: IOPS=3388, BW=3388MiB/s (3553MB/s)(10.0GiB/3022msec)
    slat (usec): min=27, max=437, avg=67.48, stdev=22.48
    clat (usec): min=1016, max=15803, avg=9337.20, stdev=1130.69
     lat (usec): min=1057, max=15871, avg=9405.05, stdev=1128.62
    clat percentiles (usec):
     |  1.00th=[ 6587],  5.00th=[ 7701], 10.00th=[ 8029], 20.00th=[ 8586],
     | 30.00th=[ 8848], 40.00th=[ 9110], 50.00th=[ 9372], 60.00th=[ 9634],
     | 70.00th=[ 9896], 80.00th=[10159], 90.00th=[10683], 95.00th=[11076],
     | 99.00th=[11994], 99.50th=[12649], 99.90th=[14484], 99.95th=[15270],
     | 99.99th=[15664]
   bw (  MiB/s): min= 3340, max= 3408, per=100.00%, avg=3389.33, stdev=25.13, samples=6
   iops        : min= 3340, max= 3408, avg=3389.33, stdev=25.13, samples=6
  lat (msec)   : 2=0.11%, 4=0.21%, 10=75.05%, 20=24.64%
  cpu          : usr=2.25%, sys=27.38%, ctx=8986, majf=0, minf=8202
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3388MiB/s (3553MB/s), 3388MiB/s-3388MiB/s (3553MB/s-3553MB/s), io=10.0GiB (10.7GB), run=3022-3022msec

Disk stats (read/write):
  nvme0n1: ios=19615/746, merge=0/5, ticks=143388/147, in_queue=143546, util=97.39%
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3401MiB/s][r=3401 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3476925: Tue Dec  5 17:11:15 2023
  read: IOPS=3384, BW=3384MiB/s (3548MB/s)(10.0GiB/3026msec)
    slat (usec): min=29, max=462, avg=67.94, stdev=24.57
    clat (usec): min=1565, max=15506, avg=9349.91, stdev=1144.48
     lat (usec): min=1631, max=15563, avg=9418.21, stdev=1142.15
    clat percentiles (usec):
     |  1.00th=[ 6390],  5.00th=[ 7635], 10.00th=[ 8094], 20.00th=[ 8586],
     | 30.00th=[ 8848], 40.00th=[ 9110], 50.00th=[ 9372], 60.00th=[ 9634],
     | 70.00th=[ 9896], 80.00th=[10159], 90.00th=[10683], 95.00th=[11076],
     | 99.00th=[12125], 99.50th=[13435], 99.90th=[15008], 99.95th=[15270],
     | 99.99th=[15270]
   bw (  MiB/s): min= 3344, max= 3416, per=100.00%, avg=3384.67, stdev=29.25, samples=6
   iops        : min= 3344, max= 3416, avg=3384.67, stdev=29.25, samples=6
  lat (msec)   : 2=0.06%, 4=0.13%, 10=75.18%, 20=24.64%
  cpu          : usr=2.18%, sys=27.50%, ctx=8954, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3384MiB/s (3548MB/s), 3384MiB/s-3384MiB/s (3548MB/s-3548MB/s), io=10.0GiB (10.7GB), run=3026-3026msec

Disk stats (read/write):
  nvme0n1: ios=20818/738, merge=0/0, ticks=150824/124, in_queue=150949, util=97.39%

```

See you in a bit.....

---

### Post by #&amp;thj^% on 2023-12-05
Looking Good!

---

### Post by tkae-lp on 2023-12-05
Right! Most of it was good.....

So good news and bad.

_Bad_: The smaller seller I got the 2 sticks off lied to me. They sent me 2 sticks with totally different part numbers on, even each stick is different. Didn't notice when I took the photo (2 white packets), but as I was taking them out the packet, I clocked it. Idiots. This is open and shut eBay not as described. They list the PN I want/need in the title and in description. So, I have 96GB of memory running at triple channel. I will return these.

_Good_: SATA cables seem good, took the opportunity to blow out the chassis with air,, no erupted caps on the board (all the usual checks, including removing half a cat from the Noctua heatsinks lol) and NVMe works in PCIe slot 4 with the cheapo adapter.

The memory seller who didn't let me down are called ByteStock UK. All four of theirs are as described and work well -  they've been very helpful, quick to respond to emails and lightning to  dispatch. RAM came in bullet proof packaging. Thoroughly recommended.  Good stuff guys. I'll get the remaining 2 I need off them.

So the tests of that NVMe in slot 4:

```
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][w=3262MiB/s][w=3262 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=17288: Tue Dec  5 19:28:54 2023
  write: IOPS=3262, BW=3262MiB/s (3421MB/s)(10.0GiB/3139msec); 0 zone resets
    slat (usec): min=28, max=8656, avg=81.74, stdev=85.75
    clat (usec): min=1589, max=24667, avg=9672.76, stdev=1434.84
     lat (usec): min=1638, max=24750, avg=9754.83, stdev=1433.55
    clat percentiles (usec):
     |  1.00th=[ 4228],  5.00th=[ 9503], 10.00th=[ 9503], 20.00th=[ 9503],
     | 30.00th=[ 9503], 40.00th=[ 9503], 50.00th=[ 9503], 60.00th=[ 9503],
     | 70.00th=[ 9503], 80.00th=[ 9503], 90.00th=[ 9503], 95.00th=[ 9634],
     | 99.00th=[15926], 99.50th=[17433], 99.90th=[22414], 99.95th=[23462],
     | 99.99th=[24511]
   bw (  MiB/s): min= 3246, max= 3302, per=100.00%, avg=3270.00, stdev=23.97, samples=6
   iops        : min= 3246, max= 3302, avg=3270.00, stdev=23.97, samples=6
  lat (msec)   : 2=0.07%, 4=0.89%, 10=94.21%, 20=4.61%, 50=0.22%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=753, max=753, avg=753.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  756],  5.00th=[  756], 10.00th=[  756], 20.00th=[  756],
     | 30.00th=[  756], 40.00th=[  756], 50.00th=[  756], 60.00th=[  756],
     | 70.00th=[  756], 80.00th=[  756], 90.00th=[  756], 95.00th=[  756],
     | 99.00th=[  756], 99.50th=[  756], 99.90th=[  756], 99.95th=[  756],
     | 99.99th=[  756]
  cpu          : usr=16.44%, sys=12.52%, ctx=10198, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3262MiB/s (3421MB/s), 3262MiB/s-3262MiB/s (3421MB/s-3421MB/s), io=10.0GiB (10.7GB), run=3139-3139msec

Disk stats (read/write):
  nvme0n1: ios=1/20335, merge=0/2, ticks=9/192827, in_queue=192837, util=96.24%
--------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][w=3267MiB/s][w=3267 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=19268: Tue Dec  5 19:29:08 2023
  write: IOPS=3252, BW=3253MiB/s (3411MB/s)(10.0GiB/3148msec); 0 zone resets
    slat (usec): min=38, max=7193, avg=87.27, stdev=71.28
    clat (usec): min=2143, max=24835, avg=9697.95, stdev=1558.63
     lat (usec): min=2209, max=24929, avg=9785.66, stdev=1556.83
    clat percentiles (usec):
     |  1.00th=[ 3916],  5.00th=[ 9503], 10.00th=[ 9503], 20.00th=[ 9503],
     | 30.00th=[ 9503], 40.00th=[ 9503], 50.00th=[ 9503], 60.00th=[ 9503],
     | 70.00th=[ 9503], 80.00th=[ 9503], 90.00th=[ 9503], 95.00th=[ 9634],
     | 99.00th=[15926], 99.50th=[17433], 99.90th=[22938], 99.95th=[23987],
     | 99.99th=[24511]
   bw (  MiB/s): min= 3224, max= 3288, per=100.00%, avg=3260.00, stdev=24.88, samples=6
   iops        : min= 3224, max= 3288, avg=3260.00, stdev=24.88, samples=6
  lat (msec)   : 4=1.03%, 10=94.13%, 20=4.60%, 50=0.24%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=830, max=830, avg=830.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  828],  5.00th=[  828], 10.00th=[  828], 20.00th=[  828],
     | 30.00th=[  828], 40.00th=[  828], 50.00th=[  828], 60.00th=[  828],
     | 70.00th=[  828], 80.00th=[  828], 90.00th=[  828], 95.00th=[  828],
     | 99.00th=[  828], 99.50th=[  828], 99.90th=[  828], 99.95th=[  828],
     | 99.99th=[  828]
  cpu          : usr=16.94%, sys=14.17%, ctx=10211, majf=0, minf=11
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3253MiB/s (3411MB/s), 3253MiB/s-3253MiB/s (3411MB/s-3411MB/s), io=10.0GiB (10.7GB), run=3148-3148msec

Disk stats (read/write):
  nvme0n1: ios=0/20267, merge=0/1, ticks=0/192642, in_queue=192644, util=96.21%
--------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3417MiB/s][r=3417 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=22263: Tue Dec  5 19:29:44 2023
  read: IOPS=3398, BW=3399MiB/s (3564MB/s)(10.0GiB/3013msec)
    slat (usec): min=30, max=463, avg=56.47, stdev=21.63
    clat (usec): min=1606, max=15963, avg=9322.58, stdev=1021.37
     lat (usec): min=1666, max=16017, avg=9379.36, stdev=1022.37
    clat percentiles (usec):
     |  1.00th=[ 6980],  5.00th=[ 7832], 10.00th=[ 8160], 20.00th=[ 8586],
     | 30.00th=[ 8979], 40.00th=[ 9110], 50.00th=[ 9372], 60.00th=[ 9503],
     | 70.00th=[ 9634], 80.00th=[10028], 90.00th=[10552], 95.00th=[10945],
     | 99.00th=[11731], 99.50th=[11994], 99.90th=[14091], 99.95th=[15139],
     | 99.99th=[15795]
   bw (  MiB/s): min= 3328, max= 3422, per=99.96%, avg=3397.33, stdev=34.91, samples=6
   iops        : min= 3328, max= 3422, avg=3397.33, stdev=34.91, samples=6
  lat (msec)   : 2=0.10%, 4=0.12%, 10=78.68%, 20=21.10%
  cpu          : usr=2.62%, sys=22.51%, ctx=8641, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3399MiB/s (3564MB/s), 3399MiB/s-3399MiB/s (3564MB/s-3564MB/s), io=10.0GiB (10.7GB), run=3013-3013msec

Disk stats (read/write):
  nvme0n1: ios=19675/0, merge=0/0, ticks=139882/0, in_queue=139883, util=96.86%
--------------------------------------------------------------------------------
/mnt/speedtest # cd /mnt/speedtest && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3412MiB/s][r=3412 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=22933: Tue Dec  5 19:29:49 2023
  read: IOPS=3398, BW=3399MiB/s (3564MB/s)(10.0GiB/3013msec)
    slat (usec): min=28, max=493, avg=58.35, stdev=22.38
    clat (usec): min=1638, max=15810, avg=9318.01, stdev=1056.44
     lat (usec): min=1707, max=15869, avg=9376.69, stdev=1056.58
    clat percentiles (usec):
     |  1.00th=[ 6718],  5.00th=[ 7832], 10.00th=[ 8160], 20.00th=[ 8586],
     | 30.00th=[ 8848], 40.00th=[ 9110], 50.00th=[ 9372], 60.00th=[ 9503],
     | 70.00th=[ 9765], 80.00th=[10159], 90.00th=[10552], 95.00th=[10945],
     | 99.00th=[11863], 99.50th=[12518], 99.90th=[14484], 99.95th=[14877],
     | 99.99th=[15664]
   bw (  MiB/s): min= 3326, max= 3422, per=99.94%, avg=3396.67, stdev=35.46, samples=6
   iops        : min= 3326, max= 3422, avg=3396.67, stdev=35.46, samples=6
  lat (msec)   : 2=0.08%, 4=0.17%, 10=78.13%, 20=21.62%
  cpu          : usr=3.09%, sys=22.88%, ctx=8581, majf=0, minf=8202
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=3399MiB/s (3564MB/s), 3399MiB/s-3399MiB/s (3564MB/s-3564MB/s), io=10.0GiB (10.7GB), run=3013-3013msec

Disk stats (read/write):
  nvme0n1: ios=19673/2, merge=0/1, ticks=142262/7, in_queue=142272, util=96.73%
--------------------------------------------------------------------------------
/mnt/speedtest #   
```


Slight variations, but I'm overall very pleased, we've probably maxed out the mobo on this.


I've re-added the L2ARC and SLOG, which if anyone is interested, the part type you need if using gnome disk utility is Solaris Reserved. I checked the code provided by MAFoElffen, and that's what it is (yes I'm a shameless lazy GUI user ;) :

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293162&stc=1[/IMG]


I've altered the ZFS.conf to 8GB min, 64GB max... this seems like a logical starting point to me (please correct me if this is stupid):

```
options zfs zfs_arc_min=8589934592
options zfs zfs_arc_max=68719476736

```


Now we wait :)

---

### Post by #&amp;thj^% on 2023-12-05
I'm happy for you, that looks very decent.
Sad to hear about the RAM though, but if they come through like they say, sounds like a happy ending.

---

### Post by tkae-lp on 2023-12-05
> **1fallen said:**
> I'm happy for you, that looks very decent.
Sad to hear about the RAM though, but if they come through like they say, sounds like a happy ending.

Thanks :) I am happy with how things are going. I must admit, I was a bit p***** off that the smaller seller sent me the wrong stuff but it's no skin off my nose apart from dropping the return in at a post office. I'll get the right stuff from ByteStock and all will be well. I could probably just leave it at 96GB but I was looking forward to maxing out lol

One thing I will say, to continue the saga of the odd mobo and it's manual, I had a job figuring out which slots to put the stuff in. It looks like the correct order is:

A1, B1, C1, D1, A2, B2, D2, C2, which if you have 6 sticks is this (as if you are looking down on the board:

```
| Populated | Populated | Populated | Populated || {CPU HERE} || Empty | Empty | Populated | Populated |
```

Page 16 in the manual ([https://download.asrock.com/Manual/X99%20WS.pdf](https://download.asrock.com/Manual/X99%20WS.pdf)) says this is due to "Due to Intel® CPU spec deinition".......... mmmmhmmm. It sucked. Spent an hour on that lol

I forgot in the previous post, but here are the array speed tests:

```
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting 
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][17.1%][r=238MiB/s][r=238 IOPS][eta 00m:34s]
Jobs: 1 (f=1): [R(1)][90.9%][r=2877MiB/s][r=2877 IOPS][eta 00m:01s] 
TEST: (groupid=0, jobs=1): err= 0: pid=30416: Tue Dec  5 20:18:10 2023
  read: IOPS=983, BW=983MiB/s (1031MB/s)(10.0GiB/10416msec)
    slat (usec): min=284, max=492120, avg=1013.30, stdev=7563.61
    clat (usec): min=2, max=282667, avg=29578.16, stdev=45684.64
     lat (usec): min=334, max=688879, avg=30591.91, stdev=47362.49
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[   11], 10.00th=[   11], 20.00th=[   11],
     | 30.00th=[   11], 40.00th=[   11], 50.00th=[   11], 60.00th=[   12],
     | 70.00th=[   13], 80.00th=[   15], 90.00th=[  104], 95.00th=[  153],
     | 99.00th=[  194], 99.50th=[  232], 99.90th=[  271], 99.95th=[  275],
     | 99.99th=[  284]
   bw (  KiB/s): min=116736, max=2945024, per=96.68%, avg=973231.16, stdev=1142212.44, samples=19
   iops        : min=  114, max= 2876, avg=950.42, stdev=1115.44, samples=19
  lat (usec)   : 4=0.03%, 10=0.01%, 20=0.01%, 500=0.04%, 750=0.05%
  lat (msec)   : 2=0.12%, 4=0.25%, 10=0.78%, 20=79.43%, 50=5.30%
  lat (msec)   : 100=3.19%, 250=10.63%, 500=0.16%
  cpu          : usr=0.30%, sys=49.30%, ctx=573, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=983MiB/s (1031MB/s), 983MiB/s-983MiB/s (1031MB/s-1031MB/s), io=10.0GiB (10.7GB), run=10416-10416msec
-----------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2887MiB/s][r=2887 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=42082: Tue Dec  5 20:18:21 2023
  read: IOPS=2800, BW=2800MiB/s (2936MB/s)(10.0GiB/3657msec)
    slat (usec): min=286, max=1149, avg=354.14, stdev=45.43
    clat (usec): min=3, max=29343, avg=10958.68, stdev=1277.82
     lat (usec): min=332, max=30494, avg=11313.17, stdev=1309.57
    clat percentiles (usec):
     |  1.00th=[ 6915],  5.00th=[10552], 10.00th=[10683], 20.00th=[10683],
     | 30.00th=[10683], 40.00th=[10683], 50.00th=[10814], 60.00th=[10814],
     | 70.00th=[10814], 80.00th=[10945], 90.00th=[12780], 95.00th=[12780],
     | 99.00th=[13829], 99.50th=[15533], 99.90th=[24773], 99.95th=[27132],
     | 99.99th=[28967]
   bw (  MiB/s): min= 2236, max= 2888, per=99.61%, avg=2789.14, stdev=244.02, samples=7
   iops        : min= 2236, max= 2888, avg=2789.14, stdev=244.02, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.86%, 20=98.35%, 50=0.21%
  cpu          : usr=0.30%, sys=99.51%, ctx=24, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2800MiB/s (2936MB/s), 2800MiB/s-2800MiB/s (2936MB/s-2936MB/s), io=10.0GiB (10.7GB), run=3657-3657msec
-----------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=42697: Tue Dec  5 20:18:53 2023
  write: IOPS=756, BW=757MiB/s (793MB/s)(10.0GiB/13533msec); 0 zone resets
    slat (usec): min=200, max=1907, avg=397.35, stdev=259.33
    clat (usec): min=3, max=9472.4k, avg=40893.84, stdev=519000.21
     lat (usec): min=257, max=9474.1k, avg=41291.62, stdev=519067.61
    clat percentiles (msec):
     |  1.00th=[    7],  5.00th=[    9], 10.00th=[    9], 20.00th=[    9],
     | 30.00th=[    9], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[   13], 80.00th=[   15], 90.00th=[   24], 95.00th=[   29],
     | 99.00th=[   49], 99.50th=[   51], 99.90th=[ 9463], 99.95th=[ 9463],
     | 99.99th=[ 9463]
   bw (  MiB/s): min=  342, max= 3816, per=100.00%, avg=2253.33, stdev=1347.25, samples=9
   iops        : min=  342, max= 3816, avg=2253.33, stdev=1347.25, samples=9
  lat (usec)   : 4=0.03%, 10=0.02%, 500=0.05%, 750=0.04%, 1000=0.04%
  lat (msec)   : 2=0.17%, 4=0.31%, 10=63.33%, 20=21.87%, 50=13.61%
  lat (msec)   : 100=0.23%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1571, max=1571, avg=1571.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1576],  5.00th=[ 1576], 10.00th=[ 1576], 20.00th=[ 1576],
     | 30.00th=[ 1576], 40.00th=[ 1576], 50.00th=[ 1576], 60.00th=[ 1576],
     | 70.00th=[ 1576], 80.00th=[ 1576], 90.00th=[ 1576], 95.00th=[ 1576],
     | 99.00th=[ 1576], 99.50th=[ 1576], 99.90th=[ 1576], 99.95th=[ 1576],
     | 99.99th=[ 1576]
  cpu          : usr=4.40%, sys=20.31%, ctx=4677, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=757MiB/s (793MB/s), 757MiB/s-757MiB/s (793MB/s-793MB/s), io=10.0GiB (10.7GB), run=13533-13533msec
-----------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
TEST: (groupid=0, jobs=1): err= 0: pid=86521: Tue Dec  5 20:19:04 2023
  write: IOPS=1453, BW=1454MiB/s (1524MB/s)(10.0GiB/7044msec); 0 zone resets
    slat (usec): min=196, max=1479, avg=331.87, stdev=153.27
    clat (usec): min=3, max=3623.0k, avg=21253.97, stdev=198362.03
     lat (usec): min=260, max=3623.3k, avg=21586.28, stdev=198361.01
    clat percentiles (msec):
     |  1.00th=[    7],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[   10], 80.00th=[   13], 90.00th=[   17], 95.00th=[   20],
     | 99.00th=[   29], 99.50th=[   29], 99.90th=[ 3608], 99.95th=[ 3608],
     | 99.99th=[ 3608]
   bw (  MiB/s): min=  328, max= 3906, per=100.00%, avg=2533.25, stdev=1257.02, samples=8
   iops        : min=  328, max= 3906, avg=2533.25, stdev=1257.02, samples=8
  lat (usec)   : 4=0.05%, 500=0.04%, 750=0.05%, 1000=0.03%
  lat (msec)   : 2=0.17%, 4=0.29%, 10=70.34%, 20=24.24%, 50=4.49%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1025, max=1025, avg=1025.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1032],  5.00th=[ 1032], 10.00th=[ 1032], 20.00th=[ 1032],
     | 30.00th=[ 1032], 40.00th=[ 1032], 50.00th=[ 1032], 60.00th=[ 1032],
     | 70.00th=[ 1032], 80.00th=[ 1032], 90.00th=[ 1032], 95.00th=[ 1032],
     | 99.00th=[ 1032], 99.50th=[ 1032], 99.90th=[ 1032], 99.95th=[ 1032],
     | 99.99th=[ 1032]
  cpu          : usr=5.76%, sys=85.11%, ctx=2671, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1454MiB/s (1524MB/s), 1454MiB/s-1454MiB/s (1524MB/s-1524MB/s), io=10.0GiB (10.7GB), run=7044-7044msec
-----------------------------------------------------------------------------------------------------
/mnt/Tank #
```

Just a very tiny small increase!

---

### Post by tkae-lp on 2023-12-05
One thing I would like some input on is this:

```
/mnt/Tank # free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3
8445

```

and:

```
/mnt/Tank # arcstat
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
20:48:16     0     0      0     0    0     0    0     0    0  2.7G  8.0G    81G

```

I'm not sure what mmis stands for (minimum size?), but it appears to be 8GB, which is what I specified for minimum ARC, but then if I look at used memory above, shouldn't it be way more than that? I assumed the min arc value would allocate all of that immediately? There's no way my box is only using 445MB right now running an XFCE environment and firefox :D

---

### Post by #&amp;thj^% on 2023-12-05
> **tkae-lp said:**
> 
I'm not sure what mmis stands for (minimum size?), but it appears to be 8GB, which is what I specified for minimum ARC, but then if I look at used memory above, shouldn't it be way more than that? I assumed the min arc value would allocate all of that immediately? There's no way my box is only using 445MB right now running an XFCE environment and firefox :D

Man Machine Interface Subsystem.
And mine full-blown desktop XFCE firefox with 8 tabs open:
```
free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3
2685

```
out of 16Gigs

---

### Post by tkae-lp on 2023-12-05
So what is your minimum ARC setting?

You're using 2685MB of memory, how much of that has been assigned to ARC?

If your ARC min setting is 1GB, that seems plausible. Mine is set to min 8GB which would mean x, lxde, xfce and firefox are existing in 445MB... I don't believe it. I can only conclude that not 8GB is being used for ARC minimum.

Edit: Hang on, if we look at arcstac the size column says 2.7GB...  and a value of 'c' says 8GB. That to me looks like my ARC at that point was 2.7GB.
[s]So is it more like minimum definitely available should you need it vs minimum actually used?[/s] <-- this is stupid of me. Otherwise it would still show as allocated. Then I still don't understand why it doesn't show as used. Surely ZFS should just take it from the off.

---

### Post by tkae-lp on 2023-12-06
So here are some speed tests for today:

```
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3007MiB/s][r=3007 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1647334: Wed Dec  6 15:56:03 2023
  read: IOPS=2858, BW=2859MiB/s (2998MB/s)(10.0GiB/3582msec)
    slat (usec): min=171, max=990, avg=346.93, stdev=71.51
    clat (usec): min=2, max=27747, avg=10728.85, stdev=2145.31
     lat (usec): min=180, max=28525, avg=11076.14, stdev=2207.16
    clat percentiles (usec):
     |  1.00th=[ 4293],  5.00th=[ 5669], 10.00th=[10159], 20.00th=[10683],
     | 30.00th=[10814], 40.00th=[10814], 50.00th=[10814], 60.00th=[10814],
     | 70.00th=[10945], 80.00th=[10945], 90.00th=[12911], 95.00th=[12911],
     | 99.00th=[17695], 99.50th=[19268], 99.90th=[25560], 99.95th=[26608],
     | 99.99th=[27657]
   bw (  MiB/s): min= 2236, max= 3084, per=98.92%, avg=2828.00, stdev=309.52, samples=7
   iops        : min= 2236, max= 3084, avg=2828.00, stdev=309.52, samples=7
  lat (usec)   : 4=0.05%, 250=0.04%, 500=0.04%, 750=0.08%, 1000=0.05%
  lat (msec)   : 2=0.21%, 4=0.46%, 10=8.54%, 20=90.31%, 50=0.22%
  cpu          : usr=0.98%, sys=97.99%, ctx=143, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2859MiB/s (2998MB/s), 2859MiB/s-2859MiB/s (2998MB/s-2998MB/s), io=10.0GiB (10.7GB), run=3582-3582msec
------------------------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3033MiB/s][r=3033 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1651581: Wed Dec  6 15:56:57 2023
  read: IOPS=2933, BW=2933MiB/s (3076MB/s)(10.0GiB/3491msec)
    slat (usec): min=278, max=1042, avg=338.29, stdev=45.64
    clat (usec): min=2, max=30521, avg=10458.23, stdev=1305.77
     lat (usec): min=320, max=31564, avg=10796.84, stdev=1340.26
    clat percentiles (usec):
     |  1.00th=[ 6587],  5.00th=[10159], 10.00th=[10159], 20.00th=[10159],
     | 30.00th=[10159], 40.00th=[10159], 50.00th=[10290], 60.00th=[10290],
     | 70.00th=[10290], 80.00th=[10421], 90.00th=[12125], 95.00th=[12256],
     | 99.00th=[13566], 99.50th=[15270], 99.90th=[26084], 99.95th=[28443],
     | 99.99th=[30016]
   bw (  MiB/s): min= 2336, max= 3036, per=99.15%, avg=2908.33, stdev=280.74, samples=6
   iops        : min= 2336, max= 3036, avg=2908.33, stdev=280.74, samples=6
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.03%
  lat (msec)   : 2=0.16%, 4=0.29%, 10=1.28%, 20=97.87%, 50=0.22%
  cpu          : usr=0.20%, sys=99.68%, ctx=13, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2933MiB/s (3076MB/s), 2933MiB/s-2933MiB/s (3076MB/s-3076MB/s), io=10.0GiB (10.7GB), run=3491-3491msec
------------------------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=0): [f(1)][-.-%][w=271MiB/s][w=271 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1652217: Wed Dec  6 15:57:25 2023
  write: IOPS=1307, BW=1307MiB/s (1371MB/s)(10.0GiB/7834msec); 0 zone resets
    slat (usec): min=194, max=1086, avg=332.17, stdev=172.97
    clat (usec): min=3, max=4404.2k, avg=23646.61, stdev=241417.49
     lat (usec): min=259, max=4404.4k, avg=23979.18, stdev=241416.70
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    9], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[   10], 80.00th=[   11], 90.00th=[   18], 95.00th=[   27],
     | 99.00th=[   29], 99.50th=[   29], 99.90th=[ 4396], 99.95th=[ 4396],
     | 99.99th=[ 4396]
   bw (  MiB/s): min= 1220, max= 3880, per=100.00%, avg=2848.29, stdev=1021.29, samples=7
   iops        : min= 1220, max= 3880, avg=2848.29, stdev=1021.29, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.19%, 4=0.35%, 10=75.39%, 20=16.66%, 50=6.91%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=888, max=888, avg=888.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  892],  5.00th=[  892], 10.00th=[  892], 20.00th=[  892],
     | 30.00th=[  892], 40.00th=[  892], 50.00th=[  892], 60.00th=[  892],
     | 70.00th=[  892], 80.00th=[  892], 90.00th=[  892], 95.00th=[  892],
     | 99.00th=[  892], 99.50th=[  892], 99.90th=[  892], 99.95th=[  892],
     | 99.99th=[  892]
  cpu          : usr=5.09%, sys=87.39%, ctx=2802, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1307MiB/s (1371MB/s), 1307MiB/s-1307MiB/s (1371MB/s-1371MB/s), io=10.0GiB (10.7GB), run=7834-7834msec
------------------------------------------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
TEST: (groupid=0, jobs=1): err= 0: pid=1700516: Wed Dec  6 15:57:35 2023
  write: IOPS=1655, BW=1655MiB/s (1735MB/s)(10.0GiB/6187msec); 0 zone resets
    slat (usec): min=189, max=1788, avg=297.15, stdev=109.20
    clat (usec): min=2, max=3117.0k, avg=18663.16, stdev=170768.65
     lat (usec): min=244, max=3117.3k, avg=18960.71, stdev=170767.54
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[    9], 80.00th=[   11], 90.00th=[   13], 95.00th=[   18],
     | 99.00th=[   20], 99.50th=[   22], 99.90th=[ 3104], 99.95th=[ 3104],
     | 99.99th=[ 3104]
   bw (  MiB/s): min=  128, max= 4002, per=100.00%, avg=2848.29, stdev=1372.06, samples=7
   iops        : min=  128, max= 4002, avg=2848.29, stdev=1372.06, samples=7
  lat (usec)   : 4=0.05%, 250=0.01%, 500=0.06%, 750=0.04%, 1000=0.05%
  lat (msec)   : 2=0.19%, 4=0.35%, 10=76.46%, 20=21.93%, 50=0.57%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1021, max=1021, avg=1021.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1020],  5.00th=[ 1020], 10.00th=[ 1020], 20.00th=[ 1020],
     | 30.00th=[ 1020], 40.00th=[ 1020], 50.00th=[ 1020], 60.00th=[ 1020],
     | 70.00th=[ 1020], 80.00th=[ 1020], 90.00th=[ 1020], 95.00th=[ 1020],
     | 99.00th=[ 1020], 99.50th=[ 1020], 99.90th=[ 1020], 99.95th=[ 1020],
     | 99.99th=[ 1020]
  cpu          : usr=7.52%, sys=89.90%, ctx=818, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1655MiB/s (1735MB/s), 1655MiB/s-1655MiB/s (1735MB/s-1735MB/s), io=10.0GiB (10.7GB), run=6187-6187msec
```


Still seems to be ok.... here is arcstat after 24 hours and I caned the box yesterday watching stuff til the early hours:

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
16:00:21     0     0      0     0    0     0    0     0    0   28G   31G    51G

```

So as you predicted MAFoElffen, it really wants to have around 30GB given free rein.

---

### Post by tkae-lp on 2023-12-06
Just pushed the button on the final 2 IJ memory sticks from ByteStock. They accepted another offer of £15/stick, which was really good of them.

Not sure if this is allowed but I'm going to have to promo them a bit: I've had such a good experience with these guys, fast response, quick dispatch, bullet proof packaging, friendly and helpful on the phone / email, very knowledgeable about the compatibility. I seriously cannot fault any aspect of the purchase from start to finish and will definitely be returning in future. Here's their site: [https://www.bytestock.com/](https://www.bytestock.com/) and eBay store: [https://www.ebay.co.uk/str/thehedgehogman](https://www.ebay.co.uk/str/thehedgehogman)   <--- noticed their original eBay store name was "the hedgehog man" and if you look at the memory I bought: [https://www.ebay.co.uk/itm/115878327306](https://www.ebay.co.uk/itm/115878327306) it has a little Hedgehog warranty sticker on it. A flicker from the past when the company was smaller? Love it ;)

@MAFoElffen regarding my previous comment about reading stuff on other community forums, it was TrueNAS... I know this because I was Googling yesterday how to remove the L2ARC and SLOG before speed testing and upgrading and I came across this: [https://www.truenas.com/community/threads/can-i-detach-and-remove-l2arc-drive.11319/#post-55379](https://www.truenas.com/community/threads/can-i-detach-and-remove-l2arc-drive.11319/#post-55379) fairly sure it was this exact user I saw years back who said some odd things about ECC. My experience has certainly not been that the L2ARC hasn't helped. I can currently skip around in a 4K movie as much as I want and it's _instant_!

---

### Post by tkae-lp on 2023-12-07
Now up and running with 128G. Hurrah! When I first put them in, slots D1 and D2 showed as empty. I've spent the best part of 2 hours repositioning modules and scratching my head. The solution turned out to be a CMOS reset using the on board jumper. Voila!

```
               total        used        free      shared  buff/cache   available
Mem:       131819880     8880640   115036456       33996     7902784   121688756
Swap:       12581884           0    12581884

```

So I'll continue to monitor this for a while, but to be honest I think the many upgrades have either:

1. Solved it
2. Masked it to the extent that isn't not really an annoyance any more

I am still absolutely perplexed as to why this only started on Jammy though.

I've certainly enjoyed this and learned a lot. Thanks both for your input and help :)

---

### Post by #&amp;thj^% on 2023-12-07
Nice and sorry I missed your question in post#47 "So what is your minimum ARC setting?"
Nothing fancy yet, until after the first of year...(I'm building a new machine) And I'm going with a Intel i9 CPU
but just a quick view:
```
 cat /proc/spl/kstat/zfs/arcstats |grep size
size                            4    5680436736
compressed_size                 4    4943594496
uncompressed_size               4    7000697344
overhead_size                   4    426235904
hdr_size                        4    27463760
data_size                       4    4932078080
metadata_size                   4    437752320
dbuf_size                       4    50705984
dnode_size                      4    116633520
bonus_size                      4    93691328
anon_size                       4    211968
mru_size                        4    4142923776
mru_ghost_size                  4    0
mfu_size                        4    1226694656
mfu_ghost_size                  4    0
uncached_size                   4    0
l2_prefetch_asize               4    0
l2_mru_asize                    4    0
l2_mfu_asize                    4    0
l2_bufc_data_asize              4    0
l2_bufc_metadata_asize          4    0
l2_size                         4    0
l2_asize                        4    0
l2_hdr_size                     4    0
l2_log_blk_avg_asize            4    0
l2_log_blk_asize                4    0
l2_rebuild_size                 4    0
l2_rebuild_asize                4    0
arc_raw_size                    4    0
abd_chunk_waste_size            4    22111744

```
We had a good time as well. ;)

---

### Post by MAFoElffen on 2023-12-07
Glad everything is going along well!

Sorry that I have been elsewhere committed on trying to get some upstream ZFS patches and upgrades down to us peons. LOL. Everything is moving along on that front as of yesterday. Then today I had a regiment of doctors appointments at The Veterans Administration. Happy to be home and caught up!

Yes, looking at the stats looks like it hangs around 31 GB's and the disk speeds are about twice of what they are rated for, for their sustained stats. I haven't heard anything yet on if you are still getting any intermittent issues was the system dragging, nor periods of buffering on reads. Crossing fingers. 

Yes, I am very happy with those Ceacent Bifurcation cards. That same card sells retail here in the states for over $450 on Amazon.

---

### Post by tkae-lp on 2023-12-08
> **1fallen said:**
> Nice and sorry I missed your question in post#47 "So what is your minimum ARC setting?"

No worries :) thanks for posting the stats, I must admit until I started this thread I was unaware you could tweak ZFS so much.

> **1fallen said:**
> And I'm going with a Intel i9 CPU

Nice! My Xeon is getting on now (not that it really makes a difference for what I use it for). Well, so is the whole box, but it's still serving me well. I'd be very interested to look at something ARM next time, but I still think at this point life is easier with X64.

We got quite lucky with a lot of the stuff in this build. The drives for example were half price for externals, so we shucked them (that won't ever change), but the board was on massive promo and was about £100 off, and the Xeon was through a friend for about £400. I doubt that'll happen next time round. I think I remember looking up the price at the time and the E5-2695v3 was about £2000, and they're still about £500 now. That part of my system certainly doesn't struggle lol I barely ever see my CPU graph:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293174&stc=1[/IMG]

> **MAFoElffen said:**
> Glad everything is going along well!

Thanks, it certainly appears to be.

> **MAFoElffen said:**
> Sorry that I have been elsewhere  committed on trying to get some upstream ZFS patches and upgrades down  to us peons. LOL. Everything is moving along on that front as of  yesterday. Then today I had a regiment of doctors appointments at The  Veterans Administration. Happy to be home and caught up!

No  need to apologise, we all have lives outside of the internet (well  almost ;)) I totally appreciate you guys spending your free time to come  and help me out so really no need to worry about other more important  stuff taking priority. I hope your health is well. :)

> **MAFoElffen said:**
> Yes,  looking at the stats looks like it hangs around 31 GB's and the disk  speeds are about twice of what they are rated for, for their sustained  stats. I haven't heard anything yet on if you are still getting any  intermittent issues was the system dragging, nor periods of buffering on  reads. Crossing fingers.

So far so good, we're still performing well:

```
/mnt/Tank  # cd /mnt/Tank && fio --name TEST --eta-newline=5s  --filename=temp.file --rw=write --size=2g --io_size=10g  --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32  --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1572742: Fri Dec  8 09:12:02 2023
  write: IOPS=1257, BW=1258MiB/s (1319MB/s)(10.0GiB/8141msec); 0 zone resets
    slat (usec): min=188, max=1198, avg=334.08, stdev=195.50
    clat (usec): min=2, max=4693.2k, avg=24564.51, stdev=257303.30
     lat (usec): min=245, max=4693.4k, avg=24898.99, stdev=257302.74
    clat percentiles (msec):
     |  1.00th=[    7],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    8], 60.00th=[    8],
     | 70.00th=[    9], 80.00th=[   12], 90.00th=[   17], 95.00th=[   31],
     | 99.00th=[   31], 99.50th=[   31], 99.90th=[ 4665], 99.95th=[ 4665],
     | 99.99th=[ 4665]
   bw (  MiB/s): min=  982, max= 4092, per=100.00%, avg=2848.29, stdev=1209.82, samples=7
   iops        : min=  982, max= 4092, avg=2848.29, stdev=1209.82, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 250=0.01%, 500=0.05%, 750=0.04%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 2=0.16%, 4=0.32%, 10=76.14%, 20=14.95%, 50=7.94%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=888, max=888, avg=888.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  892],  5.00th=[  892], 10.00th=[  892], 20.00th=[  892],
     | 30.00th=[  892], 40.00th=[  892], 50.00th=[  892], 60.00th=[  892],
     | 70.00th=[  892], 80.00th=[  892], 90.00th=[  892], 95.00th=[  892],
     | 99.00th=[  892], 99.50th=[  892], 99.90th=[  892], 99.95th=[  892],
     | 99.99th=[  892]
  cpu          : usr=5.91%, sys=85.71%, ctx=3106, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1258MiB/s (1319MB/s), 1258MiB/s-1258MiB/s (1319MB/s-1319MB/s), io=10.0GiB (10.7GB), run=8141-8141msec
-------------------------------------------------------------------------------------------------------------------------------------------------
/mnt/Tank  # cd /mnt/Tank && fio --name TEST --eta-newline=5s  --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k  --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1  --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2964MiB/s][r=2964 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1619419: Fri Dec  8 09:12:24 2023
  read: IOPS=2868, BW=2868MiB/s (3008MB/s)(10.0GiB/3570msec)
    slat (usec): min=278, max=1144, avg=345.81, stdev=47.78
    clat (usec): min=2, max=31762, avg=10693.20, stdev=1327.98
     lat (usec): min=325, max=32908, avg=11039.37, stdev=1363.23
    clat percentiles (usec):
     |  1.00th=[ 6849],  5.00th=[10290], 10.00th=[10290], 20.00th=[10421],
     | 30.00th=[10421], 40.00th=[10421], 50.00th=[10421], 60.00th=[10552],
     | 70.00th=[10552], 80.00th=[10683], 90.00th=[12256], 95.00th=[12387],
     | 99.00th=[13829], 99.50th=[15401], 99.90th=[26870], 99.95th=[29230],
     | 99.99th=[31327]
   bw (  MiB/s): min= 2294, max= 2966, per=99.71%, avg=2860.00, stdev=249.92, samples=7
   iops        : min= 2294, max= 2966, avg=2860.00, stdev=249.92, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.02%
  lat (msec)   : 2=0.14%, 4=0.28%, 10=0.87%, 20=98.31%, 50=0.23%
  cpu          : usr=0.87%, sys=99.02%, ctx=4, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2868MiB/s (3008MB/s), 2868MiB/s-2868MiB/s (3008MB/s-3008MB/s), io=10.0GiB (10.7GB), run=3570-3570msec

/mnt/Tank  # cd /mnt/Tank && fio --name TEST --eta-newline=5s  --filename=temp.file --rw=write --size=2g --io_size=10g  --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32  --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1622239: Fri Dec  8 09:14:25 2023
  write: IOPS=1362, BW=1363MiB/s (1429MB/s)(10.0GiB/7515msec); 0 zone resets
    slat (usec): min=179, max=1725, avg=333.84, stdev=187.65
    clat (usec): min=2, max=4067.1k, avg=22686.77, stdev=222931.92
     lat (usec): min=245, max=4067.4k, avg=23021.07, stdev=222931.37
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    8], 60.00th=[    9],
     | 70.00th=[    9], 80.00th=[   13], 90.00th=[   18], 95.00th=[   28],
     | 99.00th=[   29], 99.50th=[   30], 99.90th=[ 4077], 99.95th=[ 4077],
     | 99.99th=[ 4077]
   bw (  MiB/s): min=  390, max= 4092, per=100.00%, avg=2541.00, stdev=1361.69, samples=8
   iops        : min=  390, max= 4092, avg=2541.00, stdev=1361.69, samples=8
  lat (usec)   : 4=0.05%, 250=0.01%, 500=0.05%, 750=0.06%, 1000=0.04%
  lat (msec)   : 2=0.21%, 4=0.38%, 10=74.99%, 20=16.21%, 50=7.71%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=738, max=738, avg=738.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  740],  5.00th=[  740], 10.00th=[  740], 20.00th=[  740],
     | 30.00th=[  740], 40.00th=[  740], 50.00th=[  740], 60.00th=[  740],
     | 70.00th=[  740], 80.00th=[  740], 90.00th=[  740], 95.00th=[  740],
     | 99.00th=[  740], 99.50th=[  740], 99.90th=[  740], 99.95th=[  740],
     | 99.99th=[  740]
  cpu          : usr=6.02%, sys=83.98%, ctx=3257, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1363MiB/s (1429MB/s), 1363MiB/s-1363MiB/s (1429MB/s-1429MB/s), io=10.0GiB (10.7GB), run=7515-7515msec
-------------------------------------------------------------------------------------------------------------------------------------------------
/mnt/Tank  # cd /mnt/Tank && fio --name TEST --eta-newline=5s  --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k  --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1  --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2933MiB/s][r=2933 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=1668716: Fri Dec  8 09:14:33 2023
  read: IOPS=2846, BW=2846MiB/s (2984MB/s)(10.0GiB/3598msec)
    slat (usec): min=285, max=988, avg=348.74, stdev=41.14
    clat (usec): min=2, max=28229, avg=10783.02, stdev=1234.91
     lat (usec): min=327, max=29219, avg=11132.11, stdev=1263.83
    clat percentiles (usec):
     |  1.00th=[ 6783],  5.00th=[10421], 10.00th=[10421], 20.00th=[10552],
     | 30.00th=[10552], 40.00th=[10552], 50.00th=[10552], 60.00th=[10683],
     | 70.00th=[10683], 80.00th=[10683], 90.00th=[12387], 95.00th=[12387],
     | 99.00th=[13566], 99.50th=[15139], 99.90th=[24249], 99.95th=[26346],
     | 99.99th=[27919]
   bw (  MiB/s): min= 2320, max= 2966, per=99.72%, avg=2838.00, stdev=230.41, samples=7
   iops        : min= 2320, max= 2966, avg=2838.00, stdev=230.41, samples=7
  lat (usec)   : 4=0.04%, 20=0.01%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.88%, 20=98.33%, 50=0.21%
  cpu          : usr=0.75%, sys=99.14%, ctx=5, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2846MiB/s (2984MB/s), 2846MiB/s-2846MiB/s (2984MB/s-2984MB/s), io=10.0GiB (10.7GB), run=3598-3598msec
```

Certainly,  I'm not having any issues with media playback anymore - which is the  purpose of this box and the reason why it was so awful. Skipping forward  half an hour and just loading anything (even old cartoons in 480p) was  just painful. I can still jump around in 4K with this as it is now and  it's instantly where you want it. It's bliss! ;)

It was so nice to do a scrub that took less than 24 hours!

```
  scan: scrub repaired 0B in 07:03:04 with 0 errors on Fri Dec  8 03:03:07 2023

```

> **MAFoElffen said:**
> Yes, I am very happy with those Ceacent  Bifurcation cards. That same card sells retail here in the states for  over $450 on Amazon.

Wow... yeah I often cringe when I am  forced to buy something on Amazon because I need it yesterday and I  check on Ali and it's a fraction of the cost. Even with UK VAT, it's  still a great source. I sometimes think I am in the wrong line of work  and should just quit my day job and drop ship stuff. Take the adapter  for the NVMe for example: £6 on Amazon, £2.35 on Ali free shipping. If I  could have waited, I could have got it from Ali. I know that's only  pocket change so doesn't matter so much, but a lot of my equipment I've  got on Ali and saved a ton. My solder station, air station, digital  microscope, components, HDMI switches, Class D amps.. it's all on Amazon  but 4 times the price. I'll keep that Bifurcation in my basket and will  probably treat the server to an OS drive upgrade in the new year. I can  ditch the SATA SSD and maybe pop another NVMe in for the OS.

> **MAFoElffen said:**
> upstream ZFS patches and upgrades down to us peons

Not  anything to do with the block clone bug by any chance? Well done to the  Gentoo guys for spotting that one, and thanks to you for making sure us peons have upstream patches! ;) I'm so pleased OpenZFS is a thing  now - and a thing with a lot of momentum. When I looked at TrueNAS years and years ago, I never would have  imagined that the ZFS community would have come together like this...  even when ZoL took off, it was kinda them and us lol. This really is a great example of open source unification. Too much forking happens and we need to stop forking doing it! ;)

There's even this  now: [https://github.com/openzfsonwindows](https://github.com/openzfsonwindows) like... wow.. this has to be one of the most universal filesystems at this point bar maybe FAT? <3

All we need now is pool shrinking and heterogeneous drive support *cough cough* .... Mr Overstreet has it.... *cough cough* ;) [URL="https://www.reddit.com/r/bcachefs/comments/vfbgnl/does_bcachefs_support_dynamic_pool_resizing_and/"]https://www.reddit.com/r/bcachefs/comments/vfbgnl/does_bcachefs_support_dynamic_pool_resizing_and/
[/URL]
Edit: What the?! I edited to include the CPU graph and got a message to say I had too many images... apparently smileys count, so I had to remove one of them! lol

---

### Post by tkae-lp on 2023-12-08
Thinking a bit about why I don't see the issue now, or more importantly what has changed between Bionic and Jammy - I can think of nothing else other than perhaps some other app such as one of the docker containers or Firefox is a bit more thirsty now and this was pushing it just over the edge. With an ARC for this pool size that wants to be at 31GB, and only having 32GB at the time, things were obviously tighter. Bionic definitely made use of swap a lot more, where as obviously right now I see no usage. 

My docker apps are using about 1GB, and Firefox now it's been let loose is swallowing up 12GB lol pretty sure it didn't consume that much before it was a snap! Just saying, Canonical ;)

---

### Post by MAFoElffen on 2023-12-08
Yes. Form what you shold the change could have been just Firefox switching from Apt installed to Snap installed, using more memory... and that pushing you over your machine's resource limits.

Like both 1fallen and I said, we say better days with ZFS on 22.04. Yes, we originally filed things on Feature@block_cloning, then grouped a few bugs as duplicate of another bug, which expanded that grouped it into "Multiple Data Corruption Issues in ZFS", which pushed releases of zfs-linux 2.2.2 and 2.1.14 to get back-backed back through xenial... The orignal problem is actually a problem in the code of 'cp' (copy), which go back to 2012... 1fallen and I have been testing/verifying the release/patches since it got built from the Proposed Repo, so it can get pushed to main. We have been busy with that and with a few other ZFS related packages that we have bugs filed on. I found a few problems so far, but no show stoppers.

It's not perfect (Yet, LOL), but we are trying our best to get it how we want, without problems to the other Users.

---

### Post by tkae-lp on 2023-12-08
> **MAFoElffen said:**
> Yes. Form what you shold the change could have been just Firefox switching from Apt installed to Snap installed, using more memory... and that pushing you over your machine's resource limits.

I've checked again just now and we're still fine so I think we can probably accept this as the answer and mark this as solved. So in short: ARC was responsible - but because of resource limits caused by Firefox. Solution was more RAM (and the L2ARC/SLOG has also helped). 

> **MAFoElffen said:**
>  Like both 1fallen and I said, we say better days with ZFS on 22.04. Yes, we originally filed things on Feature@block_cloning, then grouped a few bugs as duplicate of another bug, which expanded that grouped it into "Multiple Data Corruption Issues in ZFS", which pushed releases of zfs-linux 2.2.2 and 2.1.14 to get back-backed back through xenial... The orignal problem is actually a problem in the code of 'cp' (copy), which go back to 2012... 1fallen and I have been testing/verifying the release/patches since it got built from the Proposed Repo, so it can get pushed to main. We have been busy with that and with a few other ZFS related packages that we have bugs filed on. I found a few problems so far, but no show stoppers. 

Wow, you've both been busy - thanks for your efforts in your spare time to make it awesome for the rest of us.

> **MAFoElffen said:**
> It's not perfect (Yet, LOL), but we are trying our best to get it how we want, without problems to the other Users.

Again, thank you. I really do love my ZFS array. It's been great learning more about it and I look forward to what the future may bring ;)

---

### Post by tkae-lp on 2023-12-10
Uh oh..... A 1080p film buffered so I checked fio and.....


```
cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][11.7%][eta 00m:53s]
Jobs: 1 (f=1): [R(1)][20.0%][eta 00m:48s]                        
Jobs: 1 (f=1): [R(1)][30.0%][r=14.0MiB/s][r=14 IOPS][eta 00m:42s] 
Jobs: 1 (f=1): [R(1)][40.0%][eta 00m:36s]                        
Jobs: 1 (f=1): [R(1)][50.0%][r=17.0MiB/s][r=17 IOPS][eta 00m:30s] 
Jobs: 1 (f=1): [R(1)][60.0%][eta 00m:24s]                        
Jobs: 1 (f=1): [R(1)][70.0%][r=56.1MiB/s][r=56 IOPS][eta 00m:18s] 
Jobs: 1 (f=1): [R(1)][80.0%][eta 00m:12s]                        
Jobs: 1 (f=1): [R(1)][90.0%][r=45.0MiB/s][r=45 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [R(1)][100.0%][r=208MiB/s][r=208 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=4005355: Mon Dec 11 04:40:59 2023
  read: IOPS=26, BW=26.4MiB/s (27.7MB/s)(1585MiB/60001msec)
    slat (usec): min=317, max=2689.8k, avg=37848.64, stdev=238673.28
    clat (usec): min=5, max=8793.9k, avg=1089114.47, stdev=1460097.37
     lat (usec): min=918, max=8803.7k, avg=1126963.97, stdev=1501904.65
    clat percentiles (msec):
     |  1.00th=[   13],  5.00th=[   26], 10.00th=[   29], 20.00th=[   30],
     | 30.00th=[   32], 40.00th=[   54], 50.00th=[  102], 60.00th=[ 1519],
     | 70.00th=[ 1569], 80.00th=[ 1703], 90.00th=[ 3104], 95.00th=[ 4212],
     | 99.00th=[ 6208], 99.50th=[ 7483], 99.90th=[ 8792], 99.95th=[ 8792],
     | 99.99th=[ 8792]
   bw (  KiB/s): min= 4096, max=376832, per=100.00%, avg=76231.11, stdev=87574.95, samples=36
   iops        : min=    4, max=  368, avg=74.44, stdev=85.52, samples=36
  lat (usec)   : 10=0.06%, 1000=0.06%
  lat (msec)   : 2=0.06%, 4=0.19%, 10=0.44%, 20=0.76%, 50=36.15%
  lat (msec)   : 100=11.80%, 250=4.98%, 500=1.64%, 1000=1.96%, 2000=23.97%
  lat (msec)   : >=2000=17.92%
  cpu          : usr=0.01%, sys=2.61%, ctx=354, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.3%, 8=0.5%, 16=1.0%, 32=98.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=99.9%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=1585,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=26.4MiB/s (27.7MB/s), 26.4MiB/s-26.4MiB/s (27.7MB/s-27.7MB/s), io=1585MiB (1662MB), run=60001-60001msec

```

@1fallen @MAFoElffen

Bummer ;( Removing the marked as solved. I was premature in celebrating a victory....Gotta turn in. Will post back soon.

---

### Post by tkae-lp on 2023-12-11
It's picked up a bit:

```
cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][75.0%][r=2963MiB/s][r=2963 IOPS][eta 00m:02s]
TEST: (groupid=0, jobs=1): err= 0: pid=196597: Mon Dec 11 09:21:27 2023
  read: IOPS=1506, BW=1507MiB/s (1580MB/s)(10.0GiB/6797msec)
    slat (usec): min=268, max=782832, avg=660.75, stdev=12213.28
    clat (usec): min=2, max=2603.3k, avg=20465.45, stdev=126192.98
     lat (usec): min=325, max=2605.1k, avg=21126.61, stdev=128817.68
    clat percentiles (msec):
     |  1.00th=[    7],  5.00th=[   11], 10.00th=[   11], 20.00th=[   11],
     | 30.00th=[   11], 40.00th=[   11], 50.00th=[   11], 60.00th=[   11],
     | 70.00th=[   12], 80.00th=[   13], 90.00th=[   13], 95.00th=[   14],
     | 99.00th=[   87], 99.50th=[  384], 99.90th=[ 2299], 99.95th=[ 2601],
     | 99.99th=[ 2601]
   bw (  MiB/s): min=    2, max= 2968, per=100.00%, avg=1557.00, stdev=1310.19, samples=12
   iops        : min=    2, max= 2968, avg=1557.00, stdev=1310.19, samples=12
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.02%
  lat (msec)   : 2=0.14%, 4=0.27%, 10=0.87%, 20=94.75%, 50=1.11%
  lat (msec)   : 100=1.82%, 250=0.35%, 500=0.13%, 750=0.04%, 1000=0.05%
  lat (msec)   : 2000=0.11%, >=2000=0.21%
  cpu          : usr=0.34%, sys=57.22%, ctx=181, majf=0, minf=8206
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1507MiB/s (1580MB/s), 1507MiB/s-1507MiB/s (1580MB/s-1580MB/s), io=10.0GiB (10.7GB), run=6797-6797msec

```

Writes are still good:

```
cd /mnt/Tank && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=201610: Mon Dec 11 09:22:49 2023
  write: IOPS=1334, BW=1334MiB/s (1399MB/s)(10.0GiB/7676msec); 0 zone resets
    slat (usec): min=198, max=1943, avg=324.27, stdev=162.87
    clat (usec): min=3, max=4324.3k, avg=23173.10, stdev=237065.14
     lat (usec): min=256, max=4324.6k, avg=23497.79, stdev=237064.55
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    9],
     | 30.00th=[    9], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[    9], 80.00th=[   10], 90.00th=[   17], 95.00th=[   26],
     | 99.00th=[   27], 99.50th=[   28], 99.90th=[ 4329], 99.95th=[ 4329],
     | 99.99th=[ 4329]
   bw (  MiB/s): min= 1272, max= 3868, per=100.00%, avg=2848.29, stdev=1026.47, samples=7
   iops        : min= 1272, max= 3868, avg=2848.29, stdev=1026.47, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.36%, 10=79.62%, 20=12.27%, 50=7.06%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=756, max=756, avg=756.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  756],  5.00th=[  756], 10.00th=[  756], 20.00th=[  756],
     | 30.00th=[  756], 40.00th=[  756], 50.00th=[  756], 60.00th=[  756],
     | 70.00th=[  756], 80.00th=[  756], 90.00th=[  756], 95.00th=[  756],
     | 99.00th=[  756], 99.50th=[  756], 99.90th=[  756], 99.95th=[  756],
     | 99.99th=[  756]
  cpu          : usr=5.55%, sys=86.46%, ctx=2541, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1334MiB/s (1399MB/s), 1334MiB/s-1334MiB/s (1399MB/s-1399MB/s), io=10.0GiB (10.7GB), run=7676-7676msec

```

So whatever it is, it's the same as last time. Writes suffer more than reads. :-S

---

### Post by #&amp;thj^% on 2023-12-11
Interesting results, and I find reads are on average fairly close to consistent, but write speeds will vary, depending on a file or what's going on internally with the system.(system services)
Buffering can occur with many reasons.
My /tank/ is on a USB Dock, and not on the Motherboard, and from time to time I see differences with write speeds ie:
```
cd /tank/
I'll cut to the chase here:
Run status group 0 (all jobs):
  WRITE: bw=1915MiB/s (2008MB/s), 1915MiB/s-1915MiB/s (2008MB/s-2008MB/s), io=10.0GiB (10.7GB), run=5347-5347msec
```
```
 zpool list |grep tank
tank    464G  14.3G   450G        -         -     0%     3%  1.00x    ONLINE  -


```
But as i said earlier, if my tank drive is 60% or more is when I see bigger slow writes. But not always...go figure.

---

### Post by tkae-lp on 2023-12-11
> **1fallen said:**
> Interesting results, and I find reads are on average fairly close to consistent, but write speeds will vary, depending on a file or what's going on internally with the system.(system services)
Buffering can occur with many reasons.
My /tank/ is on a USB Dock, and not on the Motherboard, and from time to time I see differences with write speeds ie:
```
cd /tank/
I'll cut to the chase here:
Run status group 0 (all jobs):
  WRITE: bw=1915MiB/s (2008MB/s), 1915MiB/s-1915MiB/s (2008MB/s-2008MB/s), io=10.0GiB (10.7GB), run=5347-5347msec
```
```
df -hT /tank/
Filesystem               Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_t9tvvp zfs   878G  9.1G  869G   2% /

```
But as i said earlier, if my tank drive is 60% or more is when I see bigger slow writes. But not always...go figure.

No I do appreciate at times it will be slower, but did you see the one in the post above (second one up)?

```
Run status group 0 (all jobs):
   READ: bw=26.4MiB/s (27.7MB/s), 26.4MiB/s-26.4MiB/s (27.7MB/s-27.7MB/s), io=1585MiB (1662MB), run=60001-60001msec
```

This is about as slow as it was in the beginning. 

About the percentage used, I was:

```
~ » df -hT /mnt/Tank
Filesystem     Type  Size  Used Avail Use% Mounted on
Tank           zfs    21T   15T  6.4T  69% /mnt/Tank

```

But about a week ago when you first mentioned it, I had a box set prune, so I am currently at:

```
~ » df -hT /mnt/Tank
Filesystem     Type  Size  Used Avail Use% Mounted on
Tank           zfs    21T   12T  8.9T  57% /mnt/Tank

```

So surely this can't be the cause? And why was it fine for a few days? I just don't get it. I'm back to scratching my head. It's something else. The root cause must be something else and the upgrades have just masked it for a bit. I can understand speeds dropping, but 27MB/sec read is not ok lol

Edit:

tons of space for ARC now:

```
arcstat                                                                                                 
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
16:47:02     0     0      0     0    0     0    0     0    0   35G   37G    73G

```

```
options zfs zfs_arc_min=8589934592
options zfs zfs_arc_max=68719476736


```

---

### Post by MAFoElffen on 2023-12-11
Are you using this for anything other than a media server? I mean what other processes are going on when you are watching movies? 

On my workstation, it is dual-boot with Win11 and Ubuntu. I have Plex installed on both OS'es pointing to the same storage, where my media files are. That way my wife can watch movies, no matter what I am doing on that. Watching movies or playing music is just reads.

I thrash that machine. I game on it. I'll be running many KVM VM's doing testing, while doing program compiles... I have visual system monitoring on my desktop, with Conky statuses, and very rarely am I really taxing that i9... Or the disk through-put, or any of my 18 networking devices on it.

There has got to be something going on there, to affect that, that we are not seeing yet. We have checked all the other blocks there.

---

### Post by tkae-lp on 2023-12-11
> **MAFoElffen said:**
> Are you using this for anything other than a media server? I mean what other processes are going on when you are watching movies? 

On my workstation, it is dual-boot with Win11 and Ubuntu. I have Plex installed on both OS'es pointing to the same storage, where my media files are. That way my wife can watch movies, no matter what I am doing on that. Watching movies or playing music is just reads.

I thrash that machine. I game on it. I'll be running many KVM VM's doing testing, while doing program compiles... I have visual system monitoring on my desktop, with Conky statuses, and very rarely am I really taxing that i9... Or the disk through-put, or any of my 18 networking devices on it.

There has got to be something going on there, to affect that, that we are not seeing yet. We have checked all the other blocks there.

This is the thing. This box does pretty much nothing apart from Emby and some dockers that deal with NZB and Torrent and this is what it has done it's entire life without ever having an issue. It doesn't serve a huge SQL DB for example, or run folding at home, or scrub constantly, or have a massive amount of torrents/nzb at any one time (anyway this is irrelevant because they are sent to the 500GB disk first) or idk.... transcode a lot (front ends are Nvidia Shields that can handle most things). 

It's 3 main functions are:

1. Host music, movies and TV and serve via Emby docker
2. Use ZFS to maintain data quality
3. Use a few other dockers that deal with sorting and acquisition like radarr, sonarr, prowlarr, VPN, deluge, sabnzbd etc.

With that said, ALL these things were running with Bionic. Firefox is always open chewing up memory, but there's plenty free now and again, the firefox behaviour hasn't changed since Bionic. I literally installed Jammy and used Docker compose to fire up my containers and snap to install firefox. Install ksplice and a few other essentials and that's it.

If I thrashed this, I could understand if ground to a halt. This is something else.

---

### Post by MAFoElffen on 2023-12-11
I'm thinking about if you installed sysstat and did something like this:
```

# syntax: pidstat -d <interval> <times>
sudo pidstat -d 30 59 | tee -a $HOME/pidstats.log

```
Then it might track some of those...

And if yo added that to a cron job to run every [s]10 minutes[/s] hour or so, then it might get fairly large over a few days.

Here is a snip from the output of that
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo pidstat -d 30 100
Linux 6.2.0-37-generic (Mikes-ThinkPad-T520)     12/11/2023     _x86_64_    (8 CPU)

12:05:33 PM   UID       PID   kB_rd/s   kB_wr/s kB_ccwr/s iodelay  Command
12:06:03 PM     0      1169      0.00      4.93      0.00       0  systemd-journal
12:06:03 PM     0      3181      0.00      0.02      0.00       0  NetworkManager
12:06:03 PM   104      3210      0.00      0.00      0.00       0  rsyslogd
12:06:03 PM     0      3224      0.21      0.00      0.00       0  snapd
12:06:03 PM     0      3821    562.40      0.00      0.00       0  libvirtd
12:06:03 PM  1000      6222      3.37      0.00      0.00       0  gnome-shell
12:06:03 PM  1000      6824      0.29      0.00      0.00       0  xdg-desktop-por
12:06:03 PM  1000    205044    230.79      2.60      0.00       0  firefox
12:06:03 PM  1000    211290      0.67      0.00      0.00       0  Isolated Web Co
12:06:03 PM  1000    350276      1.43      0.00      0.00       0  Isolated Servic
12:06:03 PM  1000    355514      5.06      0.00      0.00       0  Web Content

##... <<On Dang. That is every 30 seconds for about an hour or so. Maybe run once every hour and limit it to 30 seconds & 60 times ?

12:54:03 PM   UID       PID   kB_rd/s   kB_wr/s kB_ccwr/s iodelay  Command
12:54:33 PM     0       437      4.27      0.00      0.00       0  z_rd_int_0
12:54:33 PM     0      1169      0.00     14.93      0.00       0  systemd-journal
12:54:33 PM   104      3210      0.00      0.04      0.00       0  rsyslogd
12:54:33 PM     0      3439     16.06      0.00      0.00       0  canonical-livep
12:54:33 PM     0      3821    563.33      0.00      0.00       0  libvirtd
12:54:33 PM  1000      6222      3.38      0.00      0.00       0  gnome-shell
12:54:33 PM  1000      9431    207.62      0.00      0.00       0  update-notifier
12:54:33 PM  1000    205044     65.84      0.31      0.00       0  firefox
12:54:33 PM     0    353749    154.20      0.00      0.00       0  kworker/u16:4-events_unbound
12:54:33 PM  1000    374977      6.50      0.00      0.00       0  Isolated Servic

12:54:33 PM   UID       PID   kB_rd/s   kB_wr/s kB_ccwr/s iodelay  Command
12:55:03 PM     0      1169      0.00      5.60      0.00       0  systemd-journal
12:55:03 PM     0      3178      5.42      0.00      0.00       0  cron
12:55:03 PM   104      3210      0.00      0.01      0.00       0  rsyslogd
12:55:03 PM     0      3821    563.33      0.00      0.00       0  libvirtd
12:55:03 PM  1000      6222      3.38      0.00      0.00       0  gnome-shell
12:55:03 PM  1000    205044      5.34     24.31      0.00       0  firefox
12:55:03 PM     0    353749      0.00      6.67      0.00       0  kworker/u16:4-iwlwifi
12:55:03 PM     0    353752      0.00      8.00      0.00       0  kworker/u16:7-events_power_efficient

12:55:03 PM   UID       PID   kB_rd/s   kB_wr/s kB_ccwr/s iodelay  Command
12:55:33 PM     0      3821    563.33      0.00      0.00       0  libvirtd
12:55:33 PM  1000      6222      3.38      0.00      0.00       0  gnome-shell
12:55:33 PM  1000    205044      6.63      0.13      0.00       0  firefox
12:55:33 PM     0    351618      0.00      5.60      0.00       0  kworker/u16:3-iwlwifi

Average:      UID       PID   kB_rd/s   kB_wr/s kB_ccwr/s iodelay  Command
Average:        0       437      0.64      0.00      0.00       0  z_rd_int_0
Average:        0       438      0.38      0.00      0.00       0  z_rd_int_1
Average:        0       543      0.07      0.00      0.00       0  txg_sync
Average:        0      1169      0.01      3.18      0.00       0  systemd-journal
Average:        0      3178      0.42      0.00      0.00       0  cron
Average:        0      3181      0.00      0.00      0.00       0  NetworkManager
Average:      104      3210      0.00      0.00      0.00       0  rsyslogd
Average:        0      3214      0.00      0.00      0.00       0  smartd
Average:        0      3224      0.15      0.00      0.00       0  snapd
Average:        0      3426      0.00      0.00      0.00       0  cupsd
Average:        0      3439      2.66      0.00      0.00       0  canonical-livep
Average:        0      3821    563.32      0.00      0.00       0  libvirtd
Average:        0      4999      0.00      0.00      0.00       0  nmbd
Average:        0      5085      0.01      0.00      0.00       0  samba-bgqd
Average:        0      5495      0.00      0.00      0.00       0  upowerd
Average:     1000      5904      0.00      0.00      0.00       0  systemd
Average:     1000      6222      3.40      0.00      0.00       0  gnome-shell
Average:     1000      6824      0.01      0.00      0.00       0  xdg-desktop-por
Average:     1000      7465      0.23      0.00      0.00       0  snap
Average:     1000      9431      3.92      0.00      0.00       0  update-notifier
Average:     1000     88253      0.00      0.00      0.00       0  mission-control
Average:     1000    124715      0.02      0.00      0.00       0  gnome-terminal-
Average:     1000    205044    137.25     52.22      0.00       0  firefox
Average:     1000    205412      0.03      0.00      0.00       0  WebExtensions
Average:     1000    205608      0.00      0.00      0.00       0  Isolated Web Co
Average:     1000    210615      0.00      0.00      0.00       0  Isolated Web Co
Average:     1000    211126      0.35      0.00      0.00       0  Isolated Web Co
Average:     1000    211290      0.01      0.00      0.00       0  Isolated Web Co
Average:     1000    216895      0.03      0.00      0.00       0  Isolated Web Co
Average:     1000    232100      0.20      0.00      0.00       0  Isolated Web Co
Average:     1000    232736      0.01      0.00      0.00       0  Isolated Web Co
Average:     1000    330037      0.02      0.00      0.00       0  Isolated Web Co
Average:     1000    340748      0.35      0.00      0.00       0  Isolated Web Co
Average:     1000    345265      0.02      0.00      0.00       0  Isolated Web Co
Average:     1000    347837      0.03      0.00      0.00       0  Isolated Web Co
Average:     1000    347908      0.12      0.00      0.00       0  Isolated Web Co
Average:        0    351618      4.63      1.15      0.00       0  kworker/u16:3-iwlwifi
Average:        0    353749      2.78      1.01      0.00       0  kworker/u16:4-events_unbound
Average:        0    353752      6.93      0.62      0.00       0  kworker/u16:7-iwlwifi
Average:     1000    355514      0.27      0.00      0.00       0  Isolated Web Co

```

---

### Post by tkae-lp on 2023-12-12
Sorry for the delay. The last few days have been hectic.

I ran fio and pidstat just now and was just going to post to say I am not currently in a slow down and post a snippet of pidstat BUT THEN my whole system froze! Mouse cursor could move, but no XFCE element would respond, couldn't get to another terminal to go init3 and return to init5, couldn't login via ssh, 3 x Control + Alt + Delete didn't reboot, had to hit the reboot button on the board!

This happened a few weeks ago (before upgrades) so that rules those out... I didn't think too much of it as it never happened before (we've had a LOT of bad weather here so assumed it was a power fluctuation). But now it's happened again... here is the pidstat snippet: [https://paste.ubuntu.com/p/mHHcMwQpBj/](https://paste.ubuntu.com/p/mHHcMwQpBj/)

I started to wonder if perhaps the OS SSD is faulty. I had originally checked the SMART for the array, but not the OS SSD, and sure enough I see this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293191&stc=1[/IMG]

But, the last error occurred 3 months ago as the life hours is now:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293192&stc=1[/IMG]

So I guess the next thing is replace that? What I don't get is that the last error was 3 months ago. Nothing since. This does seem to be looking like the likely culprit now though, doesn't it? I just would have expected an error to show 30 mins ago?

Edit: I can get an Evo 870 500GB SATA SSD here tomorrow. Tbh, if this Sandisk is failing, that's the 2nd one I've had in 2 years. I think I'll stick with Samsung from now on... Never had an issues with their NVMes!

---

### Post by #&amp;thj^% on 2023-12-12
> **tkae-lp said:**
> Sorry for the delay. The last few days have been hectic.

 This does seem to be looking like the likely culprit now though, doesn't it? I just would have expected an error to show 30 mins ago?
That seems like a logical guess, but other things were happening before this, Right?
Dang i hate to post and run, but I've got family in town to-nite.
Hopefully  MAFoElffen will see this. I'm starting to think hardware though, or a bad driver?? Just thinking out loud.

---

### Post by tkae-lp on 2023-12-12
> **1fallen said:**
> That seems like a logical guess, but other things were happening before this, Right?
Dang i hate to post and run, but I've got family in town to-nite.
Hopefully  MAFoElffen will see this. I'm starting to think hardware though, or a bad driver?? Just thinking out loud.

No worries - as I've said all along, I appreciate your help - enjoy your family time!

Yes, I would say the problem with ZFS slowing down has been for the past 3 or so months since Jammy. The 1st freeze was only a few weeks ago.

Edit: I just read that ATA errors can be caused by bad SATA cables, but I have just replaced those. So I suppose, whilst not impossible, we can probably rule those out. The chances of me replacing 1 bad SATA cable with another bad SATA cable on just one (the same) drive are pretty slim!

---

### Post by MAFoElffen on 2023-12-12
I would have the same guess. You just replaced the cables.

ZFS "zpool status" logs and shows read, write and cksum errors. It hasn't been showing those has it?

I tend to pay more for Samsung branded because I trust them.

I keep having errors with 1 Samsung EVO 870 drive which does not show any SMART Errors, and corrects itself with a scrubs... When i first upgraded that array from 4 disks to 5 disks, I replaced that that new SSD 3 times... thinking I just got a bad SSD... and it still goes offline very once in a blue moon. Though inconvenient, I just clear & scrub it and it shows fine and continues on. I still have not tracked down the why of that on mine. But it now only happens about once every 5 months or so. I haven't looked very hard, as it comes back up. 

The funny thing is, it's the 5th disk in a 5 (SSD) disk RAIDZ2 array and the performance is so fast, with 1 disk down in that array, I don't even notice it is degraded until  do a "status" on it.

---

### Post by tkae-lp on 2023-12-12
> **MAFoElffen said:**
> I would have the same guess. You just replaced the cables.

ZFS "zpool status" logs and shows read, write and cksum errors. It hasn't been showing those has it?

I tend to pay more for Samsung branded because I trust them.

I keep having errors with 1 Samsung EVO 870 drive which does not show any SMART Errors, and corrects itself with a scrubs... When i first upgraded that array from 4 disks to 5 disks, I replaced that that new SSD 3 times... thinking I just got a bad SSD... and it still goes offline very once in a blue moon. Though inconvenient, I just clear & scrub it and it shows fine and continues on. I still have not tracked down the why of that on mine. But it now only happens about once every 5 months or so. I haven't looked very hard, as it comes back up. 

The funny thing is, it's the 5th disk in a 5 (SSD) disk RAIDZ2 array and the performance is so fast, with 1 disk down in that array, I don't even notice it is degraded until  do a "status" on it.

Interesting with your 870 experience... I am still inclined to go with it though, I already pushed the button so it will arrive tomorrow but I won't get time to install until Thu/Fri-ish.

With regards to the zpool output, no, there has never been anything amiss there - output taken now (and I do check regularly):

```
/mnt/Tank # zpool status Tank
  pool: Tank
 state: ONLINE
  scan: scrub repaired 0B in 07:03:04 with 0 errors on Fri Dec  8 03:03:07 2023
config:

    NAME                                                                STATE     READ WRITE CKSUM
    Tank                                                                ONLINE       0     0     0
      raidz2-0                                                          ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX                                 ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W53XXXXX-part2  ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W53XXXXX-part1  ONLINE       0     0     0

errors: No known data errors
```

As you can see, I did a scrub just after I thought we'd cracked it. Nothing flagged. 

SSD arrives tomorrow.. What do I install on it? You think I should still go with Jammy? Mixing it up at this point removes our control from this experiment.... So I guess Jammy it is. Same packages etc. Whenever I do something I always take notes, so I am sure I can replicate the system I have here.

---

### Post by MAFoElffen on 2023-12-12
> **tkae-lp said:**
> Whenever I do something I always take notes, so I  am sure I can replicate the system I have here.
I do the same (with install recipes) of all the commands I used to create someting, and the output, so I have a record of, and can track how it was, and changes I made to things.

---

### Post by tkae-lp on 2023-12-13
> **MAFoElffen said:**
> all the commands I used to create someting, and the output

I do the same with commands - I don't do output though. Here's my 22.04 just in case you happen to spot any glaring errors before I reinstall, SSD is here. Will probably be Friday I get round to it. :)

```
Installing Ubuntu Server 22.04 and very minimal XFCE Environment
----------------------------------------------------------------

1. Grab Ventoy key drive and boot from the Ubuntu server ISO

2. When prompted select Ubuntu Server not Minimalised

3. Partition disks if needed and run through the rest of the installation

Note: If existing home partition, remember not to format and just assign /home

4. On first boot, login with your user and disable cloud-init:

sudo touch /etc/cloud/cloud-init.disabled

5. Edit netplan config: sudo nano /etc/netplan/00-installer-config.yaml to include:

optional: true

ie:

network:
  ethernets:
    enp0s25:
      optional: true
      dhcp4: true
    enp5s0:
      optional: true
      dhcp4: true
  version: 2


Note: optional: true prevents boot delays

6. Save the file and rename it:

sudo mv /etc/netplan/00-installer-config.yaml /etc/netplan/00-netcfg.yaml

Then:

netplan generate
netplan apply

If it moans about permissions do:

chmod 0600 /etc/netplan/00-netcfg.yaml

7. Install some basics: sudo apt install htop curl xfce4 xfce4-goodies xfce4-notes-plugin zathura apt-transport-https ca-certificates avahi-daemon qalculate-gtk

8. hddtemp doesn't seem to work with the XFCE4 sensor plugin. The preferred method for 22.04 seems to be to use hwmon via lm-sensors.

sudo apt install lm-sensors
sudo modprobe drivetemp
sensors

To make drivetemp load automatically every boot, add it to /etc/modules:

echo drivetemp | sudo tee -a /etc/modules

This allows adding each HDD to the sensor plugin, (but it's one item in the list per drive)

9. Reboot and install lxdm:

sudo apt install lxdm

Note: LXDM is preferable to LightDM because LightDM is actually not so light and comes with a TON of deps including Network-Manager whereas LXDM contains about 5 packages.

10. Reboot and login by selecting "Desktop: Xfce4 Session" and your credentials

Note: LXDM will be Debian branded (but we can change that later)
Note2:Upon logging in, if you preserved your home partition, your desktop should be similar but may have some things missing.

11. Setup / config XFCE desktops and addons as required.

12. Install Firefox and other utils:

apt install firefox file-roller gnome-disk-utility gsmartcontrol vlc 

Note: for firefox this will actually install the snap

13. a) Install ZFS and import tank:

apt install zfsutils-linux

b) Import Tank: zpool import Tank

14. Install Docker:

sudo apt-get update

sudo apt-get install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

usermod -a tk -G docker

15. Install portainer:

docker volume create portainer_data
portainer_data

docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

Login to portainer and import backup or paste compose files, and start them.

16. Install VNC Viewer / Server and login

17. Install localsend

18. Install tailscale:

curl -fsSL https://tailscale.com/install.sh | sh

Note: Don't forget to config via admin panel.

19. Install ohmyzsh!:

apt install git zsh

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

Note: Run this as your own user not root
Note2: If you're migrating from an old install, ohmyzsh is already installed in home. Just change default shell.

Set zsh as the default shell: chsh -s /bin/zsh

20. Run: sudo lxdm-config to customise login screen appearance

Note: Without sudo, you can only set your own user icon

21. Syncthing:

a. Install by following: apt.syncthing.net
b. Enable with systemctl enable syncthing@[username].service
c. Start with: systemctl start syncthing@[username].service

22. Ksplice

a. Download the .deb from here: https://ksplice.oracle.com/try/desktop

b. Install with: apt install ./uptrack.deb

c. Then run: sudo uptrack-upgrade -n and accept the user agreement

d. Edit: /etc/uptrack/uptrack.conf and change autoinstall to yes

e. Now activate with: uptrack-upgrade -y

23. Nvidia Drivers for Hardware Transcoding

The default is Nouveau. This doesn't support h264 etc. Unfortunately the Nvidia Quadro NVS 295 is too old for offical support from Ubuntu for 22.04. But there is a PPA:

add-apt-repository ppa:kelebek333/nvidia-legacy
apt install nvidia-340

Note: This currenly works well with kernel 5.15.0-88-generic. It could break in future kernels and need reverting.

24. apt update && apt upgrade

25. Remove unused apps:

apt remove xarchiver && apt autoremove

26. Reboot and profit :) 
```

---

### Post by MAFoElffen on 2023-12-13
I don't see anything jumping out at me.

---

### Post by tkae-lp on 2023-12-13
> **MAFoElffen said:**
> I don't see anything jumping out at me.

Thanks, that's reassuring. I'll report back once I get this new SSD installed.

---

### Post by tkae-lp on 2023-12-15
Ok, re-installation and setup complete. The only thing I haven't done is ksplice. I'm going to see if the problem comes back and if it doesn't, install ksplice to rule out/in that at the same time.

2 reads/writes one after another.

```
cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][100.0%][r=2986MiB/s][r=2986 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=510970: Fri Dec 15 19:19:08 2023
  read: IOPS=1490, BW=1491MiB/s (1563MB/s)(10.0GiB/6869msec)
    slat (usec): min=281, max=166664, avg=667.62, stdev=3297.33
    clat (usec): min=2, max=284276, avg=20265.78, stdev=25931.44
     lat (usec): min=326, max=285159, avg=20933.79, stdev=26638.64
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[   11], 10.00th=[   11], 20.00th=[   11],
     | 30.00th=[   11], 40.00th=[   11], 50.00th=[   11], 60.00th=[   11],
     | 70.00th=[   11], 80.00th=[   12], 90.00th=[   52], 95.00th=[   65],
     | 99.00th=[  129], 99.50th=[  180], 99.90th=[  232], 99.95th=[  279],
     | 99.99th=[  284]
   bw (  MiB/s): min=  266, max= 2960, per=94.21%, avg=1404.46, stdev=1213.29, samples=13
   iops        : min=  266, max= 2960, avg=1404.46, stdev=1213.29, samples=13
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.02%
  lat (msec)   : 2=0.13%, 4=0.23%, 10=0.75%, 20=79.90%, 50=7.38%
  lat (msec)   : 100=9.35%, 250=2.00%, 500=0.09%
  cpu          : usr=0.57%, sys=60.91%, ctx=531, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=1491MiB/s (1563MB/s), 1491MiB/s-1491MiB/s (1563MB/s-1563MB/s), io=10.0GiB (10.7GB), run=6869-6869msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=0): [f(1)][100.0%][w=271MiB/s][w=271 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=526631: Fri Dec 15 19:19:34 2023
  write: IOPS=1182, BW=1182MiB/s (1240MB/s)(10.0GiB/8662msec); 0 zone resets
    slat (usec): min=199, max=2888, avg=554.19, stdev=474.42
    clat (usec): min=3, max=3014.4k, avg=26122.23, stdev=163675.32
     lat (usec): min=244, max=3016.6k, avg=26676.90, stdev=163815.68
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    9], 60.00th=[   14],
     | 70.00th=[   19], 80.00th=[   27], 90.00th=[   42], 95.00th=[   53],
     | 99.00th=[   68], 99.50th=[   73], 99.90th=[ 3004], 99.95th=[ 3004],
     | 99.99th=[ 3004]
   bw (  MiB/s): min=   96, max= 4012, per=100.00%, avg=1661.50, stdev=1333.62, samples=12
   iops        : min=   96, max= 4012, avg=1661.50, stdev=1333.62, samples=12
  lat (usec)   : 4=0.01%, 10=0.04%, 250=0.01%, 500=0.03%, 750=0.04%
  lat (usec)   : 1000=0.03%
  lat (msec)   : 2=0.13%, 4=0.24%, 10=51.28%, 20=22.40%, 50=18.48%
  lat (msec)   : 100=7.01%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1273, max=1273, avg=1273.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1272],  5.00th=[ 1272], 10.00th=[ 1272], 20.00th=[ 1272],
     | 30.00th=[ 1272], 40.00th=[ 1272], 50.00th=[ 1272], 60.00th=[ 1272],
     | 70.00th=[ 1272], 80.00th=[ 1272], 90.00th=[ 1272], 95.00th=[ 1272],
     | 99.00th=[ 1272], 99.50th=[ 1272], 99.90th=[ 1272], 99.95th=[ 1272],
     | 99.99th=[ 1272]
  cpu          : usr=4.93%, sys=70.80%, ctx=12994, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1182MiB/s (1240MB/s), 1182MiB/s-1182MiB/s (1240MB/s-1240MB/s), io=10.0GiB (10.7GB), run=8662-8662msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2940MiB/s][r=2940 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=591376: Fri Dec 15 19:19:44 2023
  read: IOPS=2850, BW=2851MiB/s (2989MB/s)(10.0GiB/3592msec)
    slat (usec): min=279, max=1192, avg=347.79, stdev=46.49
    clat (usec): min=3, max=31039, avg=10762.67, stdev=1306.38
     lat (usec): min=325, max=32233, avg=11110.82, stdev=1340.39
    clat percentiles (usec):
     |  1.00th=[ 6915],  5.00th=[10421], 10.00th=[10421], 20.00th=[10421],
     | 30.00th=[10552], 40.00th=[10552], 50.00th=[10552], 60.00th=[10552],
     | 70.00th=[10552], 80.00th=[10683], 90.00th=[12387], 95.00th=[12387],
     | 99.00th=[13698], 99.50th=[15401], 99.90th=[26346], 99.95th=[28705],
     | 99.99th=[30540]
   bw (  MiB/s): min= 2292, max= 3006, per=99.68%, avg=2841.71, stdev=245.85, samples=7
   iops        : min= 2292, max= 3006, avg=2841.71, stdev=245.85, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.88%, 20=98.30%, 50=0.23%
  cpu          : usr=0.86%, sys=99.03%, ctx=64, majf=0, minf=8203
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2851MiB/s (2989MB/s), 2851MiB/s-2851MiB/s (2989MB/s-2989MB/s), io=10.0GiB (10.7GB), run=3592-3592msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=591662: Fri Dec 15 19:20:00 2023
  write: IOPS=1262, BW=1263MiB/s (1324MB/s)(10.0GiB/8108msec); 0 zone resets
    slat (usec): min=183, max=2929, avg=470.22, stdev=407.95
    clat (usec): min=3, max=3305.8k, avg=24472.97, stdev=179936.26
     lat (usec): min=254, max=3307.7k, avg=24943.64, stdev=180040.18
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    9], 60.00th=[   10],
     | 70.00th=[   14], 80.00th=[   19], 90.00th=[   31], 95.00th=[   51],
     | 99.00th=[   62], 99.50th=[   65], 99.90th=[ 3306], 99.95th=[ 3306],
     | 99.99th=[ 3306]
   bw (  MiB/s): min=  308, max= 4056, per=100.00%, avg=1993.80, stdev=1391.49, samples=10
   iops        : min=  308, max= 4056, avg=1993.80, stdev=1391.49, samples=10
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.04%, 750=0.05%, 1000=0.06%
  lat (msec)   : 2=0.17%, 4=0.36%, 10=60.14%, 20=20.16%, 50=14.06%
  lat (msec)   : 100=4.62%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=956, max=956, avg=956.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  956],  5.00th=[  956], 10.00th=[  956], 20.00th=[  956],
     | 30.00th=[  956], 40.00th=[  956], 50.00th=[  956], 60.00th=[  956],
     | 70.00th=[  956], 80.00th=[  956], 90.00th=[  956], 95.00th=[  956],
     | 99.00th=[  956], 99.50th=[  956], 99.90th=[  956], 99.95th=[  956],
     | 99.99th=[  956]
  cpu          : usr=5.22%, sys=76.59%, ctx=9165, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1263MiB/s (1324MB/s), 1263MiB/s-1263MiB/s (1324MB/s-1324MB/s), io=10.0GiB (10.7GB), run=8108-8108msec


```

Have I done something wrong with the arc settings?

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
19:42:31     0     0      0     0    0     0    0     0    0  2.1G  8.0G   115G

```

```
~ » cat /etc/modprobe.d/zfs.conf                                                                             
options zfs zfs_arc_min=8589934592
options zfs zfs_arc_max=68719476736
```

It seems like a lot less memory is being used now:

```
~ » free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3              
5432

```

---

### Post by tkae-lp on 2023-12-15
Forget that, I've caned the array on several devices and it's ramping up:

```
~ » free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3 
14626

```

```
 time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
20:25:23     7     1     14     0    0     1  100     0    0   15G   15G   101G
--------------------------------------------------------------------------------

```

I guess now we just wait...

Edit: should that miss% be that high?

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
20:26:35    13     2     15     0    0     2  100     0    0   20G   20G    96G
--------------------------------------------------------------------------------

```

```
cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=262705: Fri Dec 15 20:28:00 2023
  write: IOPS=1101, BW=1101MiB/s (1155MB/s)(10.0GiB/9297msec); 0 zone resets
    slat (usec): min=187, max=453027, avg=529.84, stdev=6312.16
    clat (usec): min=3, max=3904.5k, avg=28037.27, stdev=214980.73
     lat (usec): min=246, max=3906.7k, avg=28567.56, stdev=215184.64
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    8], 60.00th=[    9],
     | 70.00th=[   12], 80.00th=[   18], 90.00th=[   21], 95.00th=[   54],
     | 99.00th=[  271], 99.50th=[  464], 99.90th=[ 3876], 99.95th=[ 3910],
     | 99.99th=[ 3910]
   bw (  MiB/s): min=  374, max= 3962, per=100.00%, avg=1812.55, stdev=1421.10, samples=11
   iops        : min=  374, max= 3962, avg=1812.55, stdev=1421.10, samples=11
  lat (usec)   : 4=0.04%, 10=0.01%, 250=0.01%, 500=0.03%, 750=0.05%
  lat (usec)   : 1000=0.04%
  lat (msec)   : 2=0.17%, 4=0.34%, 10=66.80%, 20=19.43%, 50=7.63%
  lat (msec)   : 100=3.95%, 250=0.30%, 500=0.91%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=289, max=289, avg=289.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  290],  5.00th=[  290], 10.00th=[  290], 20.00th=[  290],
     | 30.00th=[  290], 40.00th=[  290], 50.00th=[  290], 60.00th=[  290],
     | 70.00th=[  290], 80.00th=[  290], 90.00th=[  290], 95.00th=[  290],
     | 99.00th=[  290], 99.50th=[  290], 99.90th=[  290], 99.95th=[  290],
     | 99.99th=[  290]
  cpu          : usr=4.54%, sys=66.77%, ctx=7293, majf=1, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1101MiB/s (1155MB/s), 1101MiB/s-1101MiB/s (1155MB/s-1155MB/s), io=10.0GiB (10.7GB), run=9297-9297msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2932MiB/s][r=2931 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=302568: Fri Dec 15 20:28:19 2023
  read: IOPS=2875, BW=2876MiB/s (3015MB/s)(10.0GiB/3561msec)
    slat (usec): min=285, max=1555, avg=344.94, stdev=38.58
    clat (usec): min=2, max=24739, avg=10677.57, stdev=1039.32
     lat (usec): min=329, max=25648, avg=11022.85, stdev=1056.27
    clat percentiles (usec):
     |  1.00th=[ 6849],  5.00th=[10421], 10.00th=[10421], 20.00th=[10552],
     | 30.00th=[10552], 40.00th=[10552], 50.00th=[10552], 60.00th=[10683],
     | 70.00th=[10683], 80.00th=[10945], 90.00th=[10945], 95.00th=[11207],
     | 99.00th=[14484], 99.50th=[14877], 99.90th=[20841], 99.95th=[22676],
     | 99.99th=[24249]
   bw (  MiB/s): min= 2680, max= 2936, per=99.74%, avg=2868.00, stdev=88.69, samples=7
   iops        : min= 2680, max= 2936, avg=2868.00, stdev=88.69, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.01%
  lat (msec)   : 2=0.13%, 4=0.29%, 10=0.85%, 20=98.45%, 50=0.13%
  cpu          : usr=1.10%, sys=98.51%, ctx=57, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2876MiB/s (3015MB/s), 2876MiB/s-2876MiB/s (3015MB/s-3015MB/s), io=10.0GiB (10.7GB), run=3561-3561msec

```

Edit2: Watching Avatar in 4K with Dolby has used up some memory! ;)

```
 time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
20:31:01     0     0      0     0    0     0    0     0    0   35G   35G    81G

```

```
free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3
40319
```

```
cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting 
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=2873MiB/s][r=2872 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=351649: Fri Dec 15 20:33:16 2023
  read: IOPS=2781, BW=2782MiB/s (2917MB/s)(10.0GiB/3681msec)
    slat (usec): min=274, max=1177, avg=356.52, stdev=46.53
    clat (usec): min=3, max=31076, avg=11029.95, stdev=1331.64
     lat (usec): min=336, max=32255, avg=11386.82, stdev=1365.82
    clat percentiles (usec):
     |  1.00th=[ 6980],  5.00th=[10683], 10.00th=[10683], 20.00th=[10683],
     | 30.00th=[10814], 40.00th=[10814], 50.00th=[10814], 60.00th=[10814],
     | 70.00th=[10945], 80.00th=[10945], 90.00th=[12780], 95.00th=[12911],
     | 99.00th=[14091], 99.50th=[15795], 99.90th=[26346], 99.95th=[28705],
     | 99.99th=[30540]
   bw (  MiB/s): min= 2216, max= 2874, per=99.59%, avg=2770.57, stdev=245.38, samples=7
   iops        : min= 2216, max= 2874, avg=2770.57, stdev=245.38, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=0.84%, 20=98.34%, 50=0.23%
  cpu          : usr=1.17%, sys=98.72%, ctx=5, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2782MiB/s (2917MB/s), 2782MiB/s-2782MiB/s (2917MB/s-2917MB/s), io=10.0GiB (10.7GB), run=3681-3681msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][eta 00m:00s]                          
TEST: (groupid=0, jobs=1): err= 0: pid=351921: Fri Dec 15 20:33:29 2023
  write: IOPS=1393, BW=1394MiB/s (1461MB/s)(10.0GiB/7348msec); 0 zone resets
    slat (usec): min=198, max=2094, avg=328.80, stdev=166.25
    clat (usec): min=3, max=3952.5k, avg=22179.16, stdev=216630.55
     lat (usec): min=261, max=3952.8k, avg=22508.45, stdev=216629.88
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[    9], 80.00th=[   11], 90.00th=[   19], 95.00th=[   24],
     | 99.00th=[   27], 99.50th=[   27], 99.90th=[ 3943], 99.95th=[ 3943],
     | 99.99th=[ 3943]
   bw (  MiB/s): min= 1330, max= 3926, per=100.00%, avg=2848.29, stdev=1008.95, samples=7
   iops        : min= 1330, max= 3926, avg=2848.29, stdev=1008.95, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.36%, 10=77.43%, 20=13.69%, 50=7.82%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=1089, max=1089, avg=1089.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[ 1096],  5.00th=[ 1096], 10.00th=[ 1096], 20.00th=[ 1096],
     | 30.00th=[ 1096], 40.00th=[ 1096], 50.00th=[ 1096], 60.00th=[ 1096],
     | 70.00th=[ 1096], 80.00th=[ 1096], 90.00th=[ 1096], 95.00th=[ 1096],
     | 99.00th=[ 1096], 99.50th=[ 1096], 99.90th=[ 1096], 99.95th=[ 1096],
     | 99.99th=[ 1096]
  cpu          : usr=6.29%, sys=85.31%, ctx=3121, majf=0, minf=14
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1394MiB/s (1461MB/s), 1394MiB/s-1394MiB/s (1461MB/s-1461MB/s), io=10.0GiB (10.7GB), run=7348-7348msec

```

---

### Post by #&amp;thj^% on 2023-12-15
Looking pretty good so far.

---

### Post by MAFoElffen on 2023-12-15
Let's see how this pans out over a few days...

---

### Post by tkae-lp on 2023-12-15
> **1fallen said:**
> Looking pretty good so far.

Seemingly so..... ;) Interestingly, the Samsung SSD is much heavier than the Sandisk. There's clearly a lot more heat discipation in there.... temp is almost half that of the Sandisk IIRC: Disk is OK (27° C / 81° F) pretty sure the Sandisk ran in the high 40s. It's been powered on enough by now to get well up to temp:

```
"Description","Value","Flags","Page, Offset"
"    Power-on Hours","11","---","0x01, 0x010"

```

> **MAFoElffen said:**
> Let's see how this pans out over a few days...

Yes, I won't be so quick to victory dance this time! As of tomorrow, I'l have a lot of spare time to will be able to continue to thrash it (if you can call basic reading of media files thrashing!). 

Right now:

```
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=0): [f(1)][100.0%][w=271MiB/s][w=271 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=520167: Fri Dec 15 23:21:52 2023
  write: IOPS=1160, BW=1161MiB/s (1217MB/s)(10.0GiB/8820msec); 0 zone resets
    slat (usec): min=195, max=2127, avg=446.67, stdev=345.36
    clat (usec): min=3, max=4211.4k, avg=26614.95, stdev=230854.66
     lat (usec): min=253, max=4211.6k, avg=27062.14, stdev=230860.39
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    9], 10.00th=[    9], 20.00th=[    9],
     | 30.00th=[    9], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[   14], 80.00th=[   18], 90.00th=[   31], 95.00th=[   42],
     | 99.00th=[   55], 99.50th=[   62], 99.90th=[ 4212], 99.95th=[ 4212],
     | 99.99th=[ 4212]
   bw (  MiB/s): min=  384, max= 3832, per=100.00%, avg=1993.80, stdev=1330.94, samples=10
   iops        : min=  384, max= 3832, avg=1993.80, stdev=1330.94, samples=10
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.04%, 1000=0.05%
  lat (msec)   : 2=0.18%, 4=0.32%, 10=66.43%, 20=15.73%, 50=15.77%
  lat (msec)   : 100=1.08%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=786, max=786, avg=786.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  788],  5.00th=[  788], 10.00th=[  788], 20.00th=[  788],
     | 30.00th=[  788], 40.00th=[  788], 50.00th=[  788], 60.00th=[  788],
     | 70.00th=[  788], 80.00th=[  788], 90.00th=[  788], 95.00th=[  788],
     | 99.00th=[  788], 99.50th=[  788], 99.90th=[  788], 99.95th=[  788],
     | 99.99th=[  788]
  cpu          : usr=5.45%, sys=75.48%, ctx=10726, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1161MiB/s (1217MB/s), 1161MiB/s-1161MiB/s (1217MB/s-1217MB/s), io=10.0GiB (10.7GB), run=8820-8820msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][-.-%][w=177MiB/s][w=177 IOPS][eta 00m:00s]  
TEST: (groupid=0, jobs=1): err= 0: pid=567469: Fri Dec 15 23:22:02 2023
  write: IOPS=1492, BW=1493MiB/s (1565MB/s)(10.0GiB/6859msec); 0 zone resets
    slat (usec): min=188, max=1782, avg=287.70, stdev=114.15
    clat (usec): min=3, max=3888.7k, avg=20698.96, stdev=213157.67
     lat (usec): min=233, max=3889.0k, avg=20987.04, stdev=213156.72
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    8], 20.00th=[    8],
     | 30.00th=[    8], 40.00th=[    8], 50.00th=[    8], 60.00th=[    8],
     | 70.00th=[    9], 80.00th=[   10], 90.00th=[   13], 95.00th=[   17],
     | 99.00th=[   24], 99.50th=[   42], 99.90th=[ 3876], 99.95th=[ 3876],
     | 99.99th=[ 3876]
   bw (  MiB/s): min= 2684, max= 4042, per=100.00%, avg=3323.00, stdev=602.93, samples=6
   iops        : min= 2684, max= 4042, avg=3323.00, stdev=602.93, samples=6
  lat (usec)   : 4=0.04%, 10=0.01%, 250=0.02%, 500=0.04%, 750=0.05%
  lat (usec)   : 1000=0.06%
  lat (msec)   : 2=0.20%, 4=0.38%, 10=80.29%, 20=17.81%, 50=0.80%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=939, max=939, avg=939.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  940],  5.00th=[  940], 10.00th=[  940], 20.00th=[  940],
     | 30.00th=[  940], 40.00th=[  940], 50.00th=[  940], 60.00th=[  940],
     | 70.00th=[  940], 80.00th=[  940], 90.00th=[  940], 95.00th=[  940],
     | 99.00th=[  940], 99.50th=[  940], 99.90th=[  940], 99.95th=[  940],
     | 99.99th=[  940]
  cpu          : usr=6.61%, sys=88.48%, ctx=2231, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1493MiB/s (1565MB/s), 1493MiB/s-1493MiB/s (1565MB/s-1565MB/s), io=10.0GiB (10.7GB), run=6859-6859msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [R(1)][-.-%][r=3016MiB/s][r=3016 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=613737: Fri Dec 15 23:22:11 2023
  read: IOPS=2926, BW=2927MiB/s (3069MB/s)(10.0GiB/3499msec)
    slat (usec): min=275, max=1055, avg=339.06, stdev=46.04
    clat (usec): min=2, max=31307, avg=10481.74, stdev=1296.16
     lat (usec): min=320, max=32361, avg=10821.15, stdev=1330.75
    clat percentiles (usec):
     |  1.00th=[ 6587],  5.00th=[10159], 10.00th=[10159], 20.00th=[10159],
     | 30.00th=[10290], 40.00th=[10290], 50.00th=[10290], 60.00th=[10290],
     | 70.00th=[10421], 80.00th=[10421], 90.00th=[11994], 95.00th=[12125],
     | 99.00th=[13435], 99.50th=[15139], 99.90th=[26346], 99.95th=[28967],
     | 99.99th=[30802]
   bw (  MiB/s): min= 2356, max= 3022, per=99.24%, avg=2904.33, stdev=268.84, samples=6
   iops        : min= 2356, max= 3022, avg=2904.33, stdev=268.84, samples=6
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.05%, 1000=0.03%
  lat (msec)   : 2=0.15%, 4=0.30%, 10=0.95%, 20=98.20%, 50=0.22%
  cpu          : usr=0.89%, sys=99.06%, ctx=16, majf=0, minf=8204
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2927MiB/s (3069MB/s), 2927MiB/s-2927MiB/s (3069MB/s-3069MB/s), io=10.0GiB (10.7GB), run=3499-3499msec
--------------------------------------------------------------------------------
/mnt/Tank # cd /mnt/Tank/ && fio --name TEST --eta-newline=5s --filename=temp.file --rw=read --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=read, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=0): [f(1)][100.0%][r=2713MiB/s][r=2712 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=613942: Fri Dec 15 23:22:19 2023
  read: IOPS=2661, BW=2662MiB/s (2791MB/s)(10.0GiB/3847msec)
    slat (usec): min=296, max=1148, avg=372.74, stdev=48.82
    clat (usec): min=2, max=33466, avg=11525.97, stdev=1407.46
     lat (usec): min=356, max=34588, avg=11899.09, stdev=1444.27
    clat percentiles (usec):
     |  1.00th=[ 7308],  5.00th=[11076], 10.00th=[11207], 20.00th=[11207],
     | 30.00th=[11338], 40.00th=[11338], 50.00th=[11338], 60.00th=[11338],
     | 70.00th=[11338], 80.00th=[11469], 90.00th=[13304], 95.00th=[13435],
     | 99.00th=[14746], 99.50th=[16581], 99.90th=[28443], 99.95th=[31065],
     | 99.99th=[32900]
   bw (  MiB/s): min= 2104, max= 2752, per=99.41%, avg=2646.00, stdev=239.23, samples=7
   iops        : min= 2104, max= 2752, avg=2646.00, stdev=239.23, samples=7
  lat (usec)   : 4=0.05%, 500=0.05%, 750=0.04%, 1000=0.01%
  lat (msec)   : 2=0.15%, 4=0.27%, 10=0.80%, 20=98.37%, 50=0.26%
  cpu          : usr=1.01%, sys=98.91%, ctx=7, majf=0, minf=8205
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=10240,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
   READ: bw=2662MiB/s (2791MB/s), 2662MiB/s-2662MiB/s (2791MB/s-2791MB/s), io=10.0GiB (10.7GB), run=3847-3847msec

```

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
23:22:41     0     0      0     0    0     0    0     0    0   21G   37G    94G
```

```
free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3
26356

```

See you on the other side of the rabbit hole :D

---

### Post by #&amp;thj^% on 2023-12-15
> **tkae-lp said:**
> 

See you on the other side of the rabbit hole :D

:lolflag:
Sometimes that's Soo True!

---

### Post by tkae-lp on 2023-12-15
:mrgreen: While I traverse the warren, do you guys know how to hide a ZFS 'element' in the XFCE4 sidebar? I did it on Bionic, and I can't remember how....

I have both the Tank and the L2ARC/SLOG in the side panel:

[IMG]https://imgur.com/Jog7Hdf.png[/IMG]

When accidentally clicking on it, it prompts for root password which is annoying. I can't remember how I hid these before?

Edit: Sorry, I realise this is off-topic

---

### Post by MAFoElffen on 2023-12-15
[LIST]
[*]Open Settings.
[*]Select Appearance in the sidebar.
[*]Click 'configure dock behaviour' in the Dock section.
[*]Slide the 'Show Volumes and Devices' toggle to off.
[/LIST]

---

### Post by tkae-lp on 2023-12-16
> **MAFoElffen said:**
> 
[LIST]
[*]Open Settings. 
[*]Select Appearance in the sidebar. 
[*]Click 'configure dock behaviour' in the Dock section. 
[*]Slide the 'Show Volumes and Devices' toggle to off. 
[/LIST]


Thank you, but is that for Gnome? I don't see those options on XFCE - but also, I am guessing that would hide all removable volumes? 

However - I woke up this morning and remembered how I did it. I used gnome disks to turn off the auto switch in mount options, then edited the last parameter adding x-gvfs-hide, so it's appended this to fstab:

```
/dev/disk/by-id/nvme-eui.002538b531410ff5-part1 /mnt/nvme-eui.002538b531410ff5-part1 auto nosuid,nodev,nofail,noauto,x-gvfs-hide 0 0
/dev/disk/by-uuid/14479364333730549985 /mnt/14479364333730549985 auto nosuid,nodev,nofail,noauto,x-gvfs-hide 0 0

```
 
Both partitions showing were the NVMe.. doing it this way seems to allow ZFS to still use them but they are now hidden on desktop and sidebar in XFCE, but when I insert a key drive it still shows.

Speeds still good this morning :)

---

### Post by tkae-lp on 2023-12-17
Dare I jinx it, but still good...

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
03:51:48     0     0      0     0    0     0    0     0    0   15G   19G    98G

```

```
READ: bw=2679MiB/s (2809MB/s), 2679MiB/s-2679MiB/s (2809MB/s-2809MB/s), io=10.0GiB (10.7GB), run=3822-3822msec

```
```

WRITE: bw=1141MiB/s (1196MB/s), 1141MiB/s-1141MiB/s (1196MB/s-1196MB/s), io=10.0GiB (10.7GB), run=8978-8978msec

```

Still caning it as much as I can and monitoring.....

---

### Post by MAFoElffen on 2023-12-18
LOL. Still crossing fingers...

---

### Post by tkae-lp on 2023-12-20
> **MAFoElffen said:**
> LOL. Still crossing fingers...

I will actually be mind blown if this turns out to be the problem all along.....

Still ok (but not officially saying this yet!) lol:

Yesterday:

```
   READ: bw=2643MiB/s (2772MB/s), 2643MiB/s-2643MiB/s (2772MB/s-2772MB/s), io=10.0GiB (10.7GB), run=3874-3874msec

```

```
  WRITE: bw=1279MiB/s (1341MB/s), 1279MiB/s-1279MiB/s (1341MB/s-1341MB/s), io=10.0GiB (10.7GB), run=8006-8006msec

```

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
03:16:21     0     0      0     0    0     0    0     0    0   22G   24G    90G

```

Now:

```
 READ: bw=3665MiB/s (3843MB/s), 3665MiB/s-3665MiB/s (3843MB/s-3843MB/s), io=10.0GiB (10.7GB), run=2794-2794msec
```

```
 WRITE: bw=1047MiB/s (1098MB/s), 1047MiB/s-1047MiB/s (1098MB/s-1098MB/s), io=10.0GiB (10.7GB), run=9776-9776msec
```


```
  time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
01:34:06    84     0      0     0    0     0    0     0    0   61G   64G    47G
```

Current Samsung SSD temp: 30c. 

Lots of Emby use of late...... continuing to test.

---

### Post by MAFoElffen on 2023-12-20
So far, so good. Still crossing fingers. LOL

---

### Post by tkae-lp on 2023-12-23
> **MAFoElffen said:**
> Still crossing fingers. LOL

Thanks, me too! :D

Interestingly, the arc (now given time) is maxing out:

```
   time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
17:24:36     0     0      0     0    0     0    0     0    0   64G   64G    40G

```

No doubt if not capped at 64GB:

```
cat /etc/modprobe.d/zfs.conf
options zfs zfs_arc_min=8589934592
options zfs zfs_arc_max=68719476736
```

It would be even higher ;)

Performance is good here though (still monitoring though!):

```
WRITE: bw=1175MiB/s (1232MB/s), 1175MiB/s-1175MiB/s (1232MB/s-1232MB/s), io=10.0GiB (10.7GB), run=8713-8713msec

READ: bw=3399MiB/s (3564MB/s), 3399MiB/s-3399MiB/s (3564MB/s-3564MB/s), io=10.0GiB (10.7GB), run=3013-3013msec
```

I might not get the chance to message again until after the 25th, so here's wishing everyone here on the forums and at Canonical a very Happy Christmas (or whatever holiday you may be celebrating now) and a Happy New Year with best wishes for 2024 ;)

---

### Post by MAFoElffen on 2023-12-23
Happy Holidays to you and your's!

---

### Post by tkae-lp on 2023-12-30
Happy New Year for tomorrow! :)

Still good btw:

```
READ: bw=2860MiB/s (2999MB/s), 2860MiB/s-2860MiB/s (2999MB/s-2999MB/s), io=10.0GiB (10.7GB), run=3580-3580msec
```
```
WRITE: bw=1164MiB/s (1221MB/s), 1164MiB/s-1164MiB/s (1221MB/s-1221MB/s), io=10.0GiB (10.7GB), run=8797-8797msec
```

---

### Post by MAFoElffen on 2023-12-30
Happy New Year!

Good to see all is well and holding!

---

### Post by tkae-lp on 2024-01-05
Just checking in to let you know I haven't forgotten about this. Things are still going well. :) It's been approx 3 weeks since re-installation and we are still merrily hopping backwards are forwards through 4K on several devices at a time. I haven't heard a peep out of the family asking me to fix Emby... it's been... bliss :D [insert little party dance here - but still not victory dance (yet) lol]. 

I am going to give it 1 more week (perhaps overkill but I think we can all agree based on the history there should have been something at that point) and, if all is still well, I will reinstall Ksplice. I am hoping this doesn't cause the issue to reappear, but either way it will answer the question.

---

### Post by MAFoElffen on 2024-01-05
Glad to hear everything is going so well.

---

### Post by tkae-lp on 2024-01-14
:-( I copied a file from one folder to another this evening (duplicate not move) and noticed it was slow... (20 secs for ~350MB)

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][53.8%][w=107MiB/s][w=107 IOPS][eta 00m:06s]
Jobs: 1 (f=1): [W(1)][59.1%][w=46.0MiB/s][w=46 IOPS][eta 00m:09s] 
Jobs: 1 (f=1): [W(1)][59.4%][w=24.0MiB/s][w=24 IOPS][eta 00m:13s] 
Jobs: 1 (f=1): [W(1)][61.0%][w=37.0MiB/s][w=37 IOPS][eta 00m:16s] 
Jobs: 1 (f=1): [W(1)][63.3%][w=37.0MiB/s][w=37 IOPS][eta 00m:18s] 
Jobs: 1 (f=1): [W(1)][66.1%][w=39.0MiB/s][w=39 IOPS][eta 00m:19s] 
Jobs: 1 (f=1): [W(1)][71.7%][w=126MiB/s][w=126 IOPS][eta 00m:17s] 
Jobs: 1 (f=1): [W(1)][81.7%][w=287MiB/s][w=287 IOPS][eta 00m:11s] 
Jobs: 1 (f=1): [W(1)][98.2%][eta 00m:01s]                         
Jobs: 1 (f=0): [f(1)][100.0%][w=271MiB/s][w=271 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=3103281: Mon Jan 15 01:44:04 2024
  write: IOPS=174, BW=174MiB/s (183MB/s)(10.0GiB/58711msec); 0 zone resets
    slat (usec): min=191, max=61178, avg=5132.95, stdev=8453.58
    clat (usec): min=4, max=6125.3k, avg=176183.18, stdev=415840.98
     lat (usec): min=297, max=6126.8k, avg=181316.96, stdev=420835.36
    clat percentiles (msec):
     |  1.00th=[    8],  5.00th=[    8], 10.00th=[    8], 20.00th=[    9],
     | 30.00th=[   10], 40.00th=[   15], 50.00th=[   53], 60.00th=[   81],
     | 70.00th=[  117], 80.00th=[  192], 90.00th=[  676], 95.00th=[  835],
     | 99.00th=[ 1083], 99.50th=[ 1284], 99.90th=[ 6141], 99.95th=[ 6141],
     | 99.99th=[ 6141]
   bw (  KiB/s): min=22528, max=4077568, per=100.00%, avg=196312.62, stdev=526535.26, samples=104
   iops        : min=   22, max= 3982, avg=191.71, stdev=514.19, samples=104
  lat (usec)   : 10=0.04%, 20=0.01%, 500=0.01%, 750=0.02%, 1000=0.03%
  lat (msec)   : 2=0.07%, 4=0.15%, 10=35.72%, 20=5.52%, 50=3.62%
  lat (msec)   : 100=19.67%, 250=18.72%, 500=4.99%, 750=1.90%, 1000=8.14%
  lat (msec)   : 2000=1.08%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=983, max=983, avg=983.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  980],  5.00th=[  980], 10.00th=[  980], 20.00th=[  980],
     | 30.00th=[  980], 40.00th=[  980], 50.00th=[  980], 60.00th=[  980],
     | 70.00th=[  980], 80.00th=[  980], 90.00th=[  980], 95.00th=[  980],
     | 99.00th=[  980], 99.50th=[  980], 99.90th=[  980], 99.95th=[  980],
     | 99.99th=[  980]
  cpu          : usr=1.02%, sys=13.79%, ctx=50057, majf=0, minf=16
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=174MiB/s (183MB/s), 174MiB/s-174MiB/s (183MB/s-183MB/s), io=10.0GiB (10.7GB), run=58711-58711msec

```

Waiting 5 minutes and checking again gives:

```
fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                          
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s] 
TEST: (groupid=0, jobs=1): err= 0: pid=3170929: Mon Jan 15 01:46:02 2024
  write: IOPS=1013, BW=1014MiB/s (1063MB/s)(10.0GiB/10102msec); 0 zone resets
    slat (usec): min=205, max=1925, avg=344.45, stdev=240.41
    clat (usec): min=3, max=6547.8k, avg=30515.32, stdev=359211.99
     lat (usec): min=260, max=6548.1k, avg=30860.17, stdev=359212.30
    clat percentiles (msec):
     |  1.00th=[    6],  5.00th=[    8], 10.00th=[    9], 20.00th=[    9],
     | 30.00th=[    9], 40.00th=[    9], 50.00th=[    9], 60.00th=[    9],
     | 70.00th=[    9], 80.00th=[   10], 90.00th=[   18], 95.00th=[   24],
     | 99.00th=[   50], 99.50th=[   53], 99.90th=[ 6544], 99.95th=[ 6544],
     | 99.99th=[ 6544]
   bw (  MiB/s): min=  726, max= 3730, per=100.00%, avg=2848.29, stdev=1081.92, samples=7
   iops        : min=  726, max= 3730, avg=2848.29, stdev=1081.92, samples=7
  lat (usec)   : 4=0.04%, 10=0.01%, 500=0.05%, 750=0.05%, 1000=0.05%
  lat (msec)   : 2=0.20%, 4=0.35%, 10=81.28%, 20=11.36%, 50=5.71%
  lat (msec)   : 100=0.61%, >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=646, max=646, avg=646.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  644],  5.00th=[  644], 10.00th=[  644], 20.00th=[  644],
     | 30.00th=[  644], 40.00th=[  644], 50.00th=[  644], 60.00th=[  644],
     | 70.00th=[  644], 80.00th=[  644], 90.00th=[  644], 95.00th=[  644],
     | 99.00th=[  644], 99.50th=[  644], 99.90th=[  644], 99.95th=[  644],
     | 99.99th=[  644]
  cpu          : usr=4.39%, sys=62.32%, ctx=9354, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=1014MiB/s (1063MB/s), 1014MiB/s-1014MiB/s (1063MB/s-1063MB/s), io=10.0GiB (10.7GB), run=10102-10102msec
```

and another 5 minutes:

```
WRITE: bw=1020MiB/s (1070MB/s), 1020MiB/s-1020MiB/s (1070MB/s-1070MB/s), io=10.0GiB (10.7GB), run=10038-10038msec

```

Despite this, one thing I will say is that things have been perfect when streaming using Emby.

A scrub was recently performed:

```
/mnt/Tank # zpool status
  pool: Tank
 state: ONLINE
  scan: scrub repaired 0B in 05:43:35 with 0 errors on Sun Jan 14 06:07:36 2024
config:

    NAME                                                                STATE     READ WRITE CKSUM
    Tank                                                                ONLINE       0     0     0
      raidz2-0                                                          ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300xxxx                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4xxxx                                 ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4xxxx                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300xxxx                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300xxxx                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300xxxx                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300xxxx                                 ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300xxxx                                 ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W53xxxxx-part2  ONLINE       0     0     0
    cache
      nvme0n1p1                                                         ONLINE       0     0     0

errors: No known data errors

```

Ksplice is not yet installed.

Could this be within the realms of acceptable slow down? I appreciate that once in a while something like this 'could' happen, as long as it doesn't happen as much as it was before. I've had no other problems. Still, I'm a bit gutted. This is the first issue since replacing the OS drive.

Another check in the 5-10 mins it's taken me to type/paste this:

```
WRITE: bw=1424MiB/s (1494MB/s), 1424MiB/s-1424MiB/s (1494MB/s-1494MB/s), io=10.0GiB (10.7GB), run=7189-7189msec
```

```
READ: bw=4525MiB/s (4745MB/s), 4525MiB/s-4525MiB/s (4745MB/s-4745MB/s), io=10.0GiB (10.7GB), run=2263-2263msec
```

What do you guys think? Problem still here or just a blip?

Edit: Gonna have to hit the hay as I have a long day tomorrow. Will check in ASAP.

---

### Post by tkae-lp on 2024-01-15
No problems today:

```
READ: bw=4326MiB/s (4536MB/s), 4326MiB/s-4326MiB/s (4536MB/s-4536MB/s), io=10.0GiB (10.7GB), run=2367-2367msec

```

```
WRITE: bw=1377MiB/s (1443MB/s), 1377MiB/s-1377MiB/s (1443MB/s-1443MB/s), io=10.0GiB (10.7GB), run=7439-7439msec
```


I'm thinking that this may have just been a freak occurrence. I continue to experience no issues with playback. However, I'm going to continue to monitor for a while.

Sorry this is taking longer than expected!

---

### Post by MAFoElffen on 2024-01-16
No problems. This is in your own time. LOL.

---

### Post by tkae-lp on 2024-01-16
Very true! ;)

No problems so far today:

```
READ: bw=3561MiB/s (3733MB/s), 3561MiB/s-3561MiB/s (3733MB/s-3733MB/s), io=10.0GiB (10.7GB), run=2876-2876msec
```
```
WRITE: bw=1782MiB/s (1869MB/s), 1782MiB/s-1782MiB/s (1869MB/s-1869MB/s), io=10.0GiB (10.7GB), run=5745-5745msec
```

Whatever it was seems to have been a freak occurrence. I even checked the new OS SSD's SMART data just in case something had flagged which might indicate a deeper SATA (board) issue but it's squeaky clean.

Still monitoring....

---

### Post by tkae-lp on 2024-01-22
Ok, this is not gone... last couple of days I've had slow downs.

Just now I see:

```
READ: bw=2735MiB/s (2868MB/s), 2735MiB/s-2735MiB/s (2868MB/s-2868MB/s), io=10.0GiB (10.7GB), run=3744-3744msec

```

But:

```
WRITE: bw=251MiB/s (263MB/s), 251MiB/s-251MiB/s (263MB/s-263MB/s), io=10.0GiB (10.7GB), run=40824-40824msec

```

So the main problem is on the write again. All the docker configs are on that tank which means the Emby DB - this could be why the write slow down is so apparent, It will want to update the DB with the current file and playback position.

Ksplice is not installed, so I guess that rules that out.

Where do we go from here? It has been so good up until this point. I've enjoyed a flawless experience until the hiccup the other day. It seems like we fix one thing and another pops up. I'm almost getting the feeling that I am dealing with multiple issues here....

ARC is not quite maxed:

```
    time  read  miss  miss%  dmis  dm%  pmis  pm%  mmis  mm%  size     c  avail
22:57:42     0     0      0     0    0     0    0     0    0   60G   64G    46G
```

Free mem:

```
free -m  | grep ^Mem | tr -s ' ' | cut -d ' ' -f 3
57147
```

We're on the eve of Noble... Do I limp along and jump or try and fix this? The curiosity in me wants to fix this.... but idk. What do you guys think?

---

### Post by #&amp;thj^% on 2024-01-22
Mine hasn't hit that yet:
```
Run status group 0 (all jobs):
  WRITE: bw=2297MiB/s (2409MB/s), 2297MiB/s-2297MiB/s (2409MB/s-2409MB/s), io=10.0GiB (10.7GB), run=4458-4458msec

```
I'm going to talk to/with  MAFoElffen to see if he is affected.

I'm on Noble but I still don't advise a jump yet....getting closer but not yet.
EDIT: Hold the press...this just in. I imported my tank and have a different showing now:
```
Run status group 0 (all jobs):
  WRITE: bw=57.3MiB/s (60.1MB/s), 57.3MiB/s-57.3MiB/s (60.1MB/s-60.1MB/s), io=3442MiB (3609MB), run=60027-60027msec

```
```
df -hT /tank
Filesystem     Type  Size  Used Avail Use% Mounted on
tank           zfs   450G  126G  325G  28% /tank

```

---

### Post by tkae-lp on 2024-01-23
[SIZE=3]_**Wow**_[/SIZE]!!....... that certainly looks like the behaviour I have been seeing. I've never seen you post speeds anywhere near that low. Whatever this thing is, I would say it's a fairly safe bet that it seems you have it as well. 

I was just watching some old Star Trek TNG episodes and Emby was struggling to load each new episode so I checked, and this is from just now:

```
WRITE: bw=1073MiB/s (1125MB/s), 1073MiB/s-1073MiB/s (1125MB/s-1125MB/s), io=10.0GiB (10.7GB), run=9541-9541msec
```

```
READ: bw=563MiB/s (591MB/s), 563MiB/s-563MiB/s (591MB/s-591MB/s), io=10.0GiB (10.7GB), run=18174-18174msec
```

Not being able to scrub through even SD without buffering is how bad it was when I first created the thread.

My space usage has increased slightly since I had a clear out:

```
df -hT /mnt/Tank
Filesystem     Type  Size  Used Avail Use% Mounted on
Tank           zfs    21T   12T  8.7T  58% /mnt/Tank
```

But in light of your slow down posted here (bearing in mind you are no where near 58%) I am not sure if it's the free space that's doing it. However, I will offload some stuff this evening and bring it back down a bit just to check.

Just to be clear, I'm not on Noble, still on Jammy. I was just contemplating it.

Edit: Just checked back in the thread, and I was originally at 69% full when opening this thread. I got it down to 57%.

It seems unlikely this is the cause. However, I have talked to the kids and pruned another series they no longer want, freeing 192GB so back down to:

```
Filesystem     Type  Size  Used Avail Use% Mounted on
Tank           zfs    21T   12T  8.9T  57% /mnt/Tank

```

---

### Post by #&amp;thj^% on 2024-01-24
MAFoElffen has reported the same, and we are trying to find why.

I get better write speeds in my /tank with btrfs.
```
Run status group 0 (all jobs):
  WRITE: bw=225MiB/s (236MB/s), 225MiB/s-225MiB/s (236MB/s-236MB/s), io=10.0GiB (10.7GB), run=45526-45526msec

```
This drive:
```
&#9472;[/tank]
&#9492;&#9472;&#9472;&#9596; $df -hT
Filesystem      Type      Size  Used Avail Use% Mounted on
udev            devtmpfs  6.8G     0  6.8G   0% /dev
tmpfs           tmpfs     1.4G  2.1M  1.4G   1% /run
/dev/sda2       btrfs     457G  100G  356G  22% /
tmpfs           tmpfs     6.8G  516K  6.8G   1% /dev/shm
tmpfs           tmpfs     5.0M   16K  5.0M   1% /run/lock
efivarfs        efivarfs  148K   71K   73K  50% /sys/firmware/efi/efivars
/dev/sda2       btrfs     457G  100G  356G  22% /home
/dev/sda1       vfat      300M  8.8M  291M   3% /boot/efi
tank            zfs       450G  126G  325G  28% /tank
tank/test       zfs       325G  128K  325G   1% /test
tank/filesystem zfs       325G  128K  325G   1% /tank/filesystem
tmpfs           tmpfs     1.4G  148K  1.4G   1% /run/user/1000

```
I agree space dose not seem to be the main factor here at all.

Still digging for a solution though.

---

### Post by tkae-lp on 2024-01-24
How odd! I did use btrfs for root a while back but am currently on ext4. However, your btrfs speeds are not what they should be even if they are faster. It's possible that this is simply random. I have found the issue to vary massively from check to check, sometimes fine [or not] for several hours/days. It may be giving the illusion that btrfs is better, when in fact you are just not in such a bad slow down right now. For example, this period of slow down I am currently experiencing is quite prevalent. I've had little relief from it. Still soldiering on through the SD TV episodes though lol

I'm sorry you guys have been afflicted with this but - in some ways - this may be a good thing as you will be able to easier dig around and diagnose on your boxes, and you both know much more about ZFS that I do. 

Please let me know if there is anything I can do/try/test.

---

### Post by #&amp;thj^% on 2024-01-24
> **tkae-lp said:**
> 
I'm sorry you guys have been afflicted with this but - in some ways - this may be a good thing as you will be able to easier dig around and diagnose on your boxes, and you both know much more about ZFS that I do. 

Please let me know if there is anything I can do/try/test.
No the speed is not up to snuff, but we have nothing or nowhere to start so I prod and prod till something reveals the problem.

And don't be sorry this how we help fix new or existing bugs...it takes a community. :)

Just my notes disregard anything below:
```

$zdb

tank:
    version: 5000
    name: 'tank'
    state: 0
    txg: 19707
    pool_guid: 10926758658995060061
    errata: 0
    hostid: 320048488
    hostname: 'parrot'
    com.delphix:has_per_vdev_zaps
    vdev_children: 1
    vdev_tree:
        type: 'root'
        id: 0
        guid: 10926758658995060061
        create_txg: 4
        com.klarasystems:vdev_zap_root: 129
        children[0]:
            type: 'disk'
            id: 0
            guid: 10795441740398861942
            path: '/dev/sdb2'
            whole_disk: 0
            metaslab_array: 256
            metaslab_shift: 32
            ashift: 11
            asize: 499564150784
            is_log: 0
            DTL: 1548
            create_txg: 4
            com.delphix:vdev_zap_leaf: 130
            com.delphix:vdev_zap_top: 131
    features_for_read:
        com.delphix:hole_birth
        com.delphix:embedded_data
        com.klarasystems:vdev_zaps_v2
&#9484;&#9472;[me@parrot]&#9472;[~]
&#9492;&#9472;&#9472;&#9596; $zpool get all
NAME  PROPERTY                       VALUE                          SOURCE
tank  size                           464G                           -
tank  capacity                       27%                            -
tank  altroot                        -                              default
tank  health                         ONLINE                         -
tank  guid                           10926758658995060061           -
tank  version                        -                              default
tank  bootfs                         -                              default
tank  delegation                     on                             default
tank  autoreplace                    off                            default
tank  cachefile                      -                              default
tank  failmode                       wait                           default
tank  listsnapshots                  off                            default
tank  autoexpand                     off                            default
tank  dedupratio                     1.00x                          -
tank  free                           338G                           -
tank  allocated                      126G                           -
tank  readonly                       off                            -
tank  ashift                         0                              default
tank  comment                        -                              default
tank  expandsize                     -                              -
tank  freeing                        0                              -
tank  fragmentation                  0%                             -
tank  leaked                         0                              -
tank  multihost                      off                            default
tank  checkpoint                     -                              -
tank  load_guid                      2699787098362106378            -
tank  autotrim                       off                            default
tank  compatibility                  off                            default
tank  bcloneused                     0                              -
tank  bclonesaved                    0                              -
tank  bcloneratio                    1.00x                          -
tank  feature@async_destroy          enabled                        local
tank  feature@empty_bpobj            active                         local
tank  feature@lz4_compress           active                         local
tank  feature@multi_vdev_crash_dump  enabled                        local
tank  feature@spacemap_histogram     active                         local
tank  feature@enabled_txg            active                         local
tank  feature@hole_birth             active                         local
tank  feature@extensible_dataset     active                         local
tank  feature@embedded_data          active                         local
tank  feature@bookmarks              enabled                        local
tank  feature@filesystem_limits      enabled                        local
tank  feature@large_blocks           enabled                        local
tank  feature@large_dnode            enabled                        local
tank  feature@sha512                 enabled                        local
tank  feature@skein                  enabled                        local
tank  feature@edonr                  enabled                        local
tank  feature@userobj_accounting     active                         local
tank  feature@encryption             enabled                        local
tank  feature@project_quota          active                         local
tank  feature@device_removal         enabled                        local
tank  feature@obsolete_counts        enabled                        local
tank  feature@zpool_checkpoint       enabled                        local
tank  feature@spacemap_v2            active                         local
tank  feature@allocation_classes     enabled                        local
tank  feature@resilver_defer         enabled                        local
tank  feature@bookmark_v2            enabled                        local
tank  feature@redaction_bookmarks    enabled                        local
tank  feature@redacted_datasets      enabled                        local
tank  feature@bookmark_written       enabled                        local
tank  feature@log_spacemap           active                         local
tank  feature@livelist               enabled                        local
tank  feature@device_rebuild         enabled                        local
tank  feature@zstd_compress          enabled                        local
tank  feature@draid                  enabled                        local
tank  feature@zilsaxattr             active                         local
tank  feature@head_errlog            active                         local
tank  feature@blake3                 enabled                        local
tank  feature@block_cloning          enabled                        local
tank  feature@vdev_zaps_v2           active                         local

```

This is one problem on mine:
```
tank  ashift                         0      
```
This will cause very slow write speeds.
I'm not done yet still disregard (I need these notes in case I blow my system up LOL)
My history
```
sudo zpool history tank
History for 'tank':
2023-11-29.13:28:07 zpool create -f tank /dev/sda2
2023-11-29.14:47:10 zpool export tank
2023-11-29.20:28:10 zpool import tank
2023-11-30.07:35:53 zpool import tank
2023-11-30.08:54:09 zpool import -c /etc/zfs/zpool.cache -aN
2023-11-30.12:43:22 zpool import -c /etc/zfs/zpool.cache -aN
2023-11-30.14:46:25 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-01.07:49:14 zpool import tank
2023-12-01.11:29:03 zfs create tank/filesystem
2023-12-01.11:30:27 zfs snapshot tank/filesystem@friday
2023-12-01.13:22:25 zpool export rpool/ROOT/ubuntu_2wtpxc@friday tank
2023-12-03.08:53:48 zpool import tank
2023-12-03.13:41:24 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-04.09:49:21 zpool import -f tank
2023-12-04.09:51:07 zpool export tank
2023-12-04.11:05:45 zpool import tank
2023-12-04.11:06:00 zfs create -o canmount=on -o mountpoint=/test tank/test
2023-12-04.11:28:16 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-04.13:41:38 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-05.07:23:49 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-05.07:35:28 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-05.09:05:30 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-07.10:26:53 zpool import tank
2023-12-07.12:15:42 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-07.14:22:40 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-08.12:51:41 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-08.12:59:27 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-08.16:00:25 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.11:39:00 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.11:52:22 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.14:38:28 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.14:42:25 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.15:24:27 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.15:33:06 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-09.16:00:56 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-10.06:49:46 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-10.17:32:37 zpool import tank
2023-12-11.09:31:43 zpool import tank
2023-12-11.11:17:00 zpool import tank
2023-12-12.18:55:23 zpool import tank
2023-12-12.19:48:11 zpool export tank
2023-12-19.12:28:24 zpool import tank
2023-12-19.12:53:32 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-20.15:24:26 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-21.07:05:43 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-21.13:07:05 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-21.13:10:20 zpool import -c /etc/zfs/zpool.cache -aN
2023-12-25.07:44:20 zpool import tank
2024-01-09.13:06:55 zpool import -f tank
2024-01-09.14:35:03 zfs destroy tank/filesystem@friday
2024-01-12.11:37:35 zpool import -f tank
2024-01-13.06:43:44 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-13.06:54:25 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-13.09:53:01 zpool import -f tank
2024-01-13.13:19:31 zpool import -f tank
2024-01-13.14:57:26 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-13.15:17:35 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-13.18:23:07 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-16.08:28:28 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-16.08:37:42 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-17.07:53:42 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-17.08:00:46 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-18.08:10:53 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-19.02:37:59 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-19.02:51:02 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-19.17:13:38 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-20.06:29:26 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-20.13:52:46 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-21.08:19:48 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-21.08:32:50 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-21.15:23:27 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-21.15:36:43 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-21.17:16:40 zpool import -f tank
2024-01-22.16:34:27 zpool import -f tank
2024-01-22.16:46:25 zpool scrub tank
2024-01-22.16:49:55 zpool export tank
2024-01-23.11:12:14 zpool import -f tank
2024-01-24.05:48:48 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.08:48:19 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.08:54:41 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.09:03:09 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.09:08:42 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.09:17:39 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.09:21:14 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.09:26:17 zpool import -c /etc/zfs/zpool.cache -aN
2024-01-24.13:27:06 zpool import -c /etc/zfs/zpool.cache -aN

```
Temp Check:
```
=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        28 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    3,723,733 [1.90 TB]
Data Units Written:                 6,534,694 [3.34 TB]
Host Read Commands:                 124,029,758
Host Write Commands:                202,144,712
Controller Busy Time:               422
Power Cycles:                       3,277
Power On Hours:                     670
Unsafe Shutdowns:                   326
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0

Warning: NVMe Get Log truncated to 0x200 bytes, 0x200 bytes zero filled
Error Information (NVMe Log 0x01, 16 of 256 entries)
No Errors Logged


```

---

### Post by tkae-lp on 2024-01-25
> **1fallen said:**
> No the speed is not up to snuff, but we have nothing or nowhere to start so I prod and prod till something reveals the problem.

And don't be sorry this how we help fix new or existing bugs...it takes a community. :)

Being an amateur tinkerer in many things, I often come across issues with whatever it is that I have decided to take my hand to. Usually, ~80% of them are solved with a quick search, ~15% with an extended search and almost all of the remaining 5% a quick post - but this is the first time I have experienced an issue with one of my hobbies that has required such a long running thread due to such an elusive issue. I guess what I am trying to say is that I thoroughly appreciate your continued help with this. The community vibe is strong with this one ;)

---

### Post by MAFoElffen on 2024-01-25
"The Force is strong in this one..."

Still here. I'm not having that problem. (Yet.) I did have some other strangeness. Which was odd and I cannot explain a why for it, really. 

It lost track of the device device name for one of my L2ARC's. (???) Easy to fix, and the nothing was really wrong with it after I re-added it. But I cannot explain the why, or even how it could have done that. It wasn't even something that was valid for a vdev. That is the first time I have seen that in 18 years

---

### Post by tkae-lp on 2024-01-27
That's odd... not sure what to make of that! I have one of my NVMe drive rename itself on import, but it still works, it's just annoying.

Today has been horrible for speed :sad: Can't even watch a SD file without it freezing every 10 seconds.

```
WRITE: bw=96.6MiB/s (101MB/s), 96.6MiB/s-96.6MiB/s (101MB/s-101MB/s), io=5800MiB (6082MB), run=60061-60061msec
```
```
READ: bw=3195MiB/s (3350MB/s), 3195MiB/s-3195MiB/s (3350MB/s-3350MB/s), io=10.0GiB (10.7GB), run=3205-3205msec
```

So odd that it's the write that affects it. I can only imagine it's something to do with the docker config files, like writing to the emby DB.

I've resorted to using VLC today and browsing a samba share :-S

---

### Post by MAFoElffen on 2024-01-27
The thing I have a problem grasping, is that the process of what you are doing (watching something from your media server) is a read process. Why is the read speed high, and the write speed so low?

I must not be seeing "something" there that is going on.

I think we need to capture some sampling data to look want might be going on...

Look at this, and use something similar. I will explain what is going on, so you can modify the command to what is on yours
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ [COLOR=#ff0000]iostat -x --pretty sda2 sda3 sda3 sda4 sda5 sda6 2 | tee ~/Scripts/iostat.log.txt[/COLOR]
Linux 6.2.0-39-generic (Mikes-ThinkPad-T520)     01/27/2024     _x86_64_    (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.31    0.16    1.05    0.06    0.00   95.42

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.11     0.00   0.00    0.42    38.35 sda2
    0.00      0.12     0.00   0.00    0.43    44.00 sda3
    0.00      0.11     0.00   0.00    0.41    38.35 sda4
    0.00      0.11     0.00   0.00    0.49    38.35 sda5
    0.11      0.94     0.09  43.42    1.01     8.23 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.29      5.31     1.04  78.35    0.25    18.48 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.02 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.81    0.00    0.25    0.00    0.00   98.94

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.56    0.00    0.13    0.00    0.00   99.31

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.75    0.00    0.19    0.00    0.00   99.06

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.13    0.00    0.38    0.00    0.00   98.50

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.75    0.00    0.50    0.25    0.00   98.50

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.19    0.00    0.50    0.00    0.00   98.31

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.38    0.00    0.88    0.00    0.00   97.75

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.12    0.00    0.69    0.25    0.00   97.94

     r/s     rkB/s   rrqm/s  %rrqm r_await rareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     w/s     wkB/s   wrqm/s  %wrqm w_await wareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     d/s     dkB/s   drqm/s  %drqm d_await dareq-sz Device
    0.00      0.00     0.00   0.00    0.00     0.00 sda2
    0.00      0.00     0.00   0.00    0.00     0.00 sda3
    0.00      0.00     0.00   0.00    0.00     0.00 sda4
    0.00      0.00     0.00   0.00    0.00     0.00 sda5
    0.00      0.00     0.00   0.00    0.00     0.00 sda6

     f/s f_await  aqu-sz  %util Device
    0.00    0.00    0.00   0.00 sda2
    0.00    0.00    0.00   0.00 sda3
    0.00    0.00    0.00   0.00 sda4
    0.00    0.00    0.00   0.00 sda5
    0.00    0.00    0.00   0.00 sda6

^C

```
I'm using iostat to display i/o statistics of devices. It does not recognize ZFS pools names, So I give it the disk/partition names I want to watch, that relate to the partitions the pools are using. It is taking samples at 2 second intervals. It is displaying to screen, and writing to a log file, so I can review it. Use <Cntrl><C> to stop it after about 2 minutes or so.

Run this when it is slow, so maybe we can see what is going on.

---

### Post by tkae-lp on 2024-01-28
I agree, it's very puzzling.

I'll monitor over the next few days and give you some iostat logs!

---

### Post by MAFoElffen on 2024-01-28
Thank you. Very curious in seeing those samplings. They should be small enough to upload as text file attachments. But if not, then upload them to pastebins at paste.ubuntu.com with an expiration set to them of 1 year or less. I'm not a fan of taking up space for something like that forever.

---

### Post by tkae-lp on 2024-01-28
Will do. 1 year is very generous :D I was going to do a month! LOL

Whatever this thing is, it must have ears and they must be burning... I've had perfect performance today! Skipping forwards and back in 4K no problem at the moment...

---

### Post by MAFoElffen on 2024-01-28
Dang! It's trying to hide from us... LOL.

---

### Post by tkae-lp on 2024-01-30
Wait! I have something! Maybe... 

Here is the log: [https://paste.ubuntu.com/p/ZW3PT9qdCN/](https://paste.ubuntu.com/p/ZW3PT9qdCN/)

I've monitored every connected disk.

Disk key:

```
nvme0n1p1 = zfs zraid2 cache
nvme0n1p2 = zfs zraid2 slogs
sda1 = zfs zraid2 data disk
sdb1 = zfs zraid2 data disk
sdc1 = zfs zraid2 data disk
sdd1 = zfs zraid2 data disk
sde1 = zfs zraid2 data disk
sdf1 = zfs zraid2 data disk
sdg1 = zfs zraid2 data disk
sdh1 = zfs zraid2 data disk
sdi1 = 500GB OS SSD
sdj1 = 500GB temp downloads disk
```

Continuing to monitor....

---

### Post by #&amp;thj^% on 2024-01-30
What's heat like on all drives?

I've had mine under a  moderate load for a couple hours now:
```
sudo smartctl -a /dev/nvme0n1p1 |grep Temperature
Temperature:                        32 Celsius
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0
Temperature Sensor 1:               32 Celsius
Temperature Sensor 2:               33 Celsius

```

---

### Post by MAFoElffen on 2024-01-30
I'm starting to see a pattern there... 

First, this is what these columns mean:
> 
r_await is the average time (in milliseconds) for read requests issued to the device to be served. This includes the time spent by the requests in queue and the time spent servicing them.

w_await is the average time (in milliseconds) for write requests issued to the device to be served. This includes the time spent by the requests in queue and the time spent servicing them.

Look at the consistently high values for /dev/sdf1 in those two columns. That disk is only 1 disk in an 8 disk RAIDZ2 array right?

You would expect the load there would be balanced between all the disks of the array, not just one.

First I would use smartmon tools to confirm the health of that drive. If it is good, then I would move the data off the array then write it back to it. That way the data is confirmed as no fragmentation and written equally between all the drives. 

To do that though... For that much data, that is going to take some time and resources.

EDIT: Sorry about that news. Please, both of you look at that with that understanding of what that means, and see if you reach the same conclusion.

---

### Post by #&amp;thj^% on 2024-01-30
Yeppers that's a good spot MAFoElffen

---

### Post by tkae-lp on 2024-01-30
Temps of array disks:

```

sda1 =35c
sdb1 = 36c
sdc1 = 34c
sdd1 = 32c
sde1 = 31c
sdf1 = 33c
sdg1 = 31c
sdh1 = 32c
```

Yes, sdf is in the array, and does seem to be the only one in the array with issues.

But it's smart checks out - no errors. It is one of the newer drives - I had to replace 2 in the history of the pool.

Some info for sdf:

```
Complete SCT temperature log:

SCT Status Version:                  3
SCT Version (vendor specific):       522 (0x020a)
Device State:                        Active (0)
Current Temperature:                    32 Celsius
Power Cycle Min/Max Temperature:     29/35 Celsius
Lifetime    Min/Max Temperature:     19/46 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         3 minutes
Temperature Logging Interval:        59 minutes
Min/Max recommended Temperature:     14/55 Celsius
Min/Max Temperature Limit:           10/60 Celsius
Temperature History Size (Index):    128 (41)
```

And smart stat for sdf:

```
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-92-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate BarraCuda 3.5
Device Model:     ST4000DM004-2CV104
Serial Number:    ZTT4XXXX
LU WWN Device Id: 5 000c50 0e466fde3
Firmware Version: 0001
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5425 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Jan 31 02:13:03 2024 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
DSN feature is:   Unavailable
ATA Security is:  Disabled, frozen [SEC2]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 496) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x30a5)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR--   076   064   006    -    42410760
  3 Spin_Up_Time            PO----   097   097   000    -    0
  4 Start_Stop_Count        -O--CK   100   100   020    -    50
  5 Reallocated_Sector_Ct   PO--CK   100   100   010    -    0
  7 Seek_Error_Rate         POSR--   093   060   045    -    1964192642
  9 Power_On_Hours          -O--CK   089   089   000    -    10197 (64 162 0)
 10 Spin_Retry_Count        PO--C-   100   100   097    -    0
 12 Power_Cycle_Count       -O--CK   100   100   020    -    50
183 Runtime_Bad_Block       -O--CK   100   100   000    -    0
184 End-to-End_Error        -O--CK   100   100   099    -    0
187 Reported_Uncorrect      -O--CK   100   100   000    -    0
188 Command_Timeout         -O--CK   100   096   000    -    0 114 177
189 High_Fly_Writes         -O-RCK   100   100   000    -    0
190 Airflow_Temperature_Cel -O---K   068   054   040    -    32 (Min/Max 29/35)
191 G-Sense_Error_Rate      -O--CK   100   100   000    -    0
192 Power-Off_Retract_Count -O--CK   100   100   000    -    390
193 Load_Cycle_Count        -O--CK   100   100   000    -    493
194 Temperature_Celsius     -O---K   032   046   000    -    32 (0 19 0 0 0)
195 Hardware_ECC_Recovered  -O-RC-   076   064   000    -    42410760
197 Current_Pending_Sector  -O--C-   100   100   000    -    0
198 Offline_Uncorrectable   ----C-   100   100   000    -    0
199 UDMA_CRC_Error_Count    -OSRCK   200   200   000    -    0
240 Head_Flying_Hours       ------   100   253   000    -    10170h+36m+58.864s
241 Total_LBAs_Written      ------   100   253   000    -    13331335686
242 Total_LBAs_Read         ------   100   253   000    -    85484145805
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O      5  Comprehensive SMART error log
0x03       GPL     R/O      5  Ext. Comprehensive SMART error log
0x04       GPL,SL  R/O      8  Device Statistics log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x08       GPL     R/O      2  Power Conditions log
0x09           SL  R/W      1  Selective self-test log
0x0c       GPL     R/O   2048  Pending Defects log
0x10       GPL     R/O      1  NCQ Command Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x21       GPL     R/O      1  Write stream error log
0x22       GPL     R/O      1  Read stream error log
0x24       GPL     R/O    512  Current Device Internal Status Data log
0x30       GPL,SL  R/O      9  IDENTIFY DEVICE data log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa1       GPL,SL  VS      24  Device vendor specific log
0xa2       GPL     VS    8160  Device vendor specific log
0xa6       GPL     VS     192  Device vendor specific log
0xa8-0xa9  GPL,SL  VS     136  Device vendor specific log
0xab       GPL     VS       1  Device vendor specific log
0xb0       GPL     VS    9048  Device vendor specific log
0xbd       GPL     VS       8  Device vendor specific log
0xbe-0xbf  GPL     VS   65535  Device vendor specific log
0xc0       GPL,SL  VS       1  Device vendor specific log
0xc1       GPL,SL  VS      16  Device vendor specific log
0xc3       GPL,SL  VS       8  Device vendor specific log
0xc4       GPL,SL  VS      24  Device vendor specific log
0xd1       GPL     VS     264  Device vendor specific log
0xd3       GPL     VS    1920  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (5 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Status Version:                  3
SCT Version (vendor specific):       522 (0x020a)
Device State:                        Active (0)
Current Temperature:                    32 Celsius
Power Cycle Min/Max Temperature:     29/35 Celsius
Lifetime    Min/Max Temperature:     19/46 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         3 minutes
Temperature Logging Interval:        59 minutes
Min/Max recommended Temperature:     14/55 Celsius
Min/Max Temperature Limit:           10/60 Celsius
Temperature History Size (Index):    128 (41)

Index    Estimated Time   Temperature Celsius
  42    2024-01-25 20:58    33  **************
  43    2024-01-25 21:57    33  **************
  44    2024-01-25 22:56    32  *************
  45    2024-01-25 23:55    33  **************
  46    2024-01-26 00:54    34  ***************
  47    2024-01-26 01:53    34  ***************
  48    2024-01-26 02:52    32  *************
  49    2024-01-26 03:51    33  **************
 ...    ..(  4 skipped).    ..  **************
  54    2024-01-26 08:46    33  **************
  55    2024-01-26 09:45    34  ***************
  56    2024-01-26 10:44    34  ***************
  57    2024-01-26 11:43    33  **************
 ...    ..(  7 skipped).    ..  **************
  65    2024-01-26 19:35    33  **************
  66    2024-01-26 20:34    34  ***************
 ...    ..(  3 skipped).    ..  ***************
  70    2024-01-27 00:30    34  ***************
  71    2024-01-27 01:29    33  **************
  72    2024-01-27 02:28    33  **************
  73    2024-01-27 03:27    32  *************
  74    2024-01-27 04:26    32  *************
  75    2024-01-27 05:25    33  **************
  76    2024-01-27 06:24    33  **************
  77    2024-01-27 07:23    33  **************
  78    2024-01-27 08:22    32  *************
  79    2024-01-27 09:21    32  *************
  80    2024-01-27 10:20    33  **************
  81    2024-01-27 11:19    32  *************
 ...    ..(  4 skipped).    ..  *************
  86    2024-01-27 16:14    32  *************
  87    2024-01-27 17:13    33  **************
  88    2024-01-27 18:12    32  *************
 ...    ..(  2 skipped).    ..  *************
  91    2024-01-27 21:09    32  *************
  92    2024-01-27 22:08    31  ************
  93    2024-01-27 23:07    32  *************
 ...    ..( 18 skipped).    ..  *************
 112    2024-01-28 17:48    32  *************
 113    2024-01-28 18:47    33  **************
 114    2024-01-28 19:46    33  **************
 115    2024-01-28 20:45    33  **************
 116    2024-01-28 21:44    32  *************
 ...    ..(  2 skipped).    ..  *************
 119    2024-01-29 00:41    32  *************
 120    2024-01-29 01:40    33  **************
 ...    ..(  6 skipped).    ..  **************
 127    2024-01-29 08:33    33  **************
   0    2024-01-29 09:32    34  ***************
   1    2024-01-29 10:31    34  ***************
   2    2024-01-29 11:30    34  ***************
   3    2024-01-29 12:29    33  **************
 ...    ..(  9 skipped).    ..  **************
  13    2024-01-29 22:19    33  **************
  14    2024-01-29 23:18    34  ***************
  15    2024-01-30 00:17    33  **************
  16    2024-01-30 01:16    34  ***************
  17    2024-01-30 02:15    33  **************
 ...    ..(  5 skipped).    ..  **************
  23    2024-01-30 08:09    33  **************
  24    2024-01-30 09:08    34  ***************
 ...    ..(  2 skipped).    ..  ***************
  27    2024-01-30 12:05    34  ***************
  28    2024-01-30 13:04    33  **************
 ...    ..( 12 skipped).    ..  **************
  41    2024-01-31 01:51    33  **************

SCT Error Recovery Control command not supported

Device Statistics (GP Log 0x04)
Page  Offset Size        Value Flags Description
0x01  =====  =               =  ===  == General Statistics (rev 1) ==
0x01  0x008  4              50  ---  Lifetime Power-On Resets
0x01  0x010  4           10197  ---  Power-on Hours
0x01  0x018  6     13330824526  ---  Logical Sectors Written
0x01  0x020  6       385929805  ---  Number of Write Commands
0x01  0x028  6     85484126939  ---  Logical Sectors Read
0x01  0x030  6       996034335  ---  Number of Read Commands
0x01  0x038  6               -  ---  Date and Time TimeStamp
0x03  =====  =               =  ===  == Rotating Media Statistics (rev 1) ==
0x03  0x008  4           10192  ---  Spindle Motor Power-on Hours
0x03  0x010  4           10191  ---  Head Flying Hours
0x03  0x018  4             493  ---  Head Load Events
0x03  0x020  4               0  ---  Number of Reallocated Logical Sectors
0x03  0x028  4               0  ---  Read Recovery Attempts
0x03  0x030  4               0  ---  Number of Mechanical Start Failures
0x03  0x038  4               0  ---  Number of Realloc. Candidate Logical Sectors
0x03  0x040  4             390  ---  Number of High Priority Unload Events
0x04  =====  =               =  ===  == General Errors Statistics (rev 1) ==
0x04  0x008  4               0  ---  Number of Reported Uncorrectable Errors
0x04  0x010  4             176  ---  Resets Between Cmd Acceptance and Completion
0x05  =====  =               =  ===  == Temperature Statistics (rev 1) ==
0x05  0x008  1              32  ---  Current Temperature
0x05  0x010  1              33  ---  Average Short Term Temperature
0x05  0x018  1              32  ---  Average Long Term Temperature
0x05  0x020  1              46  ---  Highest Temperature
0x05  0x028  1               0  ---  Lowest Temperature
0x05  0x030  1              44  ---  Highest Average Short Term Temperature
0x05  0x038  1              30  ---  Lowest Average Short Term Temperature
0x05  0x040  1              40  ---  Highest Average Long Term Temperature
0x05  0x048  1              32  ---  Lowest Average Long Term Temperature
0x05  0x050  4               0  ---  Time in Over-Temperature
0x05  0x058  1              60  ---  Specified Maximum Operating Temperature
0x05  0x060  4               0  ---  Time in Under-Temperature
0x05  0x068  1               0  ---  Specified Minimum Operating Temperature
0x06  =====  =               =  ===  == Transport Statistics (rev 1) ==
0x06  0x008  4             430  ---  Number of Hardware Resets
0x06  0x010  4              74  ---  Number of ASR Events
0x06  0x018  4               0  ---  Number of Interface CRC Errors
                                |||_ C monitored condition met
                                ||__ D supports DSN
                                |___ N normalized value

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x000a  2           28  Device-to-host register FISes sent due to a COMRESET
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
```

My pool currently contains about 11.6TB. I have a 14TB drive I use to backup the essential parts of this pool. 

So you are saying since the SMART checks out, this is pool fragmentation? I can certainly backup and replace the data. Yes it will take a while, but I don't really care too much as long as it solves the problem. The pool is quite a few years old - but if pool fragmentation is responsible, it surprises me... is 2% really doing this?

```
NAME        SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
Tank         29T  16.3T  12.7T        -         -     2%    56%  1.00x    ONLINE  -

```

(Sorry I could be totally missing the point here - it's 2.30am....)

---

### Post by MAFoElffen on 2024-01-30
How long was it faulted before you changed in the new drive?

If a drive is faulted, then it stops adding new to that drive, but continues to write to the others, causing an imbalance between the drives. This in ZFS, also can happen if you add a new drive to a normal pool. The old drives have more on it already, as the new drive starts adding data. The algorithms of writing data try to balance the written data out, but that drive will be there with less data on it. Also if you change an option, like compression or encryption, the old written data, will be what the older option was when it was written, whereas anything after that change will be written with the new option(s). Some people also do this because of fragmentation, though I have not had a big enough problem with fragmentation. Now that they added the ability to add a drive to an existing array, some thing between old and new data.

The common way to correct that in all those circumstances is to rewrite the data to the pool so it gets re-balanced and/or written with the newer options. the reason this works, is that it writes the data back to all the drives in one fell swoop.

Here is an explanation: [https://serverfault.com/a/859223](https://serverfault.com/a/859223)

On the TrueNAS Forums, I did read mention ([https://www.truenas.com/community/threads/rebalancing-the-pool-but-how-to-get-the-dev-disk-by-id-disk1.100038/post-689468](https://www.truenas.com/community/threads/rebalancing-the-pool-but-how-to-get-the-dev-disk-by-id-disk1.100038/post-689468)) that some people used this to do ZFS rebalancing: [https://github.com/markusressel/zfs-inplace-rebalancing](https://github.com/markusressel/zfs-inplace-rebalancing) ... I have not tried that script. I usually just send/receive the data back and forth. Or if i am changing an option that only changes on a pool creation with that differing option, then I rsync a backup to a drive, destroy the pool, recreate it with the new options, then rsync it back into the new pool/datasets.

---

### Post by tkae-lp on 2024-01-30
The drive in question (sdf) was only faulted for a few hours before I noticed and shutdown the server. I didn't have a drive to hand so I ordered one, then powered on when it arrived and resilvered. In the history of the pool, only 2 drives have been replaced. I did the same for both, the server was shutdown to avoid unnecessary use.  In terms of when it was replaced... well over a year ago. And definitely months before the speed problem occurred. Compression has been lz4 throughout the history of the pool. 

I agree that this does seem like the next logical step... so next I will: 

1. Backup
2. Destroy 
3. Recreate
4. Restore

Give me a few days (or more, I am busy this week) and I will report back when completed. I will then start monitoring again.

However (as a side note): if this imbalance is the issue, this seems like a pretty big flaw in ZFS - one would think the resilvering process should take care of this? If this is the case, I must say, I'm a little disappointed. I am very surprised at the possibility that 2 drive replacements could require this action.... It doesn't seem that intelligent for such an amazing FS. IMHO, OpenZFS [moving forward] should have a "re-balance and defrag" option... preferably one that can be added/chained onto a scrub! Just my 2p..

---

### Post by MAFoElffen on 2024-01-30
To give you a peek at some of that going on...

If I do this:
```

mafoelffen@msi-ubuntu:~$ sudo zpool list -v
[sudo] password for mafoelffen: 
NAME                                                   SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool                                                 2.75G   707M  2.06G        -         -     2%    25%  1.00x    ONLINE  -
  nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part2  2.75G   707M  2.06G        -         -     2%  25.1%      -    ONLINE
dpool                                                  464G  2.10M   464G        -         -     0%     0%  1.00x    ONLINE  -
  nvme-PCIe_SSD_23011650000183-part1                   464G  2.10M   464G        -         -     0%  0.00%      -    ONLINE
hpool                                                  358G  2.75G   355G        -         -     0%     0%  1.00x    ONLINE  -
  nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part5   358G  2.75G   355G        -         -     0%  0.76%      -    ONLINE
kpool                                                  928G   429G   499G        -     1.36T     1%    46%  1.00x    ONLINE  -
  nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part6   464G   329G   135G        -         -     1%  71.0%      -    ONLINE
  nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W618194B-part1   464G  99.9G   364G        -     1.36T     2%  21.5%      -    ONLINE
rpool                                                  748G  22.5G   726G        -         -     3%     3%  1.00x    ONLINE  -
  nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part3   748G  22.5G   726G        -         -     3%  3.00%      -    ONLINE

```
I can see how much is written to each disk in a pool. If you look at the kpool, you can see that one disk was added after another so the older disk has more written to it.

But if I do this:
```

mafoelffen@Mikes-B460M:~$ sudo zpool list -v
[sudo] password for mafoelffen: 
NAME                                                    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool                                                  1.88G   305M  1.58G        -         -     0%    15%  1.00x    ONLINE  -
  0196ab45-3ee2-894e-b725-39560409109f                 1.88G   305M  1.58G        -         -     0%  15.9%      -    ONLINE
datapool                                               9.09T  2.19T  6.90T        -         -     4%    24%  1.00x    ONLINE  -
  raidz2-0                                             9.09T  2.19T  6.90T        -         -     4%  24.1%      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1      -      -      -        -         -      -      -      -    ONLINE
logs                                                       -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   9.50G   328K  9.50G        -         -     0%  0.00%      -    ONLINE
cache                                                      -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   1.25T  1.21G  1.25T        -         -     0%  0.09%      -    ONLINE
kpool                                                  7.27T  3.40T  3.86T        -         -     0%    46%  1.00x    ONLINE  -
  raidz2-0                                             7.27T  3.40T  3.86T        -         -     0%  46.8%      -    ONLINE
    nvme-eui.0025385a2140bd61-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385a21418769-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385a2141f4fc-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385b21407ef0-part1                        -      -      -        -         -      -      -      -    ONLINE
rpool                                                   920G  19.4G   901G        -         -     1%     2%  1.00x    ONLINE  -
  ae13efaa-d1cf-ec40-86a6-2883f0e07102                  920G  19.4G   901G        -         -     1%  2.11%      -    ONLINE

```
You can see that it doesn't show how much is written to disks or vdev or a RAIDZ array. It it's all a guess for those.

---

### Post by tkae-lp on 2024-01-31
But on that logic (older disk has more written to it) My case is the opposite - the disk that's flagging on my end is newer.

My output shows very little:

```

NAME                                                                 SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
Tank                                                                  29T  16.3T  12.7T        -         -     2%    56%  1.00x    ONLINE  -
  raidz2-0                                                            29T  16.3T  12.7T        -         -     2%  56.1%      -    ONLINE
    ata-ST4000DM000-1F2168_S300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM004-2CV104_ZTT4XXXX   <--- SDF                          -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM004-2CV104_ZTT4XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX                                     -      -      -        -         -      -      -      -    ONLINE
logs                                                                    -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0XXXXXXXX-part2   928G   164K   928G        -         -     0%  0.00%      -    ONLINE
cache                                                                   -      -      -        -         -      -      -      -  -
  nvme0n1p1                                                          931G   928G  3.31G        -         -     0%  99.6%      -    ONLINE
```

The original drives were Seagate ST4000DM000s, the 2 replacements are ST4000DM00**4**s

I still think it's crazy that the resilvering process doesn't do more to correct this sort of thing, or that there is no 're-balance' option ;D

In any case, I'll report back as soon as I have completed the backup/restore :)

---

### Post by tkae-lp on 2024-02-04
It's looking like I might have the time I need to do the backup/restore tomorrow. Quick question before I do: Is it that I am literally just copying off then back onto the array or should I destroy then recreate it in the process?

---

### Post by MAFoElffen on 2024-02-05
It needs to write as new so if not destroying the pool, then destroying the filesystem dataset within the pool would get rid of the data written to it. Then you would not have to recreate the pool itself, right? That would save, what, one to two steps of many? I usually use rsync for that...

Or... if you do a recursive snapshot of the pool (-r), then send a full stream (-R)... Check to ensure it received a full stream... Then send/receive it back... It should overwrite the old data.

---

### Post by tkae-lp on 2024-02-05
I'm on it. It's taking a LONG time.... Long in the kind of way that makes me nervous. If anything else, this is a good time to be backing up!

Edit: Quick question:

```
logs                                                                    -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_980_PRO_with_Heatsink_2TB_S6WRNS0W5XXXXXX-part2   928G   132K   928G        -         -     0%  0.00%      -    ONLINE

```

Does this mean that only 132K is being used on this partition? If so, that's a hideous waste of 1TB :D Maybe I should swap it out for something smaller?

Edit2: Ok, rsync is doing my head in. Truth be told, I have a lot more files than the last time I backed up - a lot of music files and tiny metadata files. It's been assessing the files for about 5 hours..... The array doesn't contain mission critical stuff, so I'll hold my hands up and say I haven't backed it up for some time, the last time I did, it definitely did not take this long.

I've been looking at ZFS send/recv which I haven't used before. From what I can tell, I snap the pool, send it, rename mount point, then snap it on the other end to send back?

```
zfs send Tank/Docker@before_erase | pv | zfs receive Tank-Backup/Docker
```

I'll start with something small!

Edit3: Sorry, I missed what you said about -r and -R... we are copying now.....

```
zfs send Tank@before_erase_20240206 -R | pv | zfs receive -F Tank-Backup
```

---

### Post by MAFoElffen on 2024-02-06
You would use either a full snapshot with Send/Receive... Or an rsync backup to somewhere. Both are not needed. Right? That would result in two "separate" backups of the same thing. I mean, that would be safer, but duplicating your efforts.

---

### Post by tkae-lp on 2024-02-06
Sorry my previous post probably made it look like I am doing both. I've ditched rsync because for whatever reason it was too slow.

I'm just using send/recv now. By full snapshot you mean using the -r flag right? I've never used this before so I hope this is right. I've only ever snapped the tank and sub vols individually. 

This is what I've done:

```
zfs snapshot -r Tank@before_erase_20240206
```

```
zfs send Tank@before_erase_20240206 -R | pv | zfs receive -F Tank-Backup
```

It's about half way...

```
5.92TiB 12:52:20 [ 158MiB/s] [       <=>                   ]
```

It must be on some of the larger media files right now because the speed has picked up quite a bit.

---

### Post by MAFoElffen on 2024-02-06
The -r flag on zfs snapshot means recursive. That will create snapshots recursively of the current and all descendent datasets underneath what you asked for.

The -R flag on zfs send will will replicate the specified file system, and all the descendant file systems, up to when the named snapshot was taken. That is what you need to restore it from blank. If you do not do that, it will only send the changes since the snapshot, not the actual filesystem... And you would not have everything.

That is why I asked you to recheck the sizes of what is "sent", so you can double-check that you have a good backup.

These are the options I use for my full backups. Then in between, I use snapshots of the changes to do incrementals.

---

### Post by tkae-lp on 2024-02-06
Ok, so what I am doing is correct? 

1. I snapped the entire tank using -r
2. Then sent using -R

I will mount the vols after completion and check. It certainly appears to be sending the lot. It's copied 7.23TiB so far.

---

### Post by MAFoElffen on 2024-02-06
LOL. Yes.

---

### Post by tkae-lp on 2024-02-06
:biggrin: Ok fab. You'll have to excuse the obviously daft questions - I have sleep issues and right now they are bad. A daft question is less daft if it saves a ton of data and 24 hours ;D

Getting there!

```
7.85TiB 16:39:37 [ 130MiB/s]
```

---

### Post by tkae-lp on 2024-02-06
Ok, so this is after the send:

```
~ » zfs list
NAME                       USED  AVAIL     REFER  MOUNTPOINT
Tank                      11.3T  9.03T     11.0T  /mnt/Tank
Tank-Backup               11.3T  3.08T     11.0T  /mnt/Tank
Tank-Backup/Docker        16.3G  3.08T     16.3G  /mnt/Docker
Tank-Backup/Proxmox       14.9G  3.08T     14.9G  /mnt/Proxmox
Tank/Docker               17.0G  9.03T     16.9G  /mnt/Docker
Tank/Proxmox              15.5G  9.03T     15.5G  /mnt/Proxmox
```

After mount point reassignment:

```
zfs list
NAME                       USED  AVAIL     REFER  MOUNTPOINT
Tank                      11.3T  9.03T     11.0T  /mnt/Tank
Tank-Backup               11.3T  3.08T     11.0T  /mnt/Tank-Backup
Tank-Backup/Docker        16.3G  3.08T     16.3G  /mnt/Tank-Backup-Docker
Tank-Backup/Proxmox       14.9G  3.08T     14.9G  /mnt/Tank-Backup-Proxmox
Tank/Docker               17.0G  9.03T     16.9G  /mnt/Docker
Tank/Proxmox              15.5G  9.03T     15.5G  /mnt/Proxmox

```

The main tank looks like its size matches, but not the sub vols... what do I do? Could this be trash and temp files?

---

### Post by MAFoElffen on 2024-02-07
You could check with du right? Using the '--exclude' flag

---

### Post by tkae-lp on 2024-02-07
*facepalm* I didn't even think of du.. I had tunnel vision and was thinking there must be some ZFS command. I've had like an hours sleep in the last 36 hours... probably not the right time to be doing this, but I'll just double check everything I type!

It's looking good:

```
du -sh --exclude "./.*" --block-size=1G /mnt/Tank /mnt/Tank-Backup /mnt/Docker /mnt/Tank-Backup-Docker

11220    /mnt/Tank
11221    /mnt/Tank-Backup
17    /mnt/Docker
17    /mnt/Tank-Backup-Docker
```

Looks like I'm ready to destroy & recreate the pool then send back.

Edit:

```
zfs send Tank-Backup@before_erase_20240206 -R | pv | zfs receive Tank -F
7.24GiB 0:00:37 [ 228MiB/s] [ <=>                                                           ]

```

And we're off!

Edit2:

Having not used ZFS send/recv before, I can say that I am a convert based on this experience! It's made life so much easier than rsync, and it's way quicker for the data I have here. Another new thing taken away from this whole experience. Great stuff.

---

### Post by tkae-lp on 2024-02-08
Finally.... restoring took quite a bit longer than the backup:

Backup:

```
11.4TiB 24:48:24 [ 134MiB/s]
```

Restore:

```
11.4TiB 31:40:01 [ 105MiB/s]
```

After reassigning mount points, exporting the backup and exporting/importing the pool...

```
  pool: Tank
 state: ONLINE
config:

    NAME                                 STATE     READ WRITE CKSUM
    Tank                                 ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        ata-ST4000DM000-1F2168_S300XXXX  ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX  ONLINE       0     0     0
        ata-ST4000DM004-2CV104_ZTT4XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
        ata-ST4000DM000-1F2168_W300XXXX  ONLINE       0     0     0
    logs    
      nvme0n1p2                          ONLINE       0     0     0
    cache
      nvme0n1p1                          ONLINE       0     0     0

errors: No known data errors
```

```
NAME                                  SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
Tank                                 29.1T  16.0T  13.1T        -         -     0%    54%  1.00x    ONLINE  -
  raidz2-0                           29.1T  16.0T  13.1T        -         -     0%  54.8%      -    ONLINE
    ata-ST4000DM000-1F2168_S300XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM004-2CV104_ZTT4XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM004-2CV104_ZTT4XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX      -      -      -        -         -      -      -      -    ONLINE
    ata-ST4000DM000-1F2168_W300XXXX      -      -      -        -         -      -      -      -    ONLINE
logs                                     -      -      -        -         -      -      -      -  -
  nvme0n1p2                           928G      0   928G        -         -     0%  0.00%      -    ONLINE
cache                                    -      -      -        -         -      -      -      -  -
  nvme0n1p1                           931G     8K   931G        -         -     0%  0.00%      -    ONLINE

```

I guess now I just use the pool as normal and monitor to see if the same issue occurs! Crossing all fingers!

Edit:

```
   READ: bw=4448MiB/s (4664MB/s), 4448MiB/s-4448MiB/s (4664MB/s-4664MB/s), io=10.0GiB (10.7GB), run=2302-2302msec

```

```
  WRITE: bw=808MiB/s (847MB/s), 808MiB/s-808MiB/s (847MB/s-847MB/s), io=10.0GiB (10.7GB), run=12678-12678msec


```

---

### Post by MAFoElffen on 2024-02-10
Dang. That took a while. I was wondering if everything was okay...

Crossing fingers with you!!!

---

### Post by tkae-lp on 2024-02-19
> **MAFoElffen said:**
> Dang. That took a while. I was wondering if everything was okay...

Crossing fingers with you!!!

Thanks! Yeah it did a bit.... glad I didn't stick with rsync, it was still looking at what to do 5 hours in! I'm a ZFS send/recv convert lol

Sorry I haven't replied sooner - the last week has been busy (schools were off in the UK). 

I am still monitoring and so far things seem to be good:

```
WRITE: bw=1552MiB/s (1627MB/s), 1552MiB/s-1552MiB/s (1627MB/s-1627MB/s), io=10.0GiB (10.7GB), run=6600-6600msec

```

```
READ: bw=3417MiB/s (3583MB/s), 3417MiB/s-3417MiB/s (3583MB/s-3583MB/s), io=10.0GiB (10.7GB), run=2997-2997msec
```

Watch this space.....

---

### Post by tkae-lp on 2024-04-17
Right so hello again! 

My apologies for taking almost 2 months to reply this time, but I think we can probably all agree that I have given it more than enough time to test lol

The good news is that* I haven't had any issues since my last post*. *yay* none at all ;) everything is playing like a champ.

So this time I think we can definitely mark this as solved. 

I would like to thank both of you again for all your time and effort troubleshooting this, it means a lot and I thoroughly appreciate it. It's been total bliss clicking on something and it actually playing without constantly stopping!

I have also learnt a great deal throughout this endeavour and I would also like to thank you both for that again also. 

I'm looking forward to [s]Numbat[/s] Noble, and I will see you guys for the next adventure :)

---

### Post by #&amp;thj^% on 2024-04-20
We very much appreciate the kind feedback, and MAFoElffen did most of the heavy lifting here. :)

As far as 24.04 LTS goes I'd wait it out for a few months after it's release before *any* upgrade plans, this one has proven to have way too many moving pieces in progress.  
Just a heads up is all.

---

### Post by tkae-lp on 2024-04-23
No problem :) regardless of how much heavy lifting was done, I still  appreciate you taking your free time to help me out :-) without people  like you on forums, I'd be scratching my head and sobbing in a corner! :razz:

Thanks  for the heads up - in fact, when everything is working, it's usually  the EoL prompt that causes me to upgrade (as it was with Bionic to  Jammy) so I'll most likely be on Jammy for a while before moving to  Noble!

Edit:

I've come across a couple of other forum/reddit posts with users of the Asus variant of this board (X99WS) having issues with memory being recognised - Usually RDIMMs (like I dealt with here) so since I had such an issue with my ASRock variant of the X99 chip set, I will post this here again for others if they come across it:

_You absolutely need to match manufacturer, rank and model number and in most cases part number. If your part numbers are one digit out (different at the end), ie. G, J, K like the micron modules I listed in this thread, you absolutely must make sure that like for like part numbers are paired in the recommended module add/placement order in the manual or at the very least quad channel will not work - and worst case they probably will not be detected. After correcting modules and positioning, a CMOS reset by means of the on board jumper must be performed. Et Voila!_

---

