---
title: "Approx. 2.7GB of unaccounted for space likely caused by Ubuntu Customization Kit"
date: 2012-10-14
forum: General Help
---

### Post by Sublymonal on 2012-10-14
So I've been working on creating a custom install disk for one of my professors. I decided to go ahead and use Ubuntu Customization Kit to do so. Problem is, I made a mistake the first time 'round and had to close out. Unfortunately, it seems that it left 2.7gb of space occupied that I can't seem to hunt down. The Disk Usage Analyzer says that I'm using 14.3GB, but that there's only 11.6 being used in /.

Let me know if there's anything else I can do to get more details.


note that I have run uck-remaster-clean-all

---

### Post by Tralce on 2012-10-15
Try running the Disk Usage Analyzer as root... open terminal, type sudo baobab and hit enter. Search / and you'll find it.

---

