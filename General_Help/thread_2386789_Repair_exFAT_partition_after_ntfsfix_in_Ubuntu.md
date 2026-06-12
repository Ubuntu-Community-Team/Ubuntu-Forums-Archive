---
title: "Repair exFAT partition after ntfsfix in Ubuntu"
date: 2018-03-10
forum: General Help
---

### Post by Melano Chole on 2018-03-10
I did a stupid thing a week ago, trying to run *ntfsfix* on a exFAT-formatted USB stick. Of course, that destroyed the data. I am still able to recover 99% of the files with *photorec*, but would prefer to get the entire directory tree. It is more of a curiosity, not a real need.

I have tried the following:
- ran *testdisk*, but it won't working because treats the partiion as NTFS;
- overwrite the first 512 bytes of the damaged partition with another 512 bytes taken from a clear exFAT partition using *dd;*
- re-format the partition with *mkexfatfs* and then try *testdisk* again. (I saved an image of the partition with *ddrescue* right afrer the damage and wrote the image on the stick before every attempt, so previous experiments did not affect the following ones).

Obviously, none of that worked. Are there other things I should try?

---

