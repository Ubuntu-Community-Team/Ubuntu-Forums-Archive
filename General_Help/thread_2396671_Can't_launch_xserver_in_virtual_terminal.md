---
title: "Can't launch xserver in virtual terminal"
date: 2018-07-19
forum: General Help
---

### Post by Axis Mann on 2018-07-19
Wrong title.  Sorry.  Should be can't launch xserver in virtual terminal.

I can no longer launch xserver in a virutal terminal.  I've tried on tty1, tty2, tty3,...,etc, adnaseaum.  The command xinit -- :1 use to work as expected.  

But now, I just get a fatal server error: parse_vt_settings: Cannot open /dev/tty0 (permissions).  

I have three different installations: 14.04 with X server 1.17.2, 14.04 with xserver 1.18.3, and 16.04 with xserver 1.18.3.  I first noticed this problem on new install of 14.04 with X server 1.18.3 on a separate machine.

I never updated a prior install of ubuntu 14.04 which still runs X server 1.17.2.  The prior install of 14.04  still executes the xinit -- :1 as expected. I checked my 16.04  install  which is using  X server 1.18.3 (on same machine with working 14.04) and found it suffered the same problem as the new install of 14.04 running X server 1.18.3.

How would I go about diagnosing and correcting this problem.

---

### Post by slickymaster on 2018-07-19
Edited thread title

---

### Post by slickymaster on 2018-07-19
Thread closed.

Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2396673").

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

