---
title: "installation problem or you may be out of diskspace..."
date: 2007-12-09
forum: General Help
---

### Post by B34ST1Y on 2007-12-09
I was installing my realtek audio driver from the realtek website, and when I rebooted I got 


"your session only lasted less than 10 seconds..etc etc.....installation problem or you may be out of diskspace. Try logging in wiht one of the failsafe sessions to see if you can fix the problem"


-----


has anyone encountered this before? HELP!

---

### Post by taurus on 2007-12-09
Boot into recovery mode from GRUB menu and check your disk space.

```
df -h
```
If it says 100% used  for / (the first line), then you are running out of disk space.  Create some space with

```
apt-get clean
df -h
```

---

### Post by B34ST1Y on 2007-12-09
its impossible that i'm out of space, I can install just about anything else....but (ive reinstalled 3 times because of this problem...its getting annoying T_T lol ) when I try to install the realtek audio driver, I reboot and have gotten this problem *every* time.

---

### Post by B34ST1Y on 2007-12-10
??? *bump*

---

