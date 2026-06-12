---
title: "Best way to rmmod at boot?"
date: 2006-10-09
forum: General Help
---

### Post by Astro96 on 2006-10-09
Hi,
I have a laptop and I want to disable the internal speaker (not the sound -- the speaker that makes the terminal beep).  I found that using

rmmod pcspkr

does exactly what I want.  Often, however, I forget to run this at boot.  What is the best way to make this automatic?  I thought about allowing rmmod in sudoers for my user and then adding it to my session, but that seemed like a security risk.

Thanks!
Andy

---

### Post by yopnono on 2006-10-09
Put it in the /etc/rc.local script

---

### Post by ayoli on 2006-10-09
just put:
**pcspkr**
in: /etc/modprobe.d/blacklist

---

