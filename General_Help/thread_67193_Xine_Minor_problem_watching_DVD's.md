---
title: "Xine: Minor problem watching DVD's"
date: 2005-09-19
forum: General Help
---

### Post by St3althcAt on 2005-09-19
I'm having a minor problem watching DVD's with Xine: each 5 seconds of movie, the movies has a little milisecond brake. Yes, I can watch the DVD like that, but if I could remove thoses breaks, it would be better.

Thank you for the attention.

---

### Post by Romanmir on 2006-10-28
> **St3althcAt said:**
> I'm having a minor problem watching DVD's with Xine: each 5 seconds of movie, the movies has a little milisecond brake. Yes, I can watch the DVD like that, but if I could remove thoses breaks, it would be better.

Thank you for the attention.

sounds like DMA is not enabled on your DVD player. I don't have the details in front of me, however, that might point you in  the right direction.

---

### Post by jdunn on 2006-10-28
> **St3althcAt said:**
> I'm having a minor problem watching DVD's with Xine: each 5 seconds of movie, the movies has a little milisecond brake. Yes, I can watch the DVD like that, but if I could remove thoses breaks, it would be better.

Thank you for the attention.

Yes, it does sound like it may be a DMA issue.  Type 'sudo hdparm /dev/hdc' and you should get something like this back:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

If 'using_dma=0' then DMA is not working.  The problem could be related to drivers, firmware, or the hardware itself.

---

### Post by paca on 2006-11-01
i had the exact same problem, dma was on...
works perfect when i change the video driver in xine

xine -V sd1

---

