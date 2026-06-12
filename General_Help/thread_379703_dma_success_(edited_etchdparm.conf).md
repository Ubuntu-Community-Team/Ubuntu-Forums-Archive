---
title: "dma success (edited /etc/hdparm.conf)"
date: 2007-03-08
forum: General Help
---

### Post by bif3c on 2007-03-08
This may be obvious to many, but I'm posting because I searched high and low for a solution to my DMA woes without success.  I couldn't turn DMA on for my DVD drive (/dev/hdc) even though I had added the following to /etc/hdparm.conf:

/dev/hdc { 
dma = on 
}

When I tried

sudo hdparm -d1 /dev/hdc

at the command line, the output would say that DMA was turned on even though it wasn't.  I finally noticed that my BIOS listed my current DMA mode as udma5 when the best my DVD drive can do is udma2.  This led me to try

sudo hdparm -d1 -X66 /dev/hdc

and this worked because it backed DMA mode down to udma2, which my DVD drive can handle.  After this discovery, I just needed to edit /etc/hdparm.conf to properly enable DMA on every boot, so I added the following:

command_line {
hdparm -d1 -X66 /dev/hdc
}

This works like a charm; now DVDs play smoothly and they also burn quickly.  As I said before, this may be obvious to most, but I didn't find this suggestion in the forums (or anywhere online), so I'm posting in the hope that it may help someone else.

---

