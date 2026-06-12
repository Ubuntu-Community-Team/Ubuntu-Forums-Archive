---
title: "Constant Stuttering"
date: 2007-10-02
forum: General Help
---

### Post by line72 on 2007-10-02
I am getting constant stuttering, both of the mouse and audio.  This seems to happen more often when there is a high load (every 5 seconds), but still happens every minute or so even under a low load.  Both of my harddrives are scsi and are getting good performance, so it's not a dma issue

```

root@memwd1:~# hdparm -tT /dev/sdd1

/dev/sdd1:
 Timing cached reads:   1248 MB in  2.00 seconds = 623.96 MB/sec
 Timing buffered disk reads:  196 MB in  3.01 seconds =  65.16 MB/sec

```

I had these problems under dapper, and yesterday I upgraded to gutsy beta and they are still there.  The machine is a sun workstation w2100z.  One thing that bothers me, is on sun's [download page]("http://www.sun.com/desktop/workstation/w1100z/downloads.jsp") the 2.2 cd with the bios update mentions stuttering issues related to the fans, however, I have updated to the latest bios revision from the 2.5 cd.

Thanks in advance,
Mark

---

### Post by snickers295 on 2007-10-02
fact is most bios updates don't support linux or anything but windows so unless the update said it was for linux then thats your problem.

---

### Post by line72 on 2007-10-02
This workstation came installed from sun with linux on it.  They officially support sles 9 and the java desktop system on it.

---

### Post by snickers295 on 2007-10-02
> **line72 said:**
> This workstation came installed from sun with linux on it.  They officially support sles 9 and the java desktop system on it.
maybe you got a defective system.

---

