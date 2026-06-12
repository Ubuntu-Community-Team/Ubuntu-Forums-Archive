---
title: "disk performance"
date: 2008-03-08
forum: General Help
---

### Post by hirohitosan on 2008-03-08
Hello to everyone. I just checed the disk performance on my box and I found that.
```
sudo hdparm -t /dev/sda1
/dev/sda1:
 Timing buffered disk reads:   76 MB in  3.04 seconds =  25.00 MB/sec
sudo hdparm -t /dev/sda5
/dev/sda5:
 Timing buffered disk reads:   58 MB in  3.06 seconds =  18.95 MB/sec
sudo hdparm -t /dev/sda4
/dev/sda4:
 Timing buffered disk reads:   42 MB in  3.01 seconds =  13.97 MB/sec
sudo hdparm -t /dev/sda6
/dev/sda6:
 Timing buffered disk reads:   64 MB in  3.08 seconds =  20.80 MB/sec 

```

sda1 is NTFS volume winXP (drive C)
sda5 is NTFS volume winXP (drive D)
sda4 is EXT2 root directory /
sda6 is EXT2 /home

It seems to me that the NTFS volume is read faster than the others. It's normal?

Thanks.

---

### Post by NightwishFan on 2008-03-08
kazuma@kazuma-desktop:~$ sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  150 MB in  3.02 seconds =  49.70 MB/sec
kazuma@kazuma-desktop:~$ sudo hdparm -t /dev/sda2

/dev/sda2:
 Timing buffered disk reads:  172 MB in  3.00 seconds =  57.26 MB/sec
kazuma@kazuma-desktop:~$


My Hardy partition is faster, however I assume it is normal.

---

### Post by Whiffle on 2008-03-08
All of the OT's numbers sound slow, but that depends on the hardware.  how old is this box?  My 6 year old p4 desktop gets ~55mb/s.  My T43 gets ~38.

---

### Post by NightwishFan on 2008-03-08
The results will be slower the more active the disc in question is. I can almost double my speed when it is idle. Best is to do it with few things running.

---

### Post by hirohitosan on 2008-03-08
> **Whiffle said:**
>   how old is this box?  My 6 year old p4 desktop gets ~55mb/s.  My T43 gets ~38.
My box it's an IBM T40 from 2002. Finally I noticed that if the hd is idle for long time gives a higher transfer rate.
Thanks guys

---

