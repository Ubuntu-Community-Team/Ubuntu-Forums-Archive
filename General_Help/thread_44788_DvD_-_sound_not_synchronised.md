---
title: "DvD - sound not synchronised"
date: 2005-06-27
forum: General Help
---

### Post by Toppie on 2005-06-27
I have a little problem with dvd's:

when watching a dvd, It starts ok,  after playing a while, the sound gets behind: the movie appears sooner then the sound..

the fun part is, after a short 'pause' it is ok, but then again, after playing the movie for a short period..

this problem does only exist with dvd's
DivX gives no problems...

```

gerard@Top-computer:~$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

---

### Post by Arthemys on 2005-06-27
One problem I've noticed is DVD playback on my ThinkPad when on battery is unbearable. I've been able to improve it slightly by changing a setting regarding optical drive speed in my BIOS from "Quiet" to "Fastest". Even on AC my DVD playback isn't all that great.

Though I doubt that's the case for most people, it seems to me that there's an issue regarding IDE drive performance (DMA?) in ubuntu. Under Windows however on battery it runs fine regardless. Something about not being able to stream that data as fast as it should be.

---

