---
title: "slow file transfer between disks?"
date: 2008-05-09
forum: General Help
---

### Post by c-roc on 2008-05-09
I have three ATA 7200 rpm drives and copying a few 700mb files between them goes at around 17MB/s.  I don't know how fast windows was, but it sure seemed faster.  It should be faster, no?
Fresh install of Ubuntu 8.04, all drives are EXT3

---

### Post by c-roc on 2008-05-09
oh, and hdparm -l for the source disk is 53MB/s and the destination disk is 77MB/s.

I just drag/dropped, and cut/pasted a single 700MB file, and got the same results, around 17MB/s.

---

### Post by c-roc on 2008-05-12
can anyone point me in the right direction?

---

### Post by hcaicedo on 2008-08-21
Same problem here. 
When i test hard drive with  hdparm -tT /dev/sd :

 [SIZE="1"]Timing cached reads:   404 MB in  2.00 seconds = 201.89 MB/sec
 Timing buffered disk reads:  124 MB in  3.03 seconds =  40.86 MB/sec[/SIZE]

But when I am doing a copy whit Nautilus shows : 1.7 MB/s


Same hard drive brand on different computer :

[SIZE="1"]Timing cached reads:   6272 MB in  2.00 seconds = 3138.79 MB/sec
 Timing buffered disk reads:  288 MB in  3.01 seconds =  95.77 MB/sec[/SIZE]


Any idea what is happening ?

---

### Post by kuja on 2008-08-21
There's a lot more to things than brand. 

Higher capacity drives read and write faster, because the read/write heads don't have to travel as far. A larger cache helps things also. Also, SATA hard drives are definitely faster than their IDE brethren. 

Reading/writing most of the time is very differnet than a buffered or cached read also. Those are benchmarks of different things than normal data transfer. 

17MiB/s is probably about normal.

---

### Post by hcaicedo on 2008-08-22
maybe 17 MB/sec is OK, but 1.7 MB/sec on a sata hard drive? . I put 3 new hard drives same brand same specs on two different computers. One is a desktop the other one is server. On my desktop the hard drive is very fast. On the server can't have more than 1.7 MB/s.

---

### Post by eznet on 2010-01-07
Anyone ever figure out anything on this?  Running 7200/8MB (Maxtor 6V200E0) and averaging 8MB copies on the disk (copy \folder1 to \folder2)... we will not even discuss the lag the copy is creating on me while I am trying to type this post...

---

### Post by HiImTye on 2010-01-07
I would check your BIOS settings to see if youre being limited down the cable

---

### Post by kuja on 2010-01-10
If you really want to test if it's a problem "down the pipe", you could pull the drive, put it in an external enclosure, and connect it to another computer and test... The reverse applies also.

---

