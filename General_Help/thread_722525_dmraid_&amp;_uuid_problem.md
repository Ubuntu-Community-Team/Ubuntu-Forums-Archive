---
title: "dmraid &amp; uuid problem"
date: 2008-03-12
forum: General Help
---

### Post by Klement on 2008-03-12
Hi, I have nvidia fakeraid(s).

1.) system disk - was at some time in the past a striped raid, but one disk had to go and I destroyed the stripe in bios and used it as a single drive
2.) data - is a mirror raid

I installed ubuntu on 1.) (/dev/sda1), without using dmraid and yesterday I tried it, wow, worked great, got the data from 2.) no problem there.
But, today, boot failed, I got (initramfs) prompt with error(s): 
dmraid: rebuilding degraded array /dev/mapper/some-crap (or something like that)
mount: /dev/disk-by-uid/some-other-crap: Device or file not ready. (or something like that)

I thought, hey, the uuid is probably wrong, but guess what ... nope, its the same, vol_id says the uuid for the mapper device is the same as for /dev/sda1.

The question is, how do I fix this .. and BOOT?

---

### Post by Klement on 2008-03-15
problem solved by using dmraid -E to delete metadata from /dev/sda1

---

