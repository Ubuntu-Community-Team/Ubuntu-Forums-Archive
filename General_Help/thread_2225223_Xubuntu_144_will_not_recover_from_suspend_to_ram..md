---
title: "Xubuntu 14:4 will not recover from suspend to ram."
date: 2014-05-20
forum: General Help
---

### Post by bryncoles on 2014-05-20
Hi All.  

I have recently upgraded by laptop (Dell Inspiron 1525n) to Xubuntu 14:4 from Xubuntu 13:10.  Now when I suspend to ram, it will not wake up.  Suspend and hibernate have always worked correctly on this laptop under Ubuntu (indeed it came with Ubuntu installed on it).  

Any idea how I can resolve the problem?  Thanks all!

---

### Post by sam_baker2 on 2014-05-20
I always use rtcwake with the suspend to memory option.
Works on my desktop as well as my laptop.
Try it, it may work on your laptop.

---

### Post by sam_baker2 on 2014-05-20
By the way, I use 12.04

---

### Post by bryncoles on 2014-05-21
Hi sam_baker2.  

Thanks for helping.  How do I use rtcwake?  I had a quick gander at the man page but it is not *quite* clear to me...

---

### Post by sammiev on 2014-05-21
> **bryncoles said:**
> Hi All.  

I have recently upgraded by laptop (Dell Inspiron 1525n) to Xubuntu 14:4 from Xubuntu 13:10.  Now when I suspend to ram, it will not wake up.  Suspend and hibernate have always worked correctly on this laptop under Ubuntu (indeed it came with Ubuntu installed on it).  

Any idea how I can resolve the problem?  Thanks all!

You're possibly seeing this bug: Black screen after login from suspend in Xubuntu 14.04. Try removing light-locker and light-locker-settings and installing xscreensaver to solve the issue of buggy suspend/resume or wait for the fix.

---

