---
title: "Disk I/O stats from /proc/diskstats"
date: 2005-05-02
forum: General Help
---

### Post by YorHel on 2005-05-02
Hello,

I'm trying to create some system stats-graphs with rrdtool, I can get a lot of things working, but now I want to graph the Disk I/O stats, I can get the information from /proc/diskstats
```
cat /proc/diskstats | grep 'sda '
   8    0 sda 2461810 61427 148062742 6482992 660009 1544934 67900384 45642376 0 7162961 52128751
``` 
where:
> 
Field  1 -- # of reads issued
Field  2 -- # of reads merged, field 6 -- # of writes merged
Field  3 -- # of sectors read
Field  4 -- # of milliseconds spent reading
Field  5 -- # of writes completed
Field  7 -- # of sectors written
Field  8 -- # of milliseconds spent writing
Field  9 -- # of I/Os currently in progress
Field 10 -- # of milliseconds spent doing I/Os
Field 11 -- weighted # of milliseconds spent doing I/Os


the problem: I want to graph I/O stats in (K|M)bytes/second, and for that I need to know the total amount of bytes read from/written to the disk... but I don't know the size of one sector, nor the size of one read/write. 
Is there any way to calculate the total amount of bytes read from/written to the disk?

Thanks in advance!

---

### Post by YorHel on 2005-05-05
I hate to reply to myself, but why is it that when I ask a question, nobody answers?
Is it because I can't explain well, or just because nobody wants to answer?
I mean... I am not the only one who wants to measure Disk I/O usage, and there must be someone here who knows how, so why can't anyone help me?

---

### Post by Takis on 2005-05-05
[QUOTE=YorHel]I hate to reply to myself, but why is it that when I ask a question, nobody answers?
Is it because I can't explain well, or just because nobody wants to answer?
I mean... I am not the only one who wants to measure Disk I/O usage, and there must be someone here who knows how, so why can't anyone help me?[/QUOTE]
Dude, you have to consider the possibility that noone yet who's read your post knows how to answer...

Edit: But try running ```
sudo dumpe2fs /dev/your_hdd -h
```

---

### Post by YorHel on 2005-05-12
[QUOTE=Takis]Dude, you have to consider the possibility that noone yet who's read your post knows how to answer...[/QUOTE]
Oh, yes, sorry, forgot about that, I was impatient again  #-o 

[QUOTE=Takis]Edit: But try running ```
sudo dumpe2fs /dev/your_hdd -h
```[/QUOTE]
well, that gives me some useful info about my ext2/ext3 partitions, but the hdd I want to measure has ReiserFS, and how to get the same information for reiserfs partitions...? second, 
```
dumpe2fs 1.37 (21-Mar-2005)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          df9548b9-712b-4686-b2ef-7509a80fec7d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      filetype sparse_super large_file
Default mount options:    (none)
Filesystem state:         not clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              24903680
Block count:              49785427
Reserved block count:     2489271
Free blocks:              110981
Free inodes:              24900010
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Thu Jan  6 11:58:21 2005
Last mount time:          Sat Jan 15 11:12:12 2005
Last write time:          Tue May 10 12:43:14 2005
Mount count:              40
Maximum mount count:      36
Last checked:             Thu Jan  6 11:58:21 2005
Check interval:           15552000 (6 months)
Next check after:         Tue Jul  5 12:58:21 2005
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Default directory hash:   tea
Directory Hash Seed:      c55cd0a1-66ed-4802-be96-45810934e3bd
```
there are a few things that I might need...
Inode size:               128
Block size:               4096
Fragment size:            4096
but... which do I really need? the manpage of /proc/diskstats mentioned 'sectors' and 'read'/'writes', not 'Inodes', 'Blocks' or 'Fragments'... which is which...?

Sorry for being so annoying... but can someone please help be a little? O:)

---

### Post by zick on 2008-03-22
HI! I too am interested in the decision of this question as too I wish to get statistics from the HDD  itself (it is not pleasant to me SNMP and that as it removes it) But it is similar that really complicated question and anybody so deeply did not dig except for hackers of a kernel, and laziness to answer them :( so as a problem I shall solve I shall help than I can !

Best regards! 

P.S.

Don`t Warry be Heppy Now ! :KS

---

### Post by exvagabond on 2008-03-28
Here is a program which will let you view statistics on your disks:

iostat
[http://www.linuxinsight.com/iostat_screenshots.html](http://www.linuxinsight.com/iostat_screenshots.html)

The source is available here if you do not have the program already:
[http://www.linuxinsight.com/files/iostat-2.2.tar.gz](http://www.linuxinsight.com/files/iostat-2.2.tar.gz)

The program will output the writes or reads per second. Following is an example invocation:

iostat -x 1

This will print out extended disk information once a second. Here is an example of output:

device mgr/s mgw/s    r/s    w/s    kr/s    kw/s   size queue   wait svc_t  %b
sda        0    49   18.0   32.7    76.6 14599.6  289.5  39.3 1210.5  12.0  61
sdb        0     0    0.0    0.0     0.0     0.0    0.0   0.0    0.0   0.0   0

The kr/s and kw/s columns are the kilobytes read/written per second to the listed disks.

Hope this helps.

---

### Post by zick on 2008-04-18
Now I can help you , if you are still want get io statistics for Hard Drives exactly via /proc/diskstats.
For example:

# fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381   83  Linux
/dev/hda2            1306        1436     1052257+  82  Linux swap
/dev/hda3            1437        4866    27551475   83  Linux
 
As you can see I`ve one HDD mergered on three chunk. 

#cat /proc/diskstats | grep hda
   
   3    0 hda 43205 4113 4800428 280967 1051597 1682874 21876608 1950120 0 858685 2231096
   3    1 hda1 25838 525266 1505217 12041736
   3    2 hda2 846 1164 88 704
   3    3 hda3 20498 4272886 1229274 9834168

Let`s consider "How I can get stats for my /dev/hda3 ??"
Let`s consider this line :   3    3 hda3 20498 4272886 1229274 9834168
    After a word "hda3" we have four 32-bit (type integer) fields, us interesting these: 
The second field: 4272886 (total number of sectors which normally reads from /dev/hda3)
and The Fourth filed : 9834168 (total number of sectors which normally writes to /dev/hda3)
   These two fields - all that is necessary for us. A /proc/diskstats continuously updated and all that is necessary for us - make measurements for "second field" and "fourth field" in two different moment of time, receiving a difference of values and dividing it into an interval of time, we shall have Disk I/O stats in sectors/sec. Multiply this result on 512 (number of bytes in one sector) we shall have  Disk I/O stats in bytes/sec. 
    May be exist a problem how to measure precisely moment of a time in seconds ... 
    Here a piece of my code on &#1057; for this purpose: 

#include .....

  struct tms tiks_buf;
  long int clock_tiks = sysconf(_SC_CLK_TCK);
  clock_t times_tiks = times(&tiks_buf);
  long int times_secs = times_tiks / clock_tiks;
  ......

So, for example  for /dev/hda3 in /proc/diskstats:

------------------------------------------------------------------------------- The time, mesured (for example) as    
-------------------------------------------"second field"---"fourth field"------considering above in times_secs
In the  one moment of  time:____4273078_____11234680_________ 4536321
In the second moment of time:_ 4273094_____11263120_________ 4536620 

Elapsed time: 4536620 - 4536321= 299 sec
Then:
Speed of reads: ( (4273094 - 4273078 )/299)*512 = 27,39 bytes/sec
Speed of writes: ( (11263120 - 11234680)/299)*512 =  48699,93 bytes/sec = 47,5 Kbytes/sec 

- Now I downloaded clip from internet, my bandwich ~ 48 Kb/sec

That`s method WORK ! You can write simple utilite on shell or C++  :^)) and execute it from MRTG
(for example) and you can see greatest results, if to compare with SNMP utilities ... 

:popcorn:

Best Regards, Adrew Burdyug
ICQ: 488000016
E-Mail: [EMAIL="buran83@gmail.com"]buran83@gmail.com[/EMAIL]

---

