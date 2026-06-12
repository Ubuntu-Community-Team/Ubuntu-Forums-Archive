---
title: "DVD drive won't write in latest kernel"
date: 2007-06-18
forum: General Help
---

### Post by tvphil on 2007-06-18
This question/problem started as a thread in hardware, but soon discovered, it was not a hardware issue, it seems to be a kernel issue. When I attempted to burn (write) a DVD or a CD, I get this error message...

Burning
Executing 'genisoimage -dvd-video /home/tvphil/dvd/ | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/dvd: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
write failed: Invalid argument
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing disc

The drive reads (plays) anything I put in it and it did write before the latest kernel upgrade. It also still writes fine in the Windows partition of my hard drive, so I know the drive still is capable of writing.Now before you tell me to roll back to an earlier kernel, I don't want to and I shouldn't have to, even though I admit, it probably would work.I would rather find a way to correct this problem in the existing kernel.As you can see in the error message, it says /dev/dvd, the true device name is /dev/cdrom (or sr1).This was copied from using DVDStyler. I also attempted writing using Gnome Baker, with the correct /dev/cdrom and the same thing happened, as it did with Nautilus CD/DVD Creator as well. The DVD drive is an HL-DT-ST (LG-Hitachi)GMA 4020B.

---

