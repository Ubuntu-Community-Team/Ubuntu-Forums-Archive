---
title: "hdparm, am i good ?"
date: 2007-09-25
forum: General Help
---

### Post by cytg on 2007-09-25
So im creating a truecrypt disc and its snailing away at 20mb/s .. the disk is a Hitachi 500G (im in 7.04 btw)
So i remeber reading about hdparm and begin digging around
first off, the 500G drive is a 3 partion disc, boot swap and fs(ext3), and is sdc

so i cat /etc/hdparm.conf and every thing is commented out, and sdc is not mentioned.
then i hdparm /dev/sdc and get

/dev/sdc:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 60801/255/63, sectors = 976773168, start = 0

(same for sdc1 with is the ext3 volume)

if i try to enable dma, like this

hdparm -d1 /dev/sdc

i get

/dev/sdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Im thinking that stuff has changed ? or is handled a different way with sata drives ? perhaps autoconfigured, am i allready good ?

Thanks!

---

### Post by cytg on 2007-09-25
tested speed with hdparm

/dev/sda:
 Timing cached reads:   1756 MB in  2.00 seconds = 878.01 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.80 MB/sec

I guess im good.. cpu is maxed out too, so im guessing its not the disk thats my bottleneck in this case..

sorry for the waste of bytes ...

---

