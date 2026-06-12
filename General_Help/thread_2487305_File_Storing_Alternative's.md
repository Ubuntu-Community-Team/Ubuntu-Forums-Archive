---
title: "File Storing Alternative's"
date: 2023-05-30
forum: General Help
---

### Post by wyattwhiteeagle on 2023-05-30
I'm accustomed to storing my file's on a flashdrive, which mounts on media.
External HDD/SSD also mounts on media.

I need a better alternative for storing my files.

Any idea's?

---

### Post by sudodus on 2023-05-30
Hard disk drives and SSDs are much better alternatives than pendrives alias flashdrives because the electronics and memory cells (in the devices) are much more reliable and faster too. This is true both when connected internally and externally.

An alternative is to use some kind of storage in the internet cloud, but there are probably limits to much you can store this way (size and bandwidth limits). One way to use this kind of storage is to backup only the personal files that you cannot afford to lose.

---

### Post by wyattwhiteeagle on 2023-05-30
> **sudodus said:**
> ...One way to use this kind of storage is to backup only the personal files that you cannot afford to lose.
That being said, what are some of my options?

How would I check the bandwidth I'm currently using?

The files have to be accessible from a Windows system as well, as my fiance uses Windows and there's times when I can't get to the internet...wired or wifi.
We connect thru Wifi.

---

### Post by sudodus on 2023-05-30
You can check the bandwidth by timing (more or less manually) the transfer of a fairly big file.

If you need the data, when there is no internet connection, you need own physical storage, and if you must also bring it when you travel, I suggest a USB SSD (because a HDD is sensitive to mechanical shock). It is a good idea to have two similar devices (to have a double backup).

---

### Post by mIk3_08 on 2023-05-30
I agree with sudodus. SSD is more handy than HDD. More safer to use on USB enclosure. I have been using it for a long time now. In my case, it is tested when storing important data. Very safe and fast transferring important data. Regards and cheers.

---

### Post by wyattwhiteeagle on 2023-05-30
> **sudodus said:**
> You can check the bandwidth by timing (more or less manually) the transfer of a fairly big file.

If you need the data, when there is no internet connection, you need own physical storage, and if you must also bring it when you travel, I suggest a USB SSD (because a HDD is sensitive to mechanical shock). It is a good idea to have two similar devices (to have a double backup).

If I were to put all of my fiance's and my files, and included system data files, into one folder...that folder might be around...64-128gb...give or take.
Would that be considered a "fairly big file" if it were compressed (archived)?

---

### Post by aljames2 on 2023-05-30
Portable data and backups are not the same.  As mentioned you will want to use separate devices for your backup storage.  Your "backup storage" devices will typically be internal SSDs or HDDs.  Having a third copy on an encrypted portable HDD or SSD in an enclosure that you keep offsite in a safe place is also not a bad idea.  Your fiance will likely not be using your backups, neither will you unless something bad happens and you need to rely on them.

The reason a lot of people use the pendrives is because data is stored using the  FAT32 (or similar) filesystem which can be easily shared between windows & linux systems. Both OSs can work with this.  NTFS is another filesystem that can work on both.  Smaller, non-essential, non-personal, non-system data files.

usb SSDs or HDDs in an enclosure can also work for portability of larger media such as photos, videos, music, movies, or other non-essential data, etc.

If we are talking two remote locations and you want to set up remote access for your fiance to your system, then we get in to remote SSH or VPNs.  Simpler for her may be a Cloud service for non-personal data, or better may be to make a portable SSD or HDD as discussed and take it to her.

---

### Post by sudodus on 2023-05-31
> **wyattwhiteeagle said:**
> If I were to put all of my fiance's and my files, and included system data files, into one folder...that folder might be around...64-128gb...give or take.
Would that be considered a "fairly big file" if it were compressed (archived)?

I would consider that a "really big file". You can test the bandwidth with a smaller file, maybe 5 GiB. Be sure to include the time for flushing the buffers, otherwise you may overestimate the bandwidth.

I agree with the advice in the other replies.

Thinking about file system:

NTFS is a good alternative for files that must be available from Linux and Windows. Another alternative is exFAT. FAT32 has a file size limit of 4 GiB.

But if you have a lot of data that belong to your Ubuntu system, I would recommend a Linux file system, for example ext4, because it works faster (much faster than NTFS)  and more reliably when running with Ubuntu. You can also keep the ownership and permission settings if stored as separate files (good for incremental backup).

So you might want one partition with ext4 and one partition with NTFS in an external SSD.

---

### Post by ActionParsnip on 2023-05-31
Small file server

---

### Post by mIk3_08 on 2023-05-31
I agree with ActionParsnip. Renting server storage will do. The only disadvantage is that you always need internet to access it. But you can bring it anywhere in the world as long as you have internet and it is very safe. Regards and cheers.

---

### Post by ActionParsnip on 2023-05-31
Even a small pc with a large internal disk will do. Just remember to buy a USB drive to run backups to

---

### Post by MAFoElffen on 2023-06-01
I benchmark my storage pools with 2GiB and 10GiB files using 'fio'. I navigate to a directory inside the mount, then do
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
I use the output from those to tune my storage pools. I pay attention to the write speed and IOPS stat's.

Example:
```

mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=35012: Thu Jun  1 00:39:42 2023
  write: IOPS=4602, BW=4602MiB/s (4826MB/s)(2048MiB/445msec); 0 zone resets
    slat (usec): min=104, max=1391, avg=214.97, stdev=55.59
    clat (usec): min=120, max=13067, avg=6691.32, stdev=1209.15
     lat (usec): min=500, max=13303, avg=6906.52, stdev=1238.12
    clat percentiles (usec):
     |  1.00th=[ 4621],  5.00th=[ 5735], 10.00th=[ 5735], 20.00th=[ 5800],
     | 30.00th=[ 5932], 40.00th=[ 6128], 50.00th=[ 6390], 60.00th=[ 6652],
     | 70.00th=[ 6915], 80.00th=[ 7373], 90.00th=[ 8291], 95.00th=[ 8848],
     | 99.00th=[11338], 99.50th=[11994], 99.90th=[13042], 99.95th=[13042],
     | 99.99th=[13042]
  lat (usec)   : 250=0.05%, 750=0.10%, 1000=0.05%
  lat (msec)   : 2=0.24%, 4=0.39%, 10=97.51%, 20=1.66%
  cpu          : usr=14.86%, sys=60.81%, ctx=1821, majf=14, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2048,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=4602MiB/s (4826MB/s), 4602MiB/s-4602MiB/s (4826MB/s-4826MB/s), io=2048MiB (2147MB), run=445-445msec


mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][w=982MiB/s][w=982 IOPS][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                         
TEST: (groupid=0, jobs=1): err= 0: pid=123287: Thu Jun  1 00:43:42 2023
  write: IOPS=853, BW=854MiB/s (895MB/s)(10.0GiB/11997msec); 0 zone resets
    slat (usec): min=91, max=3163, avg=771.30, stdev=385.38
    clat (nsec): min=1839, max=4106.6M, avg=36312672.61, stdev=223892894.67
     lat (usec): min=225, max=4107.5k, avg=37084.24, stdev=223925.93
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    7], 20.00th=[    8],
     | 30.00th=[    9], 40.00th=[   32], 50.00th=[   32], 60.00th=[   32],
     | 70.00th=[   32], 80.00th=[   32], 90.00th=[   33], 95.00th=[   35],
     | 99.00th=[   39], 99.50th=[   41], 99.90th=[ 4111], 99.95th=[ 4111],
     | 99.99th=[ 4111]
   bw (  MiB/s): min=  720, max= 4454, per=100.00%, avg=1246.12, stdev=916.60, samples=16
   iops        : min=  720, max= 4454, avg=1246.12, stdev=916.60, samples=16
  lat (usec)   : 2=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.11%, 10=31.50%, 20=0.49%, 50=67.51%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=619, max=619, avg=619.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  620],  5.00th=[  620], 10.00th=[  620], 20.00th=[  620],
     | 30.00th=[  620], 40.00th=[  620], 50.00th=[  620], 60.00th=[  620],
     | 70.00th=[  620], 80.00th=[  620], 90.00th=[  620], 95.00th=[  620],
     | 99.00th=[  620], 99.50th=[  620], 99.90th=[  620], 99.95th=[  620],
     | 99.99th=[  620]
  cpu          : usr=2.96%, sys=20.59%, ctx=61303, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.2%, 32=99.7%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=854MiB/s (895MB/s), 854MiB/s-854MiB/s (895MB/s-895MB/s), io=10.0GiB (10.7GB), run=11997-11997msec

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=264386: Thu Jun  1 00:45:48 2023
  write: IOPS=3043, BW=3043MiB/s (3191MB/s)(2048MiB/673msec); 0 zone resets
    slat (usec): min=101, max=1094, avg=325.64, stdev=214.57
    clat (usec): min=2, max=22865, avg=10144.35, stdev=6263.73
     lat (usec): min=380, max=23606, avg=10470.40, stdev=6456.96
    clat percentiles (usec):
     |  1.00th=[ 4228],  5.00th=[ 4228], 10.00th=[ 4293], 20.00th=[ 4293],
     | 30.00th=[ 4293], 40.00th=[ 4424], 50.00th=[ 6849], 60.00th=[12256],
     | 70.00th=[16188], 80.00th=[17957], 90.00th=[18744], 95.00th=[19268],
     | 99.00th=[20317], 99.50th=[21103], 99.90th=[22676], 99.95th=[22938],
     | 99.99th=[22938]
   bw (  MiB/s): min= 3404, max= 3404, per=100.00%, avg=3404.00, stdev= 0.00, samples=1
   iops        : min= 3404, max= 3404, avg=3404.00, stdev= 0.00, samples=1
  lat (usec)   : 4=0.05%, 500=0.05%, 1000=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=52.15%, 20=46.14%, 50=1.12%
  cpu          : usr=14.29%, sys=84.52%, ctx=80, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2048,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3043MiB/s (3191MB/s), 3043MiB/s-3043MiB/s (3191MB/s-3191MB/s), io=2048MiB (2147MB), run=673-673msec

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 10240MiB)
Jobs: 1 (f=1): [W(1)][100.0%][w=2462MiB/s][w=2462 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=275805: Thu Jun  1 00:46:01 2023
  write: IOPS=2435, BW=2436MiB/s (2554MB/s)(10.0GiB/4204msec); 0 zone resets
    slat (usec): min=97, max=11899, avg=383.31, stdev=232.31
    clat (nsec): min=1116, max=253101k, avg=12720685.63, stdev=14370522.79
     lat (usec): min=139, max=253240, avg=13104.48, stdev=14421.88
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    6],
     | 30.00th=[    7], 40.00th=[   11], 50.00th=[   13], 60.00th=[   15],
     | 70.00th=[   17], 80.00th=[   18], 90.00th=[   19], 95.00th=[   20],
     | 99.00th=[   24], 99.50th=[   35], 99.90th=[  253], 99.95th=[  253],
     | 99.99th=[  253]
   bw (  MiB/s): min= 2204, max= 3102, per=100.00%, avg=2492.25, stdev=337.76, samples=8
   iops        : min= 2204, max= 3102, avg=2492.25, stdev=337.76, samples=8
  lat (usec)   : 2=0.01%, 250=0.01%, 500=0.01%, 750=0.02%
  lat (msec)   : 2=0.07%, 4=0.12%, 10=38.46%, 20=58.13%, 50=2.87%
  lat (msec)   : 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=465, max=465, avg=465.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  466],  5.00th=[  466], 10.00th=[  466], 20.00th=[  466],
     | 30.00th=[  466], 40.00th=[  466], 50.00th=[  466], 60.00th=[  466],
     | 70.00th=[  466], 80.00th=[  466], 90.00th=[  466], 95.00th=[  466],
     | 99.00th=[  466], 99.50th=[  466], 99.90th=[  466], 99.95th=[  466],
     | 99.99th=[  466]
  cpu          : usr=14.85%, sys=75.61%, ctx=2020, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.2%, 32=99.7%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2436MiB/s (2554MB/s), 2436MiB/s-2436MiB/s (2554MB/s-2554MB/s), io=10.0GiB (10.7GB), run=4204-4204msec

```
EDIT:
IMHO-- I consider anything on a Flash Drive as being "Temporary", disposable and of little value. That is how little I trust Flash Drives for long-term storage...

---

### Post by wyattwhiteeagle on 2023-06-24
Some things I don't mind the world knowing, while other things are more personal than that.


With that in mind, what all should I check in determining which specific internet cloud storage I should choose?
I don't want any hidden fee's, data leaks, etc.
I also don't want my info sold to other companies (if that may be an issue)

---

### Post by TheFu on 2023-06-24
For storage that is written once, but read often, not constantly updated, then a cheap flash drive is fine.  Be certain to use a file system that minimizes writes. On Linux, that's ext2 or f2fs.  

Alas, SSDs are getting cheaper so we can use them for external storage.

They are sold as external storage, but always at a premium price.  I find that I'm better off buying the SSD and enclosure to hold it separate.  Then I know the quality of the SSD and have expectations of 5+ yr warranties and performance.  The T1 line of SSD is one of the former, expensive, examples.

For external storage, say under 1TB, SSDs are becoming cheap enough to be the best option.  This week, I've seen a number of Samsung 8xx and 9xx SSDs - some Pro and some not, but with both SATA and NVMe interfaces.  NVMe should be 10x faster than SATA, but if you are connecting to USB3 (5 Gbps) or USB 3.1gen1 (5 Gbps) or USB 3.1gen2 (10 Gbps) ports, only then does the NVMe vs SATA matter.

So, you get an m.2 NVMe Samsung PRO 1TB SSD for $60 and buy a reasonable quality m.2 external enclosure for 2280 SSDs for $20-$30. 
[https://slickdeals.net/f/16713074-1tb-samsung-980-nvme-internal-solid-state-drive-ssd-44-99-f-s-amazon](https://slickdeals.net/f/16713074-1tb-samsung-980-nvme-internal-solid-state-drive-ssd-44-99-f-s-amazon) is a $45 non-PRO Samsung NVMe 1TB SSD.  The PRO can be found for a little more. For USB use, I doubt it matters.

Then you create a GPT partition table and 1 partition.  Add a LUKS encryption container and create a file system inside it for your data. Many file managers will recognize LUKS containers and prompt for a passphrase to open them. Then will mount the file system as you expect.  You can even setup the host system with keys to automatically unlock the LUKS container, but only for that system.  So if the SSD enclosure is lost or stolen without the computer, all the data will be encrypted enough to keep the FBI out (assuming stupid passphrases aren't used).

I'd not use any cloudy storage, unless you pre-encrypt everything. Don't trust their app or some javascript tool to encrypt it on the way either.

It is best to assume everything in your storage has your bank and retirement account details.  It is just too easy for a judgement lapse to happen and something sensitive to leak.  As paranoid as I am, I assume this about myself as well.  We can do 10,000 things correct, but just 1 mistake can cause terrible loss.  As humans, most of us are, we will all make mistakes.

More on LUKS encryption and automatic opening using USB devices:
* Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
* Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
* Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)                   

A year ago, using an HDD for this stuff would have made more sense.  HDDs should be about 50% the price, but due to shipping costs and other logistical considerations, finding cheap 1TB HDDs that are fast will still run $40+, so it is hardly worth it when even a SATA SSD will be 2-5x faster than any external HDD.  BTW, the old USB thumb drives will usually be the slowest and most likely to fail of all three options.

All this reminds me. I need to pull a 512GB SATA m.2 SSD from _this_ system and put it into the external USB enclosure I bought for $11 to hold it.  It is a no-name enclosure. I haven't used it yet, so I don't feel good recommending it ... today.  Maybe in a year?  Last month, I did a fresh install and used a Samsung 980 m.2 1TB NVMe SSD.  It has more storage than I'll need, so I should probably pull the SATA SSD and use it for some other stuff.

The great thing about SATA SSDs is their SMART data has the full suite of information, unlike NVMe SSDs which provide extremely limited information. 

BTW, PNY sells 1TB SATA SSDs for a little less. These are 2.5in (laptop) versions, which would fit into any normal USB3 enclosure meant to be used by laptop HDDs.

If going with a new SSD and a new enclosure, at this point, I'd get a 10 Gbps enclosure even if the SSD performance isn't anywhere near that.  After all, reusing the enclosure with a newer SSD in 3 yrs would be a savings, right?

---

### Post by SeijiSensei on 2023-06-24
I bought one of these recently. It uses USB 3.0 and has more than enough bandwidth for video. At 14 TB, I expect it will be sufficient for my data storage needs even if I make it to my nineties.

[https://www.newegg.com/seagate-expansion-14tb-black/p/N82E16822184958?Item=N82E16822184958](https://www.newegg.com/seagate-expansion-14tb-black/p/N82E16822184958?Item=N82E16822184958)

It's now attached to this

[https://www.newegg.com/p/2SW-007T-00001?Item=9SIBF3CJ8J7324](https://www.newegg.com/p/2SW-007T-00001?Item=9SIBF3CJ8J7324)

which itself is connected to my 4K TV. I installed Kubuntu alongside the existing Win11 and set up the device to share the files on the external device to the rest of my network via NFS.

---

### Post by wyattwhiteeagle on 2023-06-24
Thank you for that.


Considering my recent USB flash drive situation...
( [https://ubuntuforums.org/showthread.php?t=2487301](https://ubuntuforums.org/showthread.php?t=2487301) )
Until I learn how to avoid a new fresh clean install rendering my flash drive useless or unreadable, I need a 3rd alternative for storing my files.


I believe it is something that is being done by the LiveUSB when installing, as well as something which I have been doing with the storage flash drive that I need better practices.
(Most likely it is something I'm doing or failing to do with the storage flash drive.)

Until then, internet cloud storage is my go-to.


> **TheFu said:**
> ...I'd not use any cloudy storage, unless you pre-encrypt everything...
Yes, of course, absolutely.
Not doing that seems to be just putting the info out there, even for shady people to render my entire life to be more harsh than it is now.

---

### Post by wyattwhiteeagle on 2023-07-27
Looks like something I need to start doing.
Installing fio is easy.
What do you mean by "inside the mount"?
Do you mean a USB flash drive or a directory under / or /home or either one?
Those commands, are they needing to be "tweaked" to work on my machine?
> **MAFoElffen said:**
> I benchmark my storage pools with 2GiB and 10GiB files using 'fio'. I navigate to a directory inside the mount, then do
```

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting

```
I use the output from those to tune my storage pools. I pay attention to the write speed and IOPS stat's.

Example:
```

mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=35012: Thu Jun  1 00:39:42 2023
  write: IOPS=4602, BW=4602MiB/s (4826MB/s)(2048MiB/445msec); 0 zone resets
    slat (usec): min=104, max=1391, avg=214.97, stdev=55.59
    clat (usec): min=120, max=13067, avg=6691.32, stdev=1209.15
     lat (usec): min=500, max=13303, avg=6906.52, stdev=1238.12
    clat percentiles (usec):
     |  1.00th=[ 4621],  5.00th=[ 5735], 10.00th=[ 5735], 20.00th=[ 5800],
     | 30.00th=[ 5932], 40.00th=[ 6128], 50.00th=[ 6390], 60.00th=[ 6652],
     | 70.00th=[ 6915], 80.00th=[ 7373], 90.00th=[ 8291], 95.00th=[ 8848],
     | 99.00th=[11338], 99.50th=[11994], 99.90th=[13042], 99.95th=[13042],
     | 99.99th=[13042]
  lat (usec)   : 250=0.05%, 750=0.10%, 1000=0.05%
  lat (msec)   : 2=0.24%, 4=0.39%, 10=97.51%, 20=1.66%
  cpu          : usr=14.86%, sys=60.81%, ctx=1821, majf=14, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2048,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=4602MiB/s (4826MB/s), 4602MiB/s-4602MiB/s (4826MB/s-4826MB/s), io=2048MiB (2147MB), run=445-445msec


mafoelffen@Mikes-B460M:/data$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
Jobs: 1 (f=1): [W(1)][100.0%][w=982MiB/s][w=982 IOPS][eta 00m:00s]
Jobs: 1 (f=1): [W(1)][100.0%][eta 00m:00s]                         
TEST: (groupid=0, jobs=1): err= 0: pid=123287: Thu Jun  1 00:43:42 2023
  write: IOPS=853, BW=854MiB/s (895MB/s)(10.0GiB/11997msec); 0 zone resets
    slat (usec): min=91, max=3163, avg=771.30, stdev=385.38
    clat (nsec): min=1839, max=4106.6M, avg=36312672.61, stdev=223892894.67
     lat (usec): min=225, max=4107.5k, avg=37084.24, stdev=223925.93
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    6], 10.00th=[    7], 20.00th=[    8],
     | 30.00th=[    9], 40.00th=[   32], 50.00th=[   32], 60.00th=[   32],
     | 70.00th=[   32], 80.00th=[   32], 90.00th=[   33], 95.00th=[   35],
     | 99.00th=[   39], 99.50th=[   41], 99.90th=[ 4111], 99.95th=[ 4111],
     | 99.99th=[ 4111]
   bw (  MiB/s): min=  720, max= 4454, per=100.00%, avg=1246.12, stdev=916.60, samples=16
   iops        : min=  720, max= 4454, avg=1246.12, stdev=916.60, samples=16
  lat (usec)   : 2=0.01%, 250=0.01%, 500=0.01%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.04%, 4=0.11%, 10=31.50%, 20=0.49%, 50=67.51%
  lat (msec)   : >=2000=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=619, max=619, avg=619.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  620],  5.00th=[  620], 10.00th=[  620], 20.00th=[  620],
     | 30.00th=[  620], 40.00th=[  620], 50.00th=[  620], 60.00th=[  620],
     | 70.00th=[  620], 80.00th=[  620], 90.00th=[  620], 95.00th=[  620],
     | 99.00th=[  620], 99.50th=[  620], 99.90th=[  620], 99.95th=[  620],
     | 99.99th=[  620]
  cpu          : usr=2.96%, sys=20.59%, ctx=61303, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.2%, 32=99.7%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=854MiB/s (895MB/s), 854MiB/s-854MiB/s (895MB/s-895MB/s), io=10.0GiB (10.7GB), run=11997-11997msec

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=2g --io_size=2g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 2048MiB)

TEST: (groupid=0, jobs=1): err= 0: pid=264386: Thu Jun  1 00:45:48 2023
  write: IOPS=3043, BW=3043MiB/s (3191MB/s)(2048MiB/673msec); 0 zone resets
    slat (usec): min=101, max=1094, avg=325.64, stdev=214.57
    clat (usec): min=2, max=22865, avg=10144.35, stdev=6263.73
     lat (usec): min=380, max=23606, avg=10470.40, stdev=6456.96
    clat percentiles (usec):
     |  1.00th=[ 4228],  5.00th=[ 4228], 10.00th=[ 4293], 20.00th=[ 4293],
     | 30.00th=[ 4293], 40.00th=[ 4424], 50.00th=[ 6849], 60.00th=[12256],
     | 70.00th=[16188], 80.00th=[17957], 90.00th=[18744], 95.00th=[19268],
     | 99.00th=[20317], 99.50th=[21103], 99.90th=[22676], 99.95th=[22938],
     | 99.99th=[22938]
   bw (  MiB/s): min= 3404, max= 3404, per=100.00%, avg=3404.00, stdev= 0.00, samples=1
   iops        : min= 3404, max= 3404, avg=3404.00, stdev= 0.00, samples=1
  lat (usec)   : 4=0.05%, 500=0.05%, 1000=0.05%
  lat (msec)   : 2=0.15%, 4=0.29%, 10=52.15%, 20=46.14%, 50=1.12%
  cpu          : usr=14.29%, sys=84.52%, ctx=80, majf=0, minf=12
  IO depths    : 1=0.1%, 2=0.1%, 4=0.2%, 8=0.4%, 16=0.8%, 32=98.5%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,2048,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=3043MiB/s (3191MB/s), 3043MiB/s-3043MiB/s (3191MB/s-3191MB/s), io=2048MiB (2147MB), run=673-673msec

mafoelffen@Mikes-B460M:/KVM_Pool$ fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 10240MiB)
Jobs: 1 (f=1): [W(1)][100.0%][w=2462MiB/s][w=2462 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=275805: Thu Jun  1 00:46:01 2023
  write: IOPS=2435, BW=2436MiB/s (2554MB/s)(10.0GiB/4204msec); 0 zone resets
    slat (usec): min=97, max=11899, avg=383.31, stdev=232.31
    clat (nsec): min=1116, max=253101k, avg=12720685.63, stdev=14370522.79
     lat (usec): min=139, max=253240, avg=13104.48, stdev=14421.88
    clat percentiles (msec):
     |  1.00th=[    5],  5.00th=[    5], 10.00th=[    5], 20.00th=[    6],
     | 30.00th=[    7], 40.00th=[   11], 50.00th=[   13], 60.00th=[   15],
     | 70.00th=[   17], 80.00th=[   18], 90.00th=[   19], 95.00th=[   20],
     | 99.00th=[   24], 99.50th=[   35], 99.90th=[  253], 99.95th=[  253],
     | 99.99th=[  253]
   bw (  MiB/s): min= 2204, max= 3102, per=100.00%, avg=2492.25, stdev=337.76, samples=8
   iops        : min= 2204, max= 3102, avg=2492.25, stdev=337.76, samples=8
  lat (usec)   : 2=0.01%, 250=0.01%, 500=0.01%, 750=0.02%
  lat (msec)   : 2=0.07%, 4=0.12%, 10=38.46%, 20=58.13%, 50=2.87%
  lat (msec)   : 500=0.30%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=465, max=465, avg=465.00, stdev= 0.00
    sync percentiles (nsec):
     |  1.00th=[  466],  5.00th=[  466], 10.00th=[  466], 20.00th=[  466],
     | 30.00th=[  466], 40.00th=[  466], 50.00th=[  466], 60.00th=[  466],
     | 70.00th=[  466], 80.00th=[  466], 90.00th=[  466], 95.00th=[  466],
     | 99.00th=[  466], 99.50th=[  466], 99.90th=[  466], 99.95th=[  466],
     | 99.99th=[  466]
  cpu          : usr=14.85%, sys=75.61%, ctx=2020, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.2%, 32=99.7%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10240,0,1 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=2436MiB/s (2554MB/s), 2436MiB/s-2436MiB/s (2554MB/s-2554MB/s), io=10.0GiB (10.7GB), run=4204-4204msec

```
EDIT:
IMHO-- I consider anything on a Flash Drive as being "Temporary", disposable and of little value. That is how little I trust Flash Drives for long-term storage...

---

### Post by sudodus on 2023-07-27
The mountpoint is the top level of a mounted file system. After 'cd' to the mountpoint or any subdirectory there, you are 'inside the mount' (at least that is how I would interpret it).

---

### Post by SeijiSensei on 2023-07-28
> **SeijiSensei said:**
> I bought one of these recently. It uses USB 3.0 and has more than enough bandwidth for video. At 14 TB, I expect it will be sufficient for my data storage needs even if I make it to my nineties.
One other thing. Since the storage device is directly connected to a Linux machine, it can provide file access via NFS for other *nix machines, and CIFS via Samba for Windows machines, which you said was a concern. The computer also shares these files using minidlna, which is a widely-supported protocol. My TV has a DLNA client built-in, and I'm sure many others do, too.

---

### Post by wyattwhiteeagle on 2023-07-31
Just for fun, I used the Downloads folder as the source directory inside the mount.
Then I ran the commands exporting to a text file on the Desktop.

These numbers may be only local.
Between the two info's, the terminal show's one number and the export shows a different number.

Which number would I use to tune the storage pools?
The terminal or the export?

I ran...
```
wyatt@wyatt-latitudee5400:~$    cd /home/wyatt/Downloads
wyatt@wyatt-latitudee5400:~/Downloads$    sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting &&   sudo fio --name TEST --eta-newline=5s --filename=temp.file --rw=write --size=10g --io_size=10g --blocksize=1024k --ioengine=libaio --fsync=10000 --iodepth=32 --direct=1 --numjobs=1 --runtime=60 --group_reporting > /home/wyatt/Desktop/Storage-Pool-Stats.txt
```
Terminal printed...
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process
TEST: Laying out IO file (1 file / 10240MiB)
Jobs: 1 (f=1): [W(1)][11.7%][w=65.1MiB/s][w=65 IOPS][eta 00m:53s]
Jobs: 1 (f=1): [W(1)][21.7%][w=63.1MiB/s][w=63 IOPS][eta 00m:47s] 
Jobs: 1 (f=1): [W(1)][31.7%][w=66.1MiB/s][w=66 IOPS][eta 00m:41s] 
Jobs: 1 (f=1): [W(1)][41.7%][w=65.1MiB/s][w=65 IOPS][eta 00m:35s] 
Jobs: 1 (f=1): [W(1)][51.7%][w=55.1MiB/s][w=55 IOPS][eta 00m:29s] 
Jobs: 1 (f=1): [W(1)][61.7%][w=65.0MiB/s][w=65 IOPS][eta 00m:23s] 
Jobs: 1 (f=1): [W(1)][71.7%][w=67.0MiB/s][w=67 IOPS][eta 00m:17s] 
Jobs: 1 (f=1): [W(1)][81.7%][w=67.1MiB/s][w=67 IOPS][eta 00m:11s] 
Jobs: 1 (f=1): [W(1)][90.0%][w=66.0MiB/s][w=66 IOPS][eta 00m:06s] 
Jobs: 1 (f=1): [W(1)][100.0%][w=43.0MiB/s][w=43 IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=1): err= 0: pid=2563: Mon Jul 31 00:28:28 2023
  write: IOPS=62, BW=62.5MiB/s (65.6MB/s)(3789MiB/60579msec); 0 zone resets
    slat (usec): min=132, max=532405, avg=1738.14, stdev=22788.09
    clat (msec): min=25, max=2985, avg=509.66, stdev=374.96
     lat (msec): min=26, max=2986, avg=511.40, stdev=375.27
    clat percentiles (msec):
     |  1.00th=[  133],  5.00th=[  264], 10.00th=[  309], 20.00th=[  384],
     | 30.00th=[  405], 40.00th=[  422], 50.00th=[  439], 60.00th=[  451],
     | 70.00th=[  472], 80.00th=[  506], 90.00th=[  634], 95.00th=[  852],
     | 99.00th=[ 2534], 99.50th=[ 2802], 99.90th=[ 2970], 99.95th=[ 2970],
     | 99.99th=[ 2970]
   bw (  KiB/s): min=36790, max=81920, per=100.00%, avg=64101.60, stdev=8598.18, samples=120
   iops        : min=   35, max=   80, avg=62.33, stdev= 8.37, samples=120
  lat (msec)   : 50=0.08%, 100=0.18%, 250=4.41%, 500=74.24%, 750=14.38%
  lat (msec)   : 1000=2.69%, 2000=1.11%, >=2000=2.90%
  cpu          : usr=1.45%, sys=1.45%, ctx=3436, majf=0, minf=13
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.4%, 32=99.2%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3789,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=62.5MiB/s (65.6MB/s), 62.5MiB/s-62.5MiB/s (65.6MB/s-65.6MB/s), io=3789MiB (3973MB), run=60579-60579msec

Disk stats (read/write):
  sda: ios=6/5034, merge=0/374, ticks=8424/2427219, in_queue=2442938, util=99.64%
wyatt@wyatt-latitudee5400:~/Downloads$
```
Export printed...
```
TEST: (g=0): rw=write, bs=(R) 1024KiB-1024KiB, (W) 1024KiB-1024KiB, (T) 1024KiB-1024KiB, ioengine=libaio, iodepth=32
fio-3.28
Starting 1 process

TEST: (groupid=0, jobs=1): err= 0: pid=2621: Mon Jul 31 00:29:29 2023
  write: IOPS=61, BW=62.0MiB/s (65.0MB/s)(3748MiB/60492msec); 0 zone resets
    slat (usec): min=104, max=467105, avg=1478.94, stdev=20542.18
    clat (msec): min=20, max=3037, avg=514.80, stdev=435.33
     lat (msec): min=20, max=3037, avg=516.29, stdev=435.61
    clat percentiles (msec):
     |  1.00th=[   73],  5.00th=[  215], 10.00th=[  279], 20.00th=[  347],
     | 30.00th=[  368], 40.00th=[  401], 50.00th=[  422], 60.00th=[  439],
     | 70.00th=[  481], 80.00th=[  518], 90.00th=[  667], 95.00th=[ 1334],
     | 99.00th=[ 2567], 99.50th=[ 2769], 99.90th=[ 2903], 99.95th=[ 3004],
     | 99.99th=[ 3037]
   bw (  KiB/s): min=32768, max=71823, per=100.00%, avg=63456.32, stdev=6476.03, samples=120
   iops        : min=   32, max=   70, avg=61.78, stdev= 6.29, samples=120
  lat (msec)   : 50=0.43%, 100=1.28%, 250=5.44%, 500=69.37%, 750=15.74%
  lat (msec)   : 1000=1.76%, 2000=2.21%, >=2000=3.76%
  cpu          : usr=1.37%, sys=1.27%, ctx=3507, majf=0, minf=15
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.2%, 16=0.4%, 32=99.2%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,3748,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=62.0MiB/s (65.0MB/s), 62.0MiB/s-62.0MiB/s (65.0MB/s-65.0MB/s), io=3748MiB (3930MB), run=60492-60492msec

Disk stats (read/write):
  sda: ios=1/4645, merge=0/93, ticks=2395/2223781, in_queue=2234584, util=99.80%
```

---

