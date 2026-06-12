---
title: "adjusting middle-click sensitivity"
date: 2007-01-31
forum: General Help
---

### Post by xjas05 on 2007-01-31
is it possible to adjust how sensible the middle-click on my mouse is? everytime i try to open a tab on firefox, one click opens 2-3 more tabs...

---

### Post by ADK01 on 2008-05-13
I have the same problem, only my middle click is not sensitive enough, I have to click a really long time to get it to recognize one middle click event in xev and to paste things

Edit: actually, it seems that to paste properly, i have to click and release very quickly, so in a way, it is the same thing

---

### Post by ADK01 on 2008-05-13
I was actually able to fix my problem by editing Xorg.conf, I had

Emulate3Buttons "true" 
EmulateWheel "true"
EmulateWheelButton "2"

 in there, I removed those and just did 
ZAxisMapping "4 5"
 
also make sure you have the correct protocol for your mouse

---

