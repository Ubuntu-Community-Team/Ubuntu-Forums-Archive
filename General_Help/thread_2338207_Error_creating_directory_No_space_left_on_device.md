---
title: "Error creating directory: No space left on device"
date: 2016-09-25
forum: General Help
---

### Post by Gnusboy on 2016-09-25
Hello

I'm trying to find a way to backup my home file to a 1 TB external drive.  The drive has 2 partitions: 1 is 537 GB and the other is 462 GB. The  first partition has 453 GB available and the other has 382 GB free. Both  are mounted and readable.
When I try to back up my primary 650 GB HDD on my system, I keep getting this message
"Error creating directory: No space left on device" It does not matter  whether I try to use Deja Dup, copy and paste, or a simple move command  nothing works. I cannot create a new folder or file for the back up or  anything else I can find that is supposed to work. I have read through  all of the help sections, but the ones I see are to make more room on a  system primary drive.
I don't know what else to try. Is it possible to un-mount a partition on the external drive, then re-mount it for the transfer? 

I currently run Ubuntu 14.04 64-bit. My system has become kind of fluky  with some strange behaviors and I want to reinstall 14.04 to return it  to a default installation. I can afford to lose most of my data, but  there are a couple of things I must save. If anyone can help me with  this I would appreciate it. 

I posted this question back in May, and got a command to read the stuff on all of my drives. Even so, but I don't know where to go from here. I really must keep the documents files and a few others. I could afford to lose the rest, but hope not to. 
I wonder if I am able to save and backup the important stuff, if I should go through the upgrade process. I have been using Ubuntu and have done a few upgrades without data destruction, I'm just paranoid about loosing my important data this time. Can I save stuff by booting to a live CD and transferring from there?

I don't mean to ask so many questions, but my system keeps doing weird stuff and if it dies ..
I will appreciate the help. 
I have to get this problem off of my plate.
Thanks.


Here is the info I get from these 2 commands: 
[B]
df -T[/B]

 ```
 ranhanrio@Ranha:~$ df -T 

Filesystem     Type     1K-blocks     Used Available Use% Mounted on 
udev           devtmpfs   1851192        4   1851188   1% /dev 
tmpfs          tmpfs       378992     1232    377760   1% /run 
/dev/sda8      ext4     108338136 22451356  80360460  22% / 
none           tmpfs            4        0         4   0% /sys/fs/cgroup 
none           tmpfs         5120        0      5120   0% /run/lock 
none           tmpfs      1894952      620   1894332   1% /run/shm 
none           tmpfs       102400       44    102356   1% /run/user 
/dev/sdb1      ext3        999320       60    999260   1% /media/ranhanrio/897fbe47-71a3-4afa-9722-109fc80bc2a4 
/dev/sdb3      ext3     451348860 78192760 373156100  18% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1 
/dev/sdb2      ext3     524204856 81600132 442604724  16% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3 
/dev/sda1      ext4     165281700 14540908 142321844  10% /media/ranhanrio/d936da7d-f118-4a64-87cb-ea8377a17d59
```
  
**df -i**

```
ranhanrio@Ranha:~$ df -i 

Filesystem       Inodes   IUsed   IFree IUse% Mounted on 
udev             462798     546  462252    1% /dev 
tmpfs            473738     572  473166    1% /run 
/dev/sda8       6889472 1277642 5611830   19% / 
none             473738       2  473736    1% /sys/fs/cgroup 
none             473738       3  473735    1% /run/lock 
none             473738       9  473729    1% /run/shm 
none             473738      27  473711    1% /run/user 
/dev/sdb1        131072      11  131061    1% /media/ranhanrio/897fbe47-71a3-4afa-9722-109fc80bc2a4 
/dev/sdb3        110240  110240       0  100% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1 
/dev/sdb2        128000  128000       0  100% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3 
/dev/sda1      10510336  534411 9975925    6% /media/ranhanrio/d936da7d-f118-4a64-87cb-ea8377a17d59
```

---

### Post by ian-weisser on 2016-09-25
Since 650 GB is greater than the 453 GB (or 382 GB) available, the out-of-space error seems appropriate.

---

### Post by Gnusboy on 2016-09-25
The 650 GB drive is partitioned sda1 EXT4 160.27 GB 16.51 USED 143.76 GB UNUSED
                                              sda2 EXTENDED 435.90 GB 
                                              sda7 EXT4  145.36 GB
                                              sda6 EXT4  180.43 GB 83.00 USED 97.43 UNUSED
                                              sda8 EXT4  105.09 23GB 23.28 USED 81.82 UNUSED
                                              sda5 Linux Swap  5.02 GB 397.69 USED 4.63 UNUSEDF
                                              unallocated 2.49

On the 1 TB HD                      sdb1 EXT3 1GB  48.16 USED 974.84 UNUSED
                                             sdb2 EXT3 500GB 77.90 USED 422.10 UNUSED
                                             sdb3 EXT3 430.10  74.64 USED 355.87 UNUSED

So this looks like there is plenty of drive space for me to backup to, but it doesn't work.
If you have a way to fix this I will appreciate your help.
THx


        /dev/sda8       6889472 1277642 5611830   19% / nderstand. But the 650 gig hd is partitioned
with sda8 is  only 19% full. According to GParted
 It looks like there is still 561 GB available
GParted /dev/sda8 is EXT4     6889472 1277642 5611830   19% /

P.S. does anyone know how to copy data from GParted to display here?

/dev/sda8       6889472 1277642 5611830   19% /

---

### Post by &amp;KyT$0P# on 2016-09-25
> **Gnusboy said:**
> ```
ranhanrio@Ranha:~$ df -i 

Filesystem       Inodes   IUsed   IFree IUse% Mounted on 
udev             462798     546  462252    1% /dev 
tmpfs            473738     572  473166    1% /run 
/dev/sda8       6889472 1277642 5611830   19% / 
none             473738       2  473736    1% /sys/fs/cgroup 
none             473738       3  473735    1% /run/lock 
none             473738       9  473729    1% /run/shm 
none             473738      27  473711    1% /run/user 
/dev/sdb1        131072      11  131061    1% /media/ranhanrio/897fbe47-71a3-4afa-9722-109fc80bc2a4 
[COLOR="#FF0000"][B]/dev/sdb3        110240  110240       0  100% /media/ranhanrio/205504c6-6bf7-4fc0-a732-4ea634c2d00a1 
/dev/sdb2        128000  128000       0  100% /media/ranhanrio/d60ed036-350a-4524-833e-c91e7dd76fc3 [/B][/COLOR]
/dev/sda1      10510336  534411 9975925    6% /media/ranhanrio/d936da7d-f118-4a64-87cb-ea8377a17d59
```
See the parts I highlighted in red?  You're not out of disk space, you're out of [inodes]("https://en.wikipedia.org/wiki/Inode").

Is ext3 a requirement here?

---

### Post by Gnusboy on 2016-09-28
Hi. Thanks

I have no idea of what inodes are, or how many I need. Sorry - I'm definitely ignorant on most of the pure technical stuff.

I also am befuddled by your question on EXT 3 It and the EXT 4 were both installed when I connected the external drive.

And, If you can give me a link to a guide on getting access to all my drives so I can back them up, I would appreciate the help.
Thanks

---

### Post by &amp;KyT$0P# on 2016-09-28
> **Gnusboy said:**
> I have no idea of what inodes are, or how many I need. Sorry - I'm definitely ignorant on most of the pure technical stuff.
That's OK, we all once were.  This is why I linked the Wikipedia article about inodes. :)

> I also am befuddled by your question on EXT 3 
Let's just show you then -
```
$ df -i -T -H
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
...
/dev/sda5      ext4        56M  559k   56M    2% /

```
```
$ df -H -T
Filesystem     Type      Size  Used Avail Use% Mounted on
...
/dev/sda5      ext4      901G  340G  516G  40% /

```
I know that partition is larger than yours are, but the question is are my numbers proportional to your numbers?  Let the math answer.

(On a related note, xfs filesystem being 64-bit should have even more inodes than ext4 in theory, but currently I use ext4 for everything I pay attention to, so can't comment much on other filesystems.)

Again, are you required to use ext3 for those partitions?  If not, can you temporarily move **all** the data off those partitions and reformat them to something better?

---

