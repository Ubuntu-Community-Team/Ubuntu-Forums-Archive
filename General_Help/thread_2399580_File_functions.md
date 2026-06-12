---
title: "File functions"
date: 2018-08-27
forum: General Help
---

### Post by sundaresh on 2018-08-27
I would like the libc of my UBUNTU LINUX installation to be 64-bit and not 32 bit, so open can open a file larger than 2GB. I downloaded and installed the UBUNTU image and even though it was for a 64-bit architecture, I am not sure whether the open() function is actually open64(), since by default these may probably still have been compiled for 32 bit file access, like it was on my previous UBUNTU installation. To avoid all such problems ideally I would like to use glibc in my system and not LINUX libc at all, but that may not be possible I suppose , since glibc was clearly not written for LINUX ?  BTW hoping I am not falsely maligned as a scammer of a spammer for making this request, but I have developed and tested a Perfect hash library, which is order preserving , for any two keys K1, K2, if K1 > K2 , then hash(K1) >= hash(K2) , with O(1) access time. Collisions for 100000 random 64-bit keys mapped to 32-bit hash values is virtually 0 almost always. Is there any to make this available to users of UBUNTU , should they wish to download it ?

---

### Post by spjackson on 2018-08-27
On 64-bit Ubuntu, for a 64-bit application, open() will open files larger than 2GB.

---

