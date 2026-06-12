---
title: "Ubuntu faster on USB"
date: 2013-04-18
forum: General Help
---

### Post by zoozd on 2013-04-18
Hello,

I booted today Ubuntu 11.04 from a LiveUSB to resize a partition. I noticed that when I booted using the USB, Ubuntu 11.04 on USB was faster than Ubuntu 12.10 that I have on my harddisk. One thing which amazed me was the speed at which the wireless indicator changed when trying to connect. Also, applications were loading more quickly, and they were faster overall.

Is it because my harddisk is slow? Or what is the problem?

Here are my specs:

Fujitsu A530 (2-3 years old)
Intel Core i5 M430 @ 2.27GHz x 4
Disk 24 GB (10 GB used, ext4)
Memory 3.7 GB

---

### Post by tgalati4 on 2013-04-18
Open a terminal:

```
sudo hdparm -tT /dev/sda
```

The Live DVD/USB runs entirely in RAM so it will be faster.  Your disk speeds can be compared with others by posting the output of the above command.  A fast IDE/PATA disk will be 66 to 75 MB/sec, a decent SATA disk will get above 100 MB/sec.

My disk is slow in this Acer laptop:

tgalati4@Mint14-Extensa ~ $ sudo hdparm -tT /dev/sda
[sudo] password for tgalati4: 

/dev/sda:
 Timing cached reads:   1602 MB in  2.00 seconds = 800.84 MB/sec
 Timing buffered disk reads: 144 MB in  3.04 seconds =  47.41 MB/sec

---

### Post by Frogs Hair on 2013-04-18
> Is it because my harddisk is slow? Or what is the problem? I think you answered your own question, but you did not state what drive you are using . 12.10 is more resource hungry than 11.04 also which was the last Gnome 2 release. Gnome 3 started with 11.10 and has changed as well.

---

### Post by zoozd on 2013-04-18
I got:

/dev/sda:
 Timing cached reads:   4450 MB in  2.00 seconds = 2226.94 MB/sec
 Timing buffered disk reads: 232 MB in  3.00 seconds =  77.31 MB/sec

I was wondering how the LiveUSB works, but surely if it is using the RAM then of course it will be faster.
Thank you.

---

### Post by zoozd on 2013-04-18
> **Frogs Hair said:**
> I think you answered your own question, but you did not state what drive you are using . 12.10 is more resource hungry than 11.04 also which was the last Gnome 2 release. Gnome 3 started with 11.10 and has changed as well.

I'm using Hitachi HTS545032B9A300 (PB3OC6J1), 5400 rpm.

---

### Post by Slim Odds on 2013-04-18
SSD's are MUCH faster than any spinning hard drive. Particularly when it comes to random access.
I can get from GRUB to login prompt in less than 8 seconds with my SSD based desktop system.

---

### Post by zoozd on 2013-04-18
If you are talking about the flash usb, then yes SSD is much faster, but the fact that it is connected through a USB 2.0 port doesn't allow it to go full speed. That is what I was thinking, until the sir up there told me that it runs on RAM.

---

### Post by Slim Odds on 2013-04-18
> **zoozd said:**
> If you are talking about the flash usb, then yes SSD is much faster, but the fact that it is connected through a USB 2.0 port doesn't allow it to go full speed. That is what I was thinking, until the sir up there told me that it runs on RAM.
No matter where Ubuntu loads from (HDD, SDD, DVD, CD, etc.), it runs from RAM.
Even with USB 2 the SSD stick is fast, especially if you're used to a 5400 RPM drive.
Any SSD has pretty much 0 seek time compared to an HDD.

---

