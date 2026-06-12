---
title: "k3b = I/O cpu 100% and 0% FIFO buffer"
date: 2007-02-06
forum: General Help
---

### Post by NaSeTe on 2007-02-06
Hi, i have a laptop with sony 8x dvd recorder 1gb ram 1,8ghz centrino etc.
The recorder have dma on.:

> /dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

When i burn a DVD with k3b (growisofs?) the cpu up to 100% (i/o cpu use) and fifo buffer down to 0% (i tried 30 50 and 200mb for buffer).

Any suggestions? thx.

---

