---
title: "Computer Slow while transfering data between 2 NON - OS drives. Why is this?"
date: 2014-06-19
forum: General Help
---

### Post by 777funk on 2014-06-19
I'm noticing that while doing a huge data transfer (backing up old HDD  data) that my entire computer gets pretty sluggish with programs being very lagy etc. These are non OS  drives so I wonder why this could be?
                                                                      
                                                                                   This is on Xubuntu which is of course very light for processing and  on a fast machine (new i7 4770S) with 2 new 64MB Cache 1 - 7200 RPM and  1- 5400 SATA drives doing the transferring. Speeds varied from in the  kB/s range up to 150MB/s range as it went through files. 

I was transfering an entire old Win XP hard drive with the OS.

---

### Post by col48 on 2014-06-19
Maybe the Win drive was very fragmented and/or there was a large number of small files?  Either would slow the copying down.  Can't account for the whole machine slowing down unless your other activity was I/O intensive, when there could be contention.

---

### Post by nerdtron on 2014-06-19
Transferring a lot of files on any drive will certainly slow down the responsiveness of a computer regardless of OS. It is not dependent on the CPU or RAM at all. Hard drive I/O is the real culprit here. and I see that you have a slower 5400rpm hard drive which have a slower read/write speed. Transfer speeds also vary depending on what files are transferring. Single large files are definitely faster to trandfer than a folder containing thousand of small files.

---

