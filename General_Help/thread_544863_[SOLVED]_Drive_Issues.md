---
title: "[SOLVED] Drive Issues"
date: 2007-09-06
forum: General Help
---

### Post by mtvirus on 2007-09-06
I have done searches, but have found nothing that relates to the problem I am having.

In my BIOS, I have it set up to boot from PATA CD/DVD, SATA drive, then PATA slave drive.  The issue is sometimes Linux recognizes my PATA slave drive as /dev/sda instead of /dev/sdb.  More often, it is correct (recognizing my SATA drive as /dev/sda and PATA as /dev/sdb).  I have nothing on my PATA drive that concerns Linux; it is only used as backup for my Vista installation.  My SATA drive contains both Vista and Ubuntu.

Most other distributions of Linux will not even boot from the CD.  I got Gentoo Minimal CD to boot with the all-generic-ide option passed to the kernel.  However, this caused havoc when installing GRUB.  It is now unfortunately on my PATA drive, but thank goodness, it didn't erase/overwrite any data on the drive.  Since it's set to boot last, and should never boot, I guess it does not matter (unless I want to boot from some other removable medium like flash drive).

I know this is not a Gentoo forum.  I am still worried about the random swapping of /dev/sda and /dev/sdb.  After booting into Ubuntu, the first thing I do is check to make sure it got it right.  If not, I reboot again, just to avoid anything weird happening if a new kernel upgrade comes up and/or grub needs to be updated.

Additional info:
MOBO is Intel DG965OT

If anyone else has experienced this issue and has suggestions about what can be done, please respond to this thread.

Thanks,
mtvirus

---

### Post by rsambuca on 2007-09-06
Change from /dev/sda or sdb to the uuid numbers, which will be unique to the physical drive.

---

### Post by mtvirus on 2007-09-07
That's one of the things I love about Ubuntu.  There is no confusion then when booting.

Marking this thread as solved!

Thanks,
mtvirus

---

