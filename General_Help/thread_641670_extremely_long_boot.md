---
title: "extremely long boot"
date: 2007-12-15
forum: General Help
---

### Post by scram69 on 2007-12-15
Just installed Gutsy on my desktop.  Unfortunately, bootup takes 2-3 minutes now.

I've attached the bootchart.  Sorry it's so wide - that's what happens when it takes so long to boot.  Seems to stick on modprobe, cdrom-id and ata-id.  Any ideas?

Also, in dmesg, there is a long time gap between these entries:
```
[   23.220000] lo: Disabled Privacy Extensions
[   33.864000] ath0: no IPv6 routers present
[  197.988000] loop: module loaded
[  198.020000] lp0: using parport0 (interrupt-driven).
```

thanks-

<later...>

OK, here was the problem.  There was a CD-R with some digital pictures in one of the optical drives.  Removed the CD-R, now boot takes ~20 seconds.  Is it normal for Ubuntu to struggle so mightily with cd drive contents during boot?  After all, if I wanted to boot from the CD, the BIOS would have made that decision already!  Seems a little drastic for Ubuntu to punish you for forgetting a CD in the drive with a 220 second boot...

---

