---
title: "Moving temp folders to ram disk to improve SSD life"
date: 2014-03-21
forum: General Help
---

### Post by H3R3T1K on 2014-03-21
I've been using this guide to improve the performance of my Notebook with SSD: [http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm](http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm)

  I've edited the /etc/fstab file and added the following:

tmpfs   /tmp       tmpfs   defaultsnoatimemode=1777   0  0
tmpfs   /var/spool tmpfs   defaultsnoatimemode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaultsnoatimemode=1777   0  0     
tmpfs   /var/log   tmpfs   defaultsnoatimemode=0755   0  0

I had to remove those lines (well I can't tell for sure if removing all of them was necessary) because after a reboot I would get an  error that /tmp coulndn't be mounted. I'm assuming this is because of  the encryption (the complete one, not /home) performed during install?

---

### Post by leclerc65 on 2014-03-22
I think you should change the last '0' for a '3'
For example:
tmpfs	/tmp		tmpfs defaults,noatime,mode=1777 0 0
becomes
tmpfs	/tmp		tmpfs defaults,noatime,mode=1777 0 3

---

### Post by H3R3T1K on 2014-03-22
I got it right. Should be:

```
tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0
tmpfs   /var/log   tmpfs   defaults,noatime,mode=0755   0  0
```

---

