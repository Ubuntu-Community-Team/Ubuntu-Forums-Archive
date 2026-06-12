---
title: "ATI driver help"
date: 2008-05-01
forum: General Help
---

### Post by jSpazzoid on 2008-05-01
Hello everyone, 

I upgraded to Hardy a few days ago and ever since then my computer has been very sluggish. I think it is because the ATI fglrx driver is not working properly. I have an ATI Radeon Xpress 200M card, which ran fine under Gutsy.
Any help would be very much appreciated.
EDIT: I tried to use the Catalyst Control Center but it says that fglrx is not working probably, confirming my suspicions.

---

### Post by ryth on 2008-05-01
When I did a fresh install of Hardy I had some serious issues with scroll lag (mostly resolved).  The biggest stumbling block I encountered was xserver-xgl .  When I removed that package the speed and smoothness of operation increased significantly.

Let me know if that helps.

---

### Post by jSpazzoid on 2008-05-01
Thanks ryth, 

I noticed that Xgl seemed to be doing most of the video processing at times, as opposed to the graphics card. Running pretty good now, hopefully Xgl wasn't terribly important, I don't really need Compiz anyway. 

Thanks again!

---

### Post by danwood76 on 2008-05-01
XGL shouldnt be installed.

Its not installed on a default hardy system, a lot of people isntalled it to get beryl working about a year ago on ati cards.

---

### Post by jSpazzoid on 2008-05-02
I'm still noticing that there is no 3D rendering, and windows are jerky when moved. I think fglrx is not working fully, because I know my card can handle more.

---

### Post by Non Plus Ultra on 2008-05-02
I also did an upgrade at first (to the release candidate, to be honest). Not a good idea! No 3D performance at all.
i did a fresh install of Hardy LTS through WUBI, and even compiz works with all eye candy on (I' m so happy! ;)). So doing a fresh install might solve some of your problems.

---

