---
title: "what happen to maya? because the driver of graph adapter???"
date: 2007-06-24
forum: General Help
---

### Post by arsui on 2007-06-24
as you see below; the view window of maya not normal. and very not stable, often quit itself without inform me :( 

i think is the problem of my graph adpter, it is "Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
and the driver i give him, is [COLOR="Red"]sudo apt-get install 915resolution [/COLOR] , 
and also xserver-xorg-video-intel

now, any other app is ok, only maya which is the most i like in linux. Can I find solution for it ?

Thanks your attention!

---

### Post by arsui on 2007-06-24
ok, i found it,
------------------------ 
add the following section to /etc/X11/xorg.conf:
Section "Extensions"
  Option "Composite" "Disable"
EndSection
-----&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;&#65293;
but i don't like this, :( ~~~~~ and, not complete solute the problem, it also quit auto~

---

