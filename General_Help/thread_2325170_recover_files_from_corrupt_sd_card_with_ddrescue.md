---
title: "recover files from corrupt sd card with ddrescue"
date: 2016-05-19
forum: General Help
---

### Post by JimLS on 2016-05-19
I have a corrupt 8G sd card from a BeagleBone that no longer boots.  Connected it to my desktop Ubuntu system by USB.  The FAT partition seems to work ok on a windows PC.  With Ubuntu the Linux partition mounts and a window appears with the folders.  But when I click on any of the folders I get an empty window.  I have had a hard time getting anything to work reading it.  I am trying ddrescue and ran it forwards and backwards.  It read some and got stuck both times.  I have a bit on each end but seem to missing quite a bit in the middle.   Outputs are below.  Looking for what to do next.  I don't need to make the card bootable again - I have made a new card for that.  But I would like to get several scripts off it if possible.

fdisk -l usually hangs when it get to sde drive (the sd card) but I got it to work once:
```

root@jim-ubuntu14-4:/home/jim# fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00081318

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS/exFAT
/dev/sda2       204802048  1228802047   512000000    7  HPFS/NTFS/exFAT
/dev/sda3      1228802048  1433602047   102400000   83  Linux
/dev/sda4      1433604094  3907028991  1236712449    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1433604096  3890941951  1228668928   83  Linux
/dev/sda6      3890944000  3907028991     8042496   82  Linux swap / Solaris

Disk /dev/sde: 7969 MB, 7969177600 bytes
246 heads, 62 sectors/track, 1020 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d41b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048      133119       65536    e  W95 FAT16 (LBA)
/dev/sde2          133120    15564799     7715840   83  Linux
root@jim-ubuntu14-4:/home/jim# 

```

The forward run:
```

root@jim-ubuntu14-4:/home/jim# ddrescue -d /dev/sde2 /home/jim/ddrescue.log


GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:    983040 B,  errsize:   7900 MB,  current rate:        0 B/s
   ipos:     2900 MB,   errors:       1,    average rate:       30 B/s
   opos:     2900 MB,    time since last successful read:     8.9 h
Trimming failed blocks...^C
Interrupted by user


```


The backward run (using same log)
```

root@jim-ubuntu14-4:/home/jim# ddrescue -d -R /dev/sde2 /home/jim/ddrescue.log

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:     4308 MB,  errsize:   3592 MB,  current rate:        0 B/s
   ipos:     1680 MB,   errors:       1,    average rate:     113 kB/s
   opos:     1680 MB,    time since last successful read:    10.4 h
Splitting failed blocks...
```

I just realized that what I named .log is actually the image file and I don't have a log file.  I will see what I can do with the image and if I do this again I will use a log file.

---

### Post by JimLS on 2016-05-19
I copied the image to bbb.img and tried fsck.  It doesn't seem to do anything and I am not sure why.  

```



root@jim-ubuntu14-4:/home/jim# fsck -pf bbb.imgfsck from util-linux 2.20.1
Usage: fsck.ext4 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
        [-I inode_buffer_blocks] [-P process_inode_size]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list


```

I tried mount but it failed
```

root@jim-ubuntu14-4:/home/jim# mount  bbb.img /media/jim/bbbmntmount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
and the dmesg output
```

root@jim-ubuntu14-4:/home/jim# dmesg | tail 
[94519.152299] Add. Sense: Unrecovered read error
[94519.152300] sd 14:0:0:3: [sde] CDB: 
[94519.152300] Read(10): 28 00 00 03 5f 18 00 00 08 00
[94519.152303] end_request: I/O error, dev sde, sector 220952
[94519.152322] EXT4-fs warning (device sde2): __ext4_read_dirblock:901: error reading directory block (ino 24241, block 0)
[94623.309062] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[94623.309064] EXT4-fs (loop0): write access unavailable, cannot proceed
[95350.584078] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[95350.584084] EXT4-fs (loop0): write access unavailable, cannot proceed
[95463.686555] EXT4-fs (loop0): no journal found

```

---

### Post by JimLS on 2016-05-19
I wasn't able to find the files I was looking for and it looks like a big part of the middle of the disk was missed so I am trying again with a log file:

ddrescue -d -n -v /dev/sde2 /home/jim/bbbrun2.img /home/jim/ddrescue.log

I am guessing I will need to run reversed and then run forward with starting offset to skip over bad section but am guessing a bit.  I adjusted the switches to what I think will work better...

---

### Post by sudodus on 2016-05-20
Have you tried the two-step method of Example 1 described in '7 A small tutorial with examples' that you find running ```
info ddrescue
```

```
sudo ddrescue -f -n /dev/sde /dev/sdx logfile
sudo ddrescue -d -f -r3 /dev/sde /dev/sdx logfile
```

assuming that the bad drive is seen as /dev/sde and the cloned copy is seen as /dev/sdx. Change **[SIZE=3]e[/SIZE]** and **[SIZE=3]x[/SIZE]** to the correct current drive letters.

The difference is that this approach is cloning the whole device instead of a partition. You must have a lot of patience, because the process is ***very*** slow, when it has to try to read from bad or almost bad memory cells. (It is slow enough reading from a hard disk drive.)

Also, if you change and try like this, you should start with a new logfile.

---

### Post by JimLS on 2016-05-20
When you say very slow are you talking hours, days, ??  I let them run overnight but apparently that isn't long enough?  At what point do I say it is stuck and interrupt to go to the next step?  I have seen advice to restart at an offset when it gets stuck to avoid the bad area.

---

### Post by sudodus on 2016-05-20
```
'-f'
'--force'
     Force overwrite of OUTFILE. Needed when OUTFILE is not a regular
     file, but a device or partition. This option is just a safeguard
     to prevent the inadvertent destruction of partitions, and is
     ignored for regular files.
...
'-n'
'--no-scrape'
     Skip the scraping phase. Avoids spending a lot of time trying to
     rescue the most difficult parts of the file.
...
'-d'
'--direct'
     Use direct disc access to read from INFILE, bypassing the kernel
     cache. (Open the file with the O_DIRECT flag). Use it only on
     devices or partitions, not on regular files. Sector size must be
     correctly set for this to work. Not all systems support this.

     If your system does not support direct disc access, ddrescue will
     warn you. If the sector size is not correctly set, all reads will
     result in errors, and no data will be rescued.
...
'-r N'
'--retry-passes=N'
     Exit after given number of retry passes. Defaults to 0. -1 means
     infinity. Every bad sector is tried only once in each pass. To
     retry bad sectors detected on a previous run, you must specify a
     non-zero number of retry passes.
```

The first pass should skip sectors that are hard to read and continue reasonably fast, and the second pass should focus on the difficult sectors, and save as many as possible of them.

I can't say how much time that is necessary, but it is usually more than we think, so yes, give it more than a night, maybe two days. You can check from another terminal window, if the log file has changed (if more has been written to it). Checking the size and time of late write should not damage the log file.

---

### Post by JimLS on 2016-05-20
It's been running a little over an hour and this is the status:
```

GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:    69074 kB,  errsize:    771 MB,  current rate:        0 B/s
   ipos:   840836 kB,   errors:       1,    average rate:    15857 B/s
   opos:   840836 kB,    time since last successful read:      57 m
Copying non-tried blocks...  

```

```

root@jim-ubuntu14-4:/home/jim# ddrescuelog -t ddrescue.log

current pos:   601759 kB,  current status: copying
domain size:     7969 MB,  in    1 area(s)
    rescued:    69074 kB,  in    1 area(s)  (  0.86%)
  non-tried:     7287 MB,  in    1 area(s)  ( 91.44%)

    errsize:   612377 kB,  errors:       1  (  7.68%)
non-trimmed:   612368 kB,  in   18 area(s)  (  7.68%)
  non-split:         0 B,  in    0 area(s)  (  0%)
 bad-sector:      8704 B,  in   17 area(s)  (  0.00%)
root@jim-ubuntu14-4:/home/jim# 

```

In trying to get some idea of how long this might take I see non-tried close to 90% so I might expect it to take about 10 times as long or about 10 hours.
But based on the read rate of 16k/sec (and falling) it would take around 6 days.

I realize that this is just the first step so additional time is required for other steps and that it is in a bad area so other areas should go much quicker.  

Will let it run for 24 hours and see...

---

### Post by JimLS on 2016-05-20
For observing the log file you can use
ddrescuelog -t logfile

I just do this from another terminal window so as to not interfere with ddrescue

Another nice status tool I just found is ddrescueview.  there is a package for Ubuntu so it was just 

apt-get install ddrescueview

and then

ddrescueview ddrescue.log

Provides a nice graphical display of progress by block.

---

### Post by JimLS on 2016-05-20
ddrescue is working but seems to fail after a short time.  I then have to remove the USB connection and reconnect and can read a short time.  I have some blocks marked as bad that I think would read fine if the program tried.  How do I force a retry without trimming/splitting/etc.  I am running with an offset to get most of the data in the image filled but not sure how to get the blocks marked as bad.  It seems to be skipping those.

---

### Post by sudodus on 2016-05-21
You are trying advanced things now - beyond my experience. Let us hope someone with more experience of ddrescue can chip in and help you :-)

---

### Post by JimLS on 2016-05-21
I have tried setting r=1 on the command line as I thought that would cause it to try a basic read a second time, perhaps the setting is r=2 (not sure if the first time is time 0 or 1).  It goes immediately to splitting.  In fact, I had an area that hadn't been tried at all and it marked them quickly as bad and moved to splitting which doesn't match the previous behaviour.  I could do a second image and the bad spots would likely be in different places but then I would need to merge the two images and that is also something I don't know how to do...  I haven't found any forums dedicated specifically to ddrescue.

---

### Post by JimLS on 2016-05-22
I struggled with ddrescue and by repeatedly copying small sections of the card I got most of the sectors into the image.  I then used ddrescue to copy it to another sd card of the same size.  It complained that the image was slightly bigger than the card.  I tried mounting it but no luck.  Since windows had no trouble seeing the FAT partition I did a quick search for ways to read a ext4 partition on wondows.  found a page that summarized 3.  Picked ext2read.  No installation, just an exe file so that's easy.  **Ran it and was able to copy the files with no problem**.  A few files copied as zero length but the card continued to function and the zero length files were of no use.  It may be that they were zero length originally and not a result of errors copying them.  I wasn't able to recover a bootable image but I had already made a new updated bootable card and really just needed a few scripts and small code files.  **Very surprising that the windows tools worked much better than the linux ones.**  I also noted that the windows program (win32diskimager) to write the image to the card was much faster than using ddrescue but that might have been the settings I used.  Just happy to have the files back. :)

Will mark this as solved.

---

### Post by sudodus on 2016-05-22
Congratulations :KS

and thank you for sharing your solution. It will be useful for other users :-)

---

### Post by JimLS on 2016-05-22
Maybe it will save someone else at least a bit of the frustration I have had.  Not saying windows tools are always better, just for this particular case they were for me.  YMMV and all that.  :)

---

