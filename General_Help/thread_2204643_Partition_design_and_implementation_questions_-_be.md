---
title: "Partition design and implementation questions - best for multi-access?"
date: 2014-02-09
forum: General Help
---

### Post by freebird54 on 2014-02-09
I recently built myself a new system,and split up the drives in what I hoped to be a useful partitioning scheme.  I have a small (128) SSD, and a 2 TB spinner.

The SSD has 3 partitions:
```

System 1:    52 ish  (currently 12.04)
System 2:    52 ish  (currently 13.10)
Ux  Swap:    16 ish  (double RAM)

```

The 2 TB internal also has 3 partitions:
```

Back 1&2:  105 ish  (all but /home each) dd backup
System 1:  250 ish   /home
System 2:  250 ish   /home 
Common :  1.4 TB

```

I also have an external 2TB for 'running' backups - but that is all handled :)

The question I have NOT answered to my satisfaction is where and how to mount the 'common data' partition.  Essentially I want to have it be the respository of those things that should be common to either system at all times - especially working spreadsheets/documents - Music - Videos.  Currently it is self-mounting (who knows why/how) in /media as a root-owned item, but I assumed that it would be best mounted under /home on each of the other systems whenever they are 'chosen'.  This may not be optimum, though - especially as the newer versions of Ubuntu make use of defaults for the 'Music' directory, for instance.

I did not want to actually SHARE the home directory, however, having experienced the chaos of different 'versionitis' when attempting that before. Which is why I have the extra partition, of course!  Should I mount it under /home as /Data - and redirect /home/Music to /home/Data/Music (etc)?  Do I mount it AS home/Music (after moving out its current contents of course)?  Do I split it up a bit more, and **separately** mount partitions as /home/Music, /home/Videos, /home/Documents etc? Should I avoid having it under /home at all, and mount it as /Data?

Any suggestions as to the most 'efficient' choices, 'safest' choices, or 'easiest' choices would be appreciated.  I can probably implement whatever is best without TOO much trouble!

If only I understood the whole file system as well as I knew AmigaDOS  :)

Thanks in advance...

---

### Post by bab1 on 2014-02-09
> **freebird54 said:**
> I recently built myself a new system,and split up the drives in what I hoped to be a useful partitioning scheme.  I have a small (128) SSD, and a 2 TB spinner.

The SSD has 3 partitions:
```

System 1:    52 ish  (currently 12.04)
System 2:    52 ish  (currently 13.10)
Ux  Swap:    16 ish  (double RAM)

```

The 2 TB internal also has 3 partitions:
```

Back 1&2:  105 ish  (all but /home each) dd backup
System 1:  250 ish   /home
System 2:  250 ish   /home 
Common :  1.4 TB

```

I also have an external 2TB for 'running' backups - but that is all handled :)

The question I have NOT answered to my satisfaction is where and how to mount the 'common data' partition.  Essentially I want to have it be the respository of those things that should be common to either system at all times - especially working spreadsheets/documents - Music - Videos.  Currently it is self-mounting (who knows why/how) in /media as a root-owned item, but I assumed that it would be best mounted under /home on each of the other systems whenever they are 'chosen'.  This may not be optimum, though - especially as the newer versions of Ubuntu make use of defaults for the 'Music' directory, for instance.

I did not want to actually SHARE the home directory, however, having experienced the chaos of different 'versionitis' when attempting that before. Which is why I have the extra partition, of course!  

Should I mount it under /home as /Data - and redirect /home/Music to /home/Data/Music (etc)?  Do I mount it AS home/Music (after moving out its current contents of course)?  Do I split it up a bit more, and **separately** mount partitions as /home/Music, /home/Videos, /home/Documents etc? Should I avoid having it under /home at all, and mount it as /Data?

[COLOR="#0000FF"]Edit: There is no efficiency gained by creating separate partitions.  A partition adds file system capacity (i.e. GB's) and the data is on a separate spindle. [/COLOR]
> 

Any suggestions as to the most 'efficient' choices, 'safest' choices, or 'easiest' choices would be appreciated.  I can probably implement whatever is best without TOO much trouble!

If only I understood the whole file system as well as I knew AmigaDOS  :)

Thanks in advance...

All mount points are the same.  There are routines for auto mounting USD connected drives (at /media), but other than that you mount them as you see fit.  The traditional place for "common data" is at /srv.  There is a standard for the various file systems (e.g  /var /etc/ /srv) see [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by oldfred on 2014-02-09
I have a 60GB SSD, with two / (root) installs also. And my working install including all of /home is 11GB. My /home is 2GB of the 11GB only because I have .wine for Picasa which is most of the 2GB.

But I have all data on rotating drive. Since I had previous found that when I have all data elsewhere my home is tiny. So I keep /home inside my / on the SSD. 

If you have 8GB of RAM you may never use swap, so it does not matter how large or where it is. I normally then suggest just 2GB to have a little.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by freebird54 on 2014-02-09
OK - in all those I definitely found the right answer for my situation - essentially it was in the first of the links posted in the previous message.  So I mounted the partition as /mnt/data (because it doesn't show up as the annoying **1.4 TB Filesystem**), created the directories I needed on it (Music, Videos, Documents, Ubuntu One), and filled them up as appropriate.  Then created links to hold their places in /home, and I end up with exactly what I was trying to do!  Thank you for retaining those links - for some reason I didn't find any of them (OK - so it was poor search terms on my part!).

Now the only unanswered question is why the fresh, empty partition (containing only an empty last+found) nevertheless apparently had 69 Gb in use?? (according to Properties anyway).  Oh well - I'll research that later - and mark this SOLVED.  Really happy to do it in one go for once....

---

### Post by oldfred on 2014-02-10
File systems whether Linux or Windows based with journals reserve space for journal. LInux reserses another 5% to try to help prevent system crash by filling system partition. If just a data partition you do not need 5% and 5% on the new very large hard drive is often too much.

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)


 sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print
Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdXY where X is drive & Y is partition.

---

### Post by freebird54 on 2014-02-10
Well, I thank you again!  I never expected to not only get an explanation - but also a 'solution'!

Originally I mainly wondered at least as much why the size discrepancy was REPORTED as much as I noted the amount of 'wasted' space... I just assumed that the space was used somehow, and would have written it off mentally as 'formatting loss'. I should have known it was resulting from a default, and changeable, parameter!  I have given it the **sudo tune2fs /dev/sdb4 -m 0** treatment, which turns
```

Inode count:              84254720
Block count:              337010944
Reserved block count:     16850547
Free blocks:              321324060
Free inodes:              84251492

```

into
```

Inode count:              84254720
Block count:              337010944
Reserved block count:     0
Free blocks:              321324060
Free inodes:              84251492

```

It is all a VERY long way from using AND for bit testing so as to stuff 8 'flags' into a byte - to save disk space on a 170k floppy!

Thanks again.

---

### Post by oldfred on 2014-02-11
Your are welcome, glad you got it working. :)

I am afraid I also remember those old floppy drives.

---

