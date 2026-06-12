---
title: "Xorg high cpu usage"
date: 2013-11-11
forum: General Help
---

### Post by ruddi on 2013-11-11
When I move the cursor around the screen like a maniac xorg uses 100% of one of my cpu cores, have searched all around the interwebs and havent found anything to fix this.
I tried to do a fresh install just for fun and changed the drivers to 331.20 (I was using 319.xx before i reinstalled the system)

Thanks in advance :) 

System: 
Ubuntu 13.10 x64
i7 3770K
gtx 760 (331.20)

---

### Post by Topsiho on 2013-11-13
Seems logical to me.

You alter the screen "like a maniac", so Xorg has to work like a maniac too, updating the cursor position all the time.

I did this too, on my 12.04 computer, and Xorg was almost instantly the top user.

Topsiho

---

### Post by ruddi on 2013-11-13
So this is normal? 
This does not happen when I am using my windows partition, when i move the cursor slowly across the screen this still happens

---

### Post by startas on 2013-11-13
Windows is a different thing, there is no malfunctioning on windows, but for linux it is ok.

---

### Post by ruddi on 2013-11-14
I managed to fix this by downgrading the nvidia driver to 319.32 (the proprietary, tested in additional drivers, I tried the 319-updates but the problem was still there)
Now xorg only uses 0-15% of the cpu

---

### Post by ruddi on 2013-11-14
Seems like I jumped the gun there. Xorg still uses up to 100% of the cpu, but the weird thing is when I play a video in vlc for a couple of minutes Xorg relaxes and only uses 0-15% and it remains so even though I exit vlc, only way to reconstruct the problem is if I reboot.
Any ideas? :)

---

### Post by ruddi on 2013-11-21
Anyone have any ideas? :)

---

