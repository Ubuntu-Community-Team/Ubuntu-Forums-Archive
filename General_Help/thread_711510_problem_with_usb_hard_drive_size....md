---
title: "problem with usb hard drive size..."
date: 2008-02-29
forum: General Help
---

### Post by Mia_tech on 2008-02-29
I have a 200GB hard drive connected to my kubuntu box, the only problem is that the OS is reporting the wrong size

/dev/sdb1             184G   55G  120G  32% /media/usbdisk

is reporting 184GB, but is really 200....is there something wrong here or that could be happening in linux?

thanks

---

### Post by Rocket2DMn on 2008-02-29
No, that is normal on any operating system.  When a manufacturer sells you a drive, they measure GB in 10^9 bits when in reality a GB is 2^30 bits.  At the very basic level, they say a kilobyte is 1000 bytes when really its 2^10=1024 bytes.  This offset is one of the primary reasons your disk size says it's less than what's on the box.
Secondly, filesystems have overhead for storing tables and whatnot to make the disk more useful, and ext3 happens to have a fairly large overhead.

Long story short, 184GB is right on where it should be.

---

