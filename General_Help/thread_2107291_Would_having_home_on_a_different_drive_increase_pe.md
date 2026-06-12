---
title: "Would having /home on a different drive increase performance?"
date: 2013-01-21
forum: General Help
---

### Post by jeevo on 2013-01-21
Hi!

I am wondering if i could expect xubuntu to perform better if the home directory would be placed on it's own hard-drive.

So
sda would be /
sdb would be /home

Naturally i feel that it would be faster, since the load on a single hard-drive would be less. However,  would the same still apply if sdb has a slower read speed? say 15% slower.

I am unsure of how often things are read from /home compared to /

I tried searching for some definite answers but couldn't find any. 

I am currently moving my installation from sdb (slower) to sda (faster) but i was wondering if leaving /home on sdb would be beneficial or not. I'm going to give having everything on the faster drive for a week or two now before i switch in order to get my own opinion on the matter, but if anyone had anything solid on the subject i would appreciate it.

---

### Post by CaptainMark on 2013-01-21
There are security benefits to separating root and home, but performance wont improve

---

### Post by Roasted on 2013-01-21
My /home is on another partition (a RAID mirror in fact), and there's no speed difference.

60GB SSD = /
2x1TB RAID 1 = /home

---

### Post by mcduck on 2013-01-21
In theory, yes. In practice the benefit would be very, very small, nothing you'd be able to notice outside of benchmarking tools.

(and you'll definitely want to have both root and home on as fast drive as possible, so the "15% slower" drive would be best used as a separate storage drive instead)

---

### Post by jeevo on 2013-01-21
Ah i see, thanks for all the quick answers! =)

---

### Post by TheGuyWithTheFace on 2013-01-21
As the others have said, you probably wouldn't see any performance gains, but some people recommend having your /home on a separate partition anyway, as that makes it easier to fresh install a new operating system without wiping your data.

---

