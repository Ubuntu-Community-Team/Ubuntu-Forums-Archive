---
title: "RAID 6 ?? (not a typo)"
date: 2008-01-22
forum: General Help
---

### Post by dgray_from_dc on 2008-01-22
Anyone know whether or not Ubuntu is RAID 6 capable?  I'm preparing to put together a RAID 5 server with 4 x 250GB drives.  I've built and broken my server a few times just playing around trying to figure out what configuration is best.  I used webmin to build my arrays and I noticed a RAID 6 option in webmin.  (For those who don't know, that's not a typo, RAID 6 is the same as RAID 5 except with two sets of parity data making it capable of surviving the simultaneous failure of two drives.)  Since I plan to grow/replace the array anyway, I'm a little curious if anyone has had any experience with RAID 6 and whether or not it's even worth testing.

My thoughts on it are that there's only a very slight difference between RAID 5 + SPARE and RAID 6.  That difference being simultaneous drive fail tolerance.  Otherwise, array capacity is the same and RAID 5 probably offers better performance (only writing parity once).  I'm inclined to go ahead with RAID 5 but I'm just curious.

---

### Post by gvartser on 2008-01-22
Sounds expensive, from what I have read about raid6, the only benefit is a more redundant storage. But as for performance i doubt it. But then again, its always fun to test new things.. ;)

---

### Post by dgray_from_dc on 2008-01-24
RAID 6? . . . Anybody? . . . No?

---

### Post by fjgaude on 2008-01-25
This site tells all about raid:

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Have fun.

---

