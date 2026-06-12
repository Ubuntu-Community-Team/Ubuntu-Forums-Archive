---
title: "sata speed issues"
date: 2007-04-22
forum: General Help
---

### Post by goodmanbrown on 2007-04-22
I just put my first-ever SATA drive into my Edgy desktop.  It's in there with two IDE hard drives, and two IDE optical drives.  It's a Western Digital Caviar, 16MB buffer, 7200 RPM.

I copied some video files to the SATA drive, and when I watch them in totem-xine, I get occasional skips and stutters that do not happen when I watch a video from the IDE drives.  I thought maybe the SATA drive is running slowly, but that doesn't seem to be the case according to hdparm:

```
$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2236 MB in  2.00 seconds = 1116.96 MB/sec
 Timing buffered disk reads:  184 MB in  3.03 seconds =  60.76 MB/sec
```

What else could be causing this stuttering in videos on the SATA drive?  Could this indicate some problem with the drive?  I'm hesitant to commit data to it before I figure out what is causing this behavior.

---

