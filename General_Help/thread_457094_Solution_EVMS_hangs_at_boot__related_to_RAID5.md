---
title: "Solution: EVMS hangs at boot / related to RAID5"
date: 2007-05-28
forum: General Help
---

### Post by fellgoog on 2007-05-28
Hi, just a hint to anyone with the same problem:

I have a RAID5 with 5 disks. My main installation is on another disk. Sometime yesterday, one SATA disk was dropped out due to some hiccup (no real failure). I found out, shut down the system, checked the disk, inserted it again, and booted up. Then I added the disk again to the array. Everything went smooth (except that the mdadm version of 6.06 LTS server didn't support --re-add), and the array started rebuilding.

In order to check whether the array was really fine, I re-booted again.

From there on, EVMS would hang on every boot, as long as the new, additional disk was in the system. It failed with the message "glibc double free or corruption detected" and the machine would not go any further.

In the end, I removed the disk, ran a 

sudo apt-get remove evms

and everything was fine again. Maybe I'll find out more in the future, until then good luck to anyone with similar problems.

---

