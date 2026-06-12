---
title: "Interesting disk performance stats"
date: 2008-06-11
forum: General Help
---

### Post by dbyrne on 2008-06-11
Some interesting performance stats (well hdparm stats ...):

System: P4-based PC

2x750Gb SATA Seagate Barracudas
sdc1 + sdd1 = RAID-1 array md0
sdc5 + sdd5 = RAID-1 array md1
sdc6 + sdd6 = RAID-1 array md2
sdc7 + sdd7 = RAID-1 array md3

x300Gb PATA Seagate Barracudas
sda1 + sdb1 = RAID-1 array md4

I've built the following drives:
/ mounted on md0
LVM swap-vg on md1 containing 1 LV: swap-lv
LVM home-vg on md2 containing 1 LV: home-lv
LVM data-vg striped over md3 + md4 (RAID-10) containing 3 LVs: media-lv, dbspace-lv, websites-lv

Now the interesting thing is that they all perform pretty much the same, although I would have expected the RAID-10 drive to be faster than the others:

Test 1: /dev/md0 made up of 2 x SATA partitions
```
# hdparm -Tt /dev/md0
/dev/md0:
 Timing cached reads:   1536 MB in  2.00 seconds = 768.11 MB/sec
 Timing buffered disk reads:  302 MB in  3.00 seconds = 100.51 MB/sec

```

Test 2: LVM over a single RAID-1 partition /dev/md2
```
# hdparm -Tt /dev/home-vg/home-lv
/dev/home-vg/home-lv:
 Timing cached reads:   1518 MB in  2.00 seconds = 758.84 MB/sec
 Timing buffered disk reads:  298 MB in  3.01 seconds =  98.93 MB/sec

```

Test 3: RAID-10 drive made up of LVM striped over two RAID-1 arrays: /dev/md3 (2 x SATA partitions) and /dev/md4 (2 x EIDE partitions)
```
# hdparm -Tt /dev/data-vg/dbspace-lv
/dev/data-vg/dbspace-lv:
 Timing cached reads:   1530 MB in  2.00 seconds = 764.35 MB/sec
 Timing buffered disk reads:  152 MB in  1.89 seconds =  80.35 MB/sec

```

---

### Post by sdennie on 2008-06-11
If I understand correctly, you've not setup RAID10 but, LVM ontop of two RAID1 arrays.  That's similar but not the same and I don't think data is necessary completely striped across the two arrays.  You may want to compare performance between /dev/md3 and /dev/md4 and see if things make more sense.

---

### Post by dbyrne on 2008-06-11
Hmm, you could well be right. I created the data VG with:

```
# vgcreate data-vg /dev/md3 /dev/md4
```

then made the logical volumes with (for example):

```
# lvcreate -i2 -I64 --name media-lv --size 200G data-vg
    Logical volume "media-lv" created
```

I thought that would stripe writes to the LV across the two physical volumes but maybe not ...

---

### Post by sdennie on 2008-06-11
If you setup the disks like that it should indeed be striping very similar to RAID0.  I'm not sure what the problem could be.  I'm not an LVM/RAID expert but, is it possible that the extremely limited bandwidth of the IDE /dev/md4 is bringing the net performance down?

---

### Post by dbyrne on 2008-06-12
Yes, the PATA drives could be limiting the overall performance but as they are ATA/133 probably not by that much really. The SATA disks themselves are limited by my motherboard to running at 150Mb/s, so only ~10% faster than the PATA ones.

However the hdparm stats themselves vary by 5-10% from one run to another so any performance reduction due to the different device bandwidths in the arrays probably gets lost in the statistical noise :lolflag:

I guess the lesson is not to expect an automatic appreciable performance gain from RAID-0: there may be other factors at work. If I discover any specifics in my case I'll post an update.

---

### Post by fjgaude on 2008-06-12
Speed, throughput is controlled by many things, like the controller bus, the disk internal transfer rate, CPU and local RAM. The external drive rate is likely not much of an issue, especially with SATA.

Some time ago I tested four drives, all SATA 36GB WD Raptors, in raid0 configs, mdadm:

one drive    = 44MB/sec
two drives   = 80MB/sec
three drives = 111MB/sec
four drives  = 103MB/sec

From this I concluded, which seems to hold true today, the PCI bus that these, at the time, fast drives was the bottle neck.

Sure enough, when I went to a new motherboard with PCI-E X1 controllers the speed for four drives went to 160MB/sec, all tests using hdpram -tT.

Now I run raid5 with four drives that checked at about 70MB/sec each and get about 210MB/sec throughput, which is as it should be, equal to the speed of three drives.

All very interesing and something to keep on top of, to learn about, eh?

---

### Post by dbyrne on 2008-06-12
> **fjgaude said:**
> 
...
All very interesing and something to keep on top of, to learn about, eh?

That's just what I thought :) Not finding my system slow, but interested to see the difference between different disk configs.

To add to the above, I did a bit more testing to see how writes compared as hdparm seems to focus on reads:

Test 1. tar up a 5Gb directory, use a different copy of the same directory on each disk: tar cf X bigdir
Test 2. copy the tar file: cp X Y
Test 3. erase the tar file and the copy: rm X Y
Test 4. # time dd if=/dev/zero of=./X bs=512k count=4096
The results were repeatable and consistent:

/home-lv = the LVM over RAID on SATA
/shared-lv = the LVM striped over two RAID drives, SATA + PATA

```

        /home-lv                   /shared-lv
Test 1: 3m16.801s                  2m40.837s
Test 2: 2m57.060s                  2m8.838s
Test 3: 0m14.746s                  0m14.290s
Test 4: 0m39.581s, 54.3 MB/s       0m19.322s, 111 MB/s

```

So it looks like in reality the performance of the LVM over RAID is quite a bit faster percentage-wise for writes.

---

### Post by fjgaude on 2008-06-12
Thanks for sharing... confirms much of the testing I've done over the years. I live with this:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

As a graphic designer the speed under virtual WinXP is more than quick enough. <smile>

---

### Post by dbyrne on 2008-06-13
<cough!!><splutter!!>:shock: Those stats are outrageously fast !! Not surprised you're finding the speed enough :)

---

