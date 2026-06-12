---
title: "Not booting: I/O resource not free, cannot open /dev/root"
date: 2007-09-07
forum: General Help
---

### Post by elinap on 2007-09-07
Thinkpad T41 with dual boot ubuntu(7.04 with all updates)/windows.
Was working fine, until can not boot from installation on hard disk. Can boot from the CD using Live CD.

Some of the messages that appear on screen during boot:
- ide1: I/O resource 0x376-0x376 not free.
- ide1: ports already in use, skipping probe
- register_blkdev: cannot get major 3 for ide0
Done.
/init: /init: 1: cannot open /dev/root: No such device or address
and some other messages: mounting problems.

and it drops into BusyBox.

Can anybody suggest how to fix this?

Thanks very much, and I would appreciate if you could email cc to [email]napchan@gmail.com[/email]

Eli

---

### Post by jnorthr on 2007-09-07
Can you boot into windows ? Do you see the supergrub menu offering you choices as to which o/s to boot ? Probably wrong on this but memory x378 sounds like what's used for parallel port operations. Have you connected or discon a printer lately ?

---

### Post by elinap on 2007-09-16
Yes, I can boot into windows.
Using LILO as boot manager, and getting the choice between windows and linux.

Nothing has been done on parallel port, or with a printer. The port that is busy is 0x376.

Any other suggestion?

thanks.

Eli

(please cc reply to [email]napchan@gmail.com[/email])

---

