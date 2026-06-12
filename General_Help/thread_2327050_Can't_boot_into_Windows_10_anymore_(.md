---
title: "Can't boot into Windows 10 anymore :("
date: 2016-06-07
forum: General Help
---

### Post by Entsafter on 2016-06-07
I wanted to install Ubuntu as a second system, I had Ubuntu before and everything worked nice as dualboot. I need Windows 10 to work with Photoshop and co.
So I installed Ubuntu on a new partition with 80 Gb and now I can't boot into Windows anymore.

Boot Repair Past Bin: [http://paste2.org/tIxBc2Bc](http://paste2.org/tIxBc2Bc)

I'm pretty much a Linux noob and I don't habe a Windows Recovery CD :(

Thank you!

---

### Post by ventrical on 2016-06-07
> **Entsafter said:**
> I wanted to install Ubuntu as a second system, I had Ubuntu before and everything worked nice as dualboot. I need Windows 10 to work with Photoshop and co.
So I installed Ubuntu on a new partition with 80 Gb and now I can't boot into Windows anymore.

Boot Repair Past Bin: [http://paste2.org/tIxBc2Bc](http://paste2.org/tIxBc2Bc)

I'm pretty much a Linux noob and I don't habe a Windows Recovery CD :(

Thank you!

Grub Rescue almost always works for me. You have to download the .ISO and burn to CD and then boot the CD.

Regards..

---

### Post by yancek on 2016-06-07
There is no entry for windows in the grub.cfg file so the first thing to try is to boot Ubuntu and run:  sudo update-grub
Watch the output for a windows entry.   Your windows partition is at the beginning of the drive yet is labelled sda2.  Not sure how that happened.  Also, sda1 with Ubuntu is marked as the active/bootable partition which is totally unnecessary for Linux so you might change that to the windows partition if the update-grub doesn't work.  Then run update-grub again.

---

