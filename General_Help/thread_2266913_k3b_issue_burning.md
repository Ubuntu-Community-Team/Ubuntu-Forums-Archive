---
title: "k3b issue burning"
date: 2015-02-26
forum: General Help
---

### Post by carl4926 on 2015-02-26
Recently I have k3b burning a .iso - getting to 98% and then errors out.
However the DVD is playable 
The .iso is from devede and is a video
It was working OK a week or so ago
Only thing that changes is my DVD media from Verbatim to mediastar-taiyo-yuden-16x

---

### Post by carl4926 on 2015-02-26
I forgot to add this is 14.04 with the KDE PPA
Tested a parallel installation of openSUSE and the burning was fine

---

### Post by Yellow Pasque on 2015-02-26
Well, if you still have a Verbatim disc, and it works, then I think you found your answer. Maybe your DVD drive needs a firmware update to fix/add compatibility with certain disc brands.
Otherwise, you might see if k3b generates a detailed log and look at that for more info.

There is a bugfix release of k3b (2.0.3). Ubuntu 15.04 will have that version, but current releases are still using 2.0.2 (I'm not sure what version of k3b your opensuse install is using).

---

### Post by carl4926 on 2015-02-27
> **Temüjin said:**
> Well, if you still have a Verbatim disc, and it works, then I think you found your answer. Maybe your DVD drive needs a firmware update to fix/add compatibility with certain disc brands.
Otherwise, you might see if k3b generates a detailed log and look at that for more info.

There is a bugfix release of k3b (2.0.3). Ubuntu 15.04 will have that version, but current releases are still using 2.0.2 (I'm not sure what version of k3b your opensuse install is using).

To be clear.
No, I didn't have any more Verbatim. The successful burn in openSUSE was with the new media.
And, remember the burn in kubuntu, although it didn't get past 98%, once it error'd out and I ejected the DVD and then tried it, it worked as a normal movie DVD.

k3b in openSUSE is v. 2.0.80

---

