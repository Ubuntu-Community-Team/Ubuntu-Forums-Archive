---
title: "[SOLVED] Boot usb disk from flopply"
date: 2008-05-26
forum: General Help
---

### Post by leon.hh on 2008-05-26
Good morning everyone! I'm having a very bothering problem: I just bought a 160GB external HDD and I installed Ubuntu 8.04 on it, I customized that installation to make it bootable in any machine, so I can take my data and my Ubuntu everywhere, no problems so far.

The problem shows when I try to boot my disk in a machine that doesn't allow usb boot. I know that there is a floppy image that allows to boot from any device (even if the motherboard BIOS doesn't support it), I used it long time ago but now I can't find it, if someone knows about this image, please send me a link to download it.

Thanks

---

### Post by HeartBT on 2008-05-26
Yes, please help this fella out, and post here the howto.  I've been head scratching and fumbling for this exact solution for a whole day!

---

### Post by leon.hh on 2008-05-27
Well, good for both of us. I just remembered where I had the floppy image I was talking about: Just download the attached file, uncompress it (tar -xvzf bf.tar.gz) and transfer it to a blank floppy disk (dd if=bootfloppy.img of=/dev/fd0).

That's it, boot your machine whit that floppy and you should be able to boot from any device connected to your it (even if tour motherboard doesn't support it)

If you prefer, you can download the source files from: [http://btmgr.sourceforge.net/3.7/](http://btmgr.sourceforge.net/3.7/) and create your own image

---

### Post by HeartBT on 2008-05-28
Thanks!  I'll give it a try.

---

