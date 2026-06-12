---
title: "SCSI slow to start"
date: 2008-03-14
forum: General Help
---

### Post by JillB on 2008-03-14
This is my first post with this forum, and not sure if this is the right location.

I have a U320 Adaptec controller model 39320 with two 68 pin channels. One channel is 

connected to three U320 SCSI drives. The IDs are 0, 2, 4

On boot up, the computer scans through all the possible ID connections. When it comes to ID2 

and ID4, it stops for about 30 seconds on each before moving off to the next ID.

This slows the startup time considerably.

Is this normal, or is there something I can do about it?

---

### Post by cmnorton on 2008-03-15
I believe at the point you describe, you have not seen the grub menu, and the kernel has not booted. So this appears to be a SCSI BIOS issue.

There might be something you could do, but that would require going into the SCSI BIOS to see if there are some settings you can tweak. 

Many of our SCSI servers have pretty long startup times. Things do seem to delay a while on the SCSI initializastion. One IBM server prints that the timeout is up to 5 minutes.

---

