---
title: "sdxc card visible but not accessable"
date: 2016-02-17
forum: General Help
---

### Post by bdubawoop on 2016-02-17
thinkpad e550 laptop with win7 & just installed ubuntu 14.04lts, 64b

i have a transcend 128gb sdxc card plugged in & while it shows on the ubuntu access bar on the left, clicking it does nothing.

the hard drive partitions are shown there also & i can access them ok.

the sd card works fine in win7

---

### Post by Bucky Ball on 2016-02-17
*Thread moved to **General Help**.*

Is it by any chance formatted in exFAT? I had this issue just two days ago with an SDXC card I bought for my camera. Never used one before, shot about half an hour's footage, shoved the card in my computer, couldn't open video files. 

Check you have exfat-utils and exfat-fuse installed then try again. Worked a treat for me.

---

### Post by nerdtron on 2016-02-17
Looks like the sdxc card has exFAT filesystem format. Try installing the exFAT driver from the answer page on this link: [http://askubuntu.com/questions/664765/unable-to-mount-128gb-micro-sdxc-storage-card](http://askubuntu.com/questions/664765/unable-to-mount-128gb-micro-sdxc-storage-card)

---

### Post by Bucky Ball on 2016-02-17
> **nerdtron said:**
> Looks like the sdxc card has exFAT filesystem format. Try installing the exFAT driver from the answer page on this link: [http://askubuntu.com/questions/664765/unable-to-mount-128gb-micro-sdxc-storage-card](http://askubuntu.com/questions/664765/unable-to-mount-128gb-micro-sdxc-storage-card)

Snap. I'm getting deja vu or there's an echo in here today! :D

---

### Post by bdubawoop on 2016-02-18
thanks, installing exfat-utils  & fuse worked.

---

### Post by Bucky Ball on 2016-02-18
Good news. Please see the first link in my signature to mark thread as solved.

Enjoy! :)

---

