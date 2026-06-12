---
title: "[SOLVED] Bonnie++ results faster write than read"
date: 2007-11-23
forum: General Help
---

### Post by Toet on 2007-11-23
Upgrading my computer for some years now, I ended up having 5 hard drives. I like to experiment, so I created a raid0 over the five disks. Curious for performance benchmark outcome, I run Bonnie++.

Besides it's really fast :), I get some non-expected output. I ran the test several times, with the same outcome, and it looks like it´s faster with reading than with writing. The sequential output (write if I'm correct) is 187Mb/s, the sequential input (read) is 106 Mb/s. I would expect that reading is faster than writing...

This thought is fed by other outcomes I've seen on the internet were the results are vice versa. 

Am I concluding wrong here, or is there something I'm doing wrong?

Results:

Version  1.03      ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
thuis            4G 42903  97 187178  78 43743  19 43029  91 106794  27 269.2   2
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
files:max:min        /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
thuis           512 35945  87 353033  97  5164  17 35585  86 518944  98  2754  11


By the way it's great fun a fast system like this, with almost ancient disks in the array. Guess it's not clever, save wise, to run raid0, but I backup daily.

Disks:

2 Seagate, 120GB IDE
2 Seagate, 120GB SATA
1 Samsung, 320GB SATAII

Individually the seagates score the same, sata and ide :) nice marketing thing SATA. With throughput of 40Mb/s, who needs 150 or even 300Mb/s.

---

### Post by misconfiguration on 2007-11-23
You could try tweaking the hdd's with hdparm.

---

### Post by Toet on 2007-11-23
hdparm: (first 2 disks ide, last 3 sata)
IO_support on SATA disks = 0 (default 16-bit) (which seems to be normal as hdparm is for ide drives, not for sata)

/dev/hdd1:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 16383/255/63, sectors = 234436482, start = 63

/dev/hdc1:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 16383/255/63, sectors = 234436482, start = 63

/dev/sda1:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234436482, start = 63

/dev/sdb1:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234436482, start = 63

/dev/sdc1:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 234372222, start = 63

What should I tweak?

---

### Post by misconfiguration on 2007-11-23
First I have a few things to say;

*Before any settings are tweaked with hdparm, make sure you are in init 1 (single-user-mode) to ensure you don't corrupt your data*

*Second, use my advice at your own risk, I don't want to be responsible for anything I suggest, so it's all on  you*

First I would start off by comparing read performance betwixt the drives
```
hdparm -t /dev/<hdd>
```

With IDE disks, hdparm will tell you what transfer mode is being used with your disks. With sATA drives, the drivers show the maximum transfer speed (bus transfer rate) during the boot process. Theoretically, that shouldn't have changed, but is an unlikely possibility of performance differences.

In your "write" tests, you should ensure that the "writes" are completed before they return -- i.e. use a "sync" command after the "dd" to ensure that the contents are actually written to disk, i.e. use:

```
sync;time bash -c "(dd if=/dev/zero of=bf bs=8k count=500000; sync)
```

Also you can check your /etc/fstab on your partitions to see if seek/write times are offset during mounting of the disks.

---

### Post by Toet on 2007-11-23
Write test gives 203MB/s:

sync;time bash -c "(dd if=/dev/zero of=bf bs=8k count=500000; sync)"
500000+0 records in
500000+0 records uit
4096000000 bytes (4,1 GB) gekopieerd, 20,196 seconden, 203 MB/s

real    0m24.875s
user    0m0.196s
sys     0m16.169s

Readtest (hdparm -t) give 55Mb/s for the 4 seagates each. This is normal, reading results on internet. Changing the multcount from 0 to 16 didn't gain anything. I think they are doing best at 55Mb/s. Not willing to alter the other settings, after reading the cautions. ;)
The samsung gives 86Mb/s, also good enough, considering the raid has to wait for the slower seagates.

Readtest (hdparm -t) for a logical volume on the raid0, give 150Mb/s.

All hdparm test ran 5 times for averages. No glitches in any of the runs,

So write 200Mb/s which is not to complain about. Read with 150Mb/s is slow, cause you would expect 5 times 55 = 275 - overhead (give or take a max of 75) should be at least 200 Mb/s,

I do not get your comment about the fstab and seek/write offset. Can you explain a bit more in detail what I should check/do there? Googling on fstab and offset gave no usable result.

---

### Post by Toet on 2007-11-23
Solved:

IDE disk where on same cable/controller. Split them up now. Read speeded up to 267 MB/s.

Now I hope it won't slow down when burning CD's ;)

---

### Post by fjgaude on 2007-11-26
What is the bus from which the disk controllers are being run, PCI, PCI-X or PCI-Express?

Which motherboard are you using?

Your Mb/sec is megabytes or megabits per seconds?

Yes, reads are usually faster than writes, but...

---

### Post by Toet on 2007-12-01
> **fjgaude said:**
> What is the bus from which the disk controllers are being run, PCI, PCI-X or PCI-Express?

Which motherboard are you using?

Your Mb/sec is megabytes or megabits per seconds?

Yes, reads are usually faster than writes, but...

Onboard controllers ASUS M2NPV-MX.

MB/s, megabytes.

---

### Post by misconfiguration on 2007-12-01
Ah, HA! I'm glad you solve this issue. 

Kudos mate!

---

### Post by fjgaude on 2007-12-01
Thanks. I've been thinking of a new MB for a long time... with all the troubles folks are having with Intel P35 I decided to wait awhile. Seems maybe the Asus M2N, some version of it, might be for me.

You controller bus must be on a X4 of PCI-E to get over the 250 MB/sec read speed. Tha'ts good. I know a fellow with a raid5 setup with six drives that's getting over that also, so...

Thanks again.

---

