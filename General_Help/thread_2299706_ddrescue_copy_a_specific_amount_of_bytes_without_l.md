---
title: "ddrescue: copy a specific amount of bytes without losing data"
date: 2015-10-20
forum: General Help
---

### Post by ompolicy on 2015-10-20
Hi everybody,

I have been trying to recovery a corrupted/broken external hard drive (/dev/sdb) with ddrescue for almost one week by now.
I am doing (still running in this moment) a copy block-to-block to another external hard drive (/dev/sdc) with the same dimension, 2TB.
I did first a preliminary quick recovery (with no trimming) and now the hard recovery.

That below is the complete output from my terminal:
```
[FONT=arial][COLOR=#000000]sudo ddrescue -f -n /dev/sdb /dev/sdc rescue.log

GNU ddrescue 1.17
Press Ctrl-C to interrupt
[B]Initial status (read from logfile)
rescued:     1982 MB,  errsize:    402 MB,  errors:       2[/B]
Current status
rescued:     1397 GB,  errsize:    603 GB,  current rate:        0 B/s
   ipos:   683857 MB,   errors:    1571,    average rate:    4031 kB/s
   opos:   683857 MB,    time since last successful read:      37 s
Trimming failed blocks...  
ddrescue: input file disappeared: No such file or directory[/COLOR][COLOR=#000000]
sudo ddrescue -d -f -r3 /dev/sdb /dev/sdc rescue.log

GNU ddrescue 1.17
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     1397 GB,  errsize:    603 GB,  errors:    1571
Current status
rescued:     1451 GB,  errsize:    549 GB,  current rate:     617 kB/s
   ipos:     1582 GB,   errors:    1572,    average rate:     613 kB/s
   opos:     1582 GB,    time since last successful read:       0 s
Trimming failed blocks...[/COLOR][/FONT]

```

As you can see from these first lines
```
[COLOR=#000000]Initial status (read from logfile)
rescued:     1982 MB,  errsize:    402 MB,  errors:       2[/COLOR]
```
my logfile wasn't empty, but actually I formatted the new hard drive, so that data is not there anymore.
I realized that just after long time unluckily..but I know that the most important information about the blocks and the file system are usually in the beginning of the partition (it was a FAT32 file system).
So I am wondering now if there is any chance to copy to the new hard drive just that missing 1982MB without throwing away all the job already done.

I found around something that can be useful to my case
```
sudo ddrescue -i0 -s1982MiB -f -n /dev/sdb /dev/sdc

[COLOR=#000000]sudo ddrescue [/COLOR][FONT=Verdana]-i0 -s1982MiB [/FONT][FONT=Verdana]-d -f -r3 /dev/sdb /dev/sdc[/FONT]
```
but I am not sure it can work..

Do you have any experience on that?

Thanks in advance

---

