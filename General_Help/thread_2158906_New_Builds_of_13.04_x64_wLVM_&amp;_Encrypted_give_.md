---
title: "New Builds of 13.04 x64 w/LVM &amp; Encrypted give /dev/mapper/this--vg-swap_1 Error"
date: 2013-07-01
forum: General Help
---

### Post by jamesisin on 2013-07-01
I have built several new machines over the weekend using the 64 bit version of Ubuntu 13.04.  I built them with LVM and home directory encryption.  All of them pause before the login screen because they are trying to find /dev/mapper/this--vg-swap_1.  The "this" designation I am familiar with only as it relates to the live CD.  I was able to get rid of this error by commenting out the appropriate line in /etc/fstab which made the reference.

Why is it there and why are all these systems unable to find the referent?

(I used the standard live CD installed onto a thumbdrive running YUMI to effect all of the installations.  About half were run from the live CD and installed from that deskop and about half were simply installed directly from the installer.)

---

### Post by jamesisin on 2013-07-02
Nobody else is seeing this?

(Great.  This thread is the top hit on Google for this error.)

---

### Post by jamesisin on 2013-07-06
Nobody?

---

