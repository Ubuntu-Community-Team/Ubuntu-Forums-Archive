---
title: "ufw won't stay enabled"
date: 2012-11-22
forum: General Help
---

### Post by Frank P on 2012-11-22
12.04 LTS server
after enabling ufw status sometimes says inactive and sometimes active. But even if it reportsa active a shrt time later it reports inactive again.
I have removed & purged ufw and reinstalled and opened ports but same thing keeps happening

---

### Post by Locus Kiesselbachi on 2013-02-11
I tought I had problems with gufw once, maybe it helps you too:
[http://ubuntuforums.org/showthread.php?t=2113014](http://ubuntuforums.org/showthread.php?t=2113014)

---

### Post by Bufeu on 2013-02-11
I had the same problem. I was reinstalling, reconfiguring and searched for the error several hours. Then, someone asked me if a had any other firewall installed at the same time, and yes. I had Firestarter. I purged Firestarter and ufw worked. :)

---

