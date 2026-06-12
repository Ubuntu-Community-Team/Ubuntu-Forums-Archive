---
title: "failed to boot and stuck in purple screen"
date: 2013-10-11
forum: General Help
---

### Post by freemant on 2013-10-11
Hi,

I have been using 12.10 for a long time and it has stopped working for a few days. More specifically, it fails to boot and gets stuck in the purple screen. There is no apparent disk activity while it is stuck. To troubleshoot, I've removed "quiet splash" and then further added "nomodeset" but neither has had any effect. That is, even with nomodeset, the purple screen is still shown! The only way that helps is boot into Windows 8 (dual-boot) and then restart, then somehow it will boot this time (next boot the problem will return).

Any idea how to troubleshoot? Thanks in advance!

---

### Post by oldfred on 2013-10-11
Is it fully shutting down?

I might look in log files.
You can try log file viewer. I look in dmesg for boot issues, but there are many others.
Also just look at files in /var/log

---

### Post by freemant on 2013-10-11
there are no special messages in kern.log nor dmesg.

---

### Post by fantab on 2013-10-12
Is your Hard Disk Healty? Boot with Ubuntu DVD/USB and "Try Ubuntu Without Installing".... run the utility 'Disks' and run tests on HDD to determine its health.
Are there any Proprietory Graphic drivers involved?
What happens if you run Ubuntu in [recovery mode]("https://wiki.ubuntu.com/RecoveryMode")?

---

### Post by freemant on 2013-10-12
I finally found the problem: somehow "secure boot" has been enforced in BIOS! Changing it back to "compatibility" mode fixed the problem.

Thanks all for the help :-)

---

