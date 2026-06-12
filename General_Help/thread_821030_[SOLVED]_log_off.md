---
title: "[SOLVED] log off"
date: 2008-06-06
forum: General Help
---

### Post by applehead on 2008-06-06
Hi all, 
When I click on the log off button to turn off or restart my machine nothing happens for a few minutes...

I've just upgraded to hardy but had the same problem in gusty

any ideas?

---

### Post by Joeb454 on 2008-06-06
I think this is a known bug, it may only be with certain graphics cards however - what graphics card do you have?

---

### Post by applehead on 2008-06-06
It's an NVIDIA. I'm not sure which one, I don't know how to find out in hardy.

---

### Post by Joeb454 on 2008-06-06
It'll probably tell you somewhere if you run ```
lspci
``` from a terminal :)

---

### Post by Rocket2DMn on 2008-06-06
It's
```
lspci | grep VGA
```
to just see your video card.  This is indeed a known bug, I am looking for the bug report right now.

---

### Post by applehead on 2008-06-06
ah yes

nVidia Corporation NV34 [GeForce FX 5200]

---

### Post by Rocket2DMn on 2008-06-06
Could be one of the following bugs:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/146480](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/146480)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195434](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/195434)

A lot of bug reports have been submitted, all are a little different.  However, the effect seems to be similar between all of them = a really slow shut down or log out sequence, sometimes with errors or freezing.

---

### Post by applehead on 2008-06-06
Thanks for those links.

I had the 'power manager' unchecked in   - system - preferences - sessions - startup. I just unchecked the ones I didn't think I needed, like bluetooth and evolution.

I think that should probably fix it but I can't tell since the problem goes after you've clicked it and waited once.

It's great that there's people like you out there who can help. I've been waiting three or four minutes for a shutdown. I almost hurt my hard drive by using the power button all the time. It stopped working and I had to take it out and give it a knock... works fine now :)

---

### Post by applehead on 2008-06-18
just to confirm: this did solve the problem

thanks all

---

