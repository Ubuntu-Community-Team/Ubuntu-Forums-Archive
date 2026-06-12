---
title: "[SOLVED] MythTV box slows to a crawl"
date: 2007-08-04
forum: General Help
---

### Post by burningstar4 on 2007-08-04
I set up a MythTV combined backend/frontend system on Ubuntu Feisty, as detailed by [this]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend") guide.  Everything appeared to work great, and I had relatively few problems getting everything to work.  However, now whenever I leave the system on overnight, it becomes unusably slow.  Selecting something in mythfrontend takes minutes to progress to the next menu, and even switching to a virtual terminal doesn't help - still, everything is painfully slow.  I connected to the system from another computer via SSH and let top run all night, and when I checked in the morning, the system was unresponsive, and top showed only 6MB of 512 free, but no swap used at all.  Further, the top was frozen and didn't show any processes with high memory of CPU usage.  

Demsg didn't show anything troubling, and the only things that look abnormal when I run ps aux is the appearance of 8 apache processes.  Also, I do not have DMA set on the hard disk holding the swap partition.  When I try to run hdparm -d 1 /dev/sda, it says inappropriate ioctl for the device.  Trying it on /dev/hda says no such device or file.

What can I do to get this thing to run more stably?

---

### Post by burningstar4 on 2007-08-11
Bump.  Anybody have any suggestions, perhaps how to enable DMA in this scenario?

---

### Post by praet on 2007-08-14
/dev/hda is an IDE drive, while sda mean its a scsi / sata

What does this return:
```
$ sudo hdparm -i /dev/sda
```

Also check this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636)

---

### Post by burningstar4 on 2007-08-14
The output of hdparm -i /dev/sda gives the following:
```
burningstar4@mythbox:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST380011A                               , FwRev=3.06    , SerialNo=5JV5VWC4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode
```

The bug report looks exactly like my problem, I'll try it.  Thanks!

I'm quite sure it's a hardware issue, the problem persists even on a complete reinstall of Ubuntu Feisty.

---

### Post by burningstar4 on 2007-08-16
A couple failed attempts later, I have a working recompiled kernel that fixes the dma problem.  I suspect this is the end of the problem, thank you very much for pointing me in the right direction!

---

### Post by praet on 2007-08-16
Glad to hear you got dma working.  Did that fix the overnight slowdown issue?

If you dont mind me asking did you roll back a kernel or forward?

---

### Post by burningstar4 on 2007-08-17
So far so good on the overnight slowdowns.  System now swaps out a little when necessary, and vmstat shows very few waiting cycles.

As for the kernel, I installed the linux-source-2.6.20 package and compiled my own version without Serial ATA (prod) and Parallel ATA (experimental) drivers.  So I guess I didn't really change the version so much as the specific options of the kernel itself.

---

### Post by praet on 2007-08-17
Thanks for the update.

---

