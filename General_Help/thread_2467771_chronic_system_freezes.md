---
title: "chronic system freezes"
date: 2021-10-07
forum: General Help
---

### Post by pjstock on 2021-10-07
I am running Ubuntu 20.04.3 LTS
Intel® Core™ i5-3570 CPU @ 3.40GHz × 4 
7.6 GB of Ram and a 320GB HDD

I am recently getting chronic and frequent (every hour) system freezes, both mouse and keybard not responding.

it seems like a LOT of other users suffering similar problems but not a lot of RESOLVED threads.

how do I start troubleshooting my system?

how can I find useful information (sytem logs?) that I can post here that might clarify the issues.

Peter

---

### Post by vmpx on 2021-10-12
Try disable in browser "use hardware acceleration".

---

### Post by vmpx on 2021-10-17
[B]How to fix Ubuntu 20.04 freeze after boot when NVIDIA card installed
[/B]
Replace in GRUB menu for 20.04 ”quiet splash” with ”quiet splash nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.

---

