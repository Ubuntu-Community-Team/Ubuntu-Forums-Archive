---
title: "Hero 5 corrupted video"
date: 2017-06-20
forum: General Help
---

### Post by second.exodous on 2017-06-20
So I got back from a two week bicycle tour, recording video on my Hero5 all the way, and depressingly when I got home quite a few of the .MP4 files were corrupt.  For some reason the low rez .LRV files that gopro itself uses were fine.

So I would put the micro SD card in a USB reader and pull the video off that way.  It would start out at 90 MB/s and soon drop down to 20 MB/s, and I couldn't do anything while files were copying.  I have a msata in an external case that I have for backup, but I would restart my computer then copy to that, and that would copy from my PC to the drive at 300+ MB/s.

I'm guessing this is due to the current exfat support in Linux, but I'm not sure.  Does anyone else that uses Linux, specifically Ubuntu or even more specifically Ubuntu Studio have any tips on copying files from the GoPro to their PC?  Maybe upgrade exfat support?  I was thinking maybe I should just copy strait from my GoPro since it copies so slow anyway, maybe that would help?

Thanx,
Stan

EDIT:  I use Ubuntu Studio 17.04 but am considering dropping back to 16.04.2 LTS since I won't be doing anything on this notebook besides editing video, my phone will do web browsing, email, and video chat.  It is a System76 Lemur with a 1TB SSD, 32GB of memory, the 3.5 GHz i7-7500U, so my specs shouldn't be the issue, or I think so anyway.

---

### Post by howefield on 2017-06-21
Thread moved to the "*General Help*" forum.

---

### Post by Bucky Ball on 2017-06-21
Try installing exfat-fuse and exfat-utils

```
sudo apt install exfat-fuse exfat-utils
```

... then shove the card in and see if you have more succes.

---

### Post by second.exodous on 2017-06-21
That is what I'm using apparently, I already had them.

---

