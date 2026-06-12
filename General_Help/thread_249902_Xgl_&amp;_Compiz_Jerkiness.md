---
title: "Xgl &amp; Compiz Jerkiness"
date: 2006-09-03
forum: General Help
---

### Post by mt_holden_ss on 2006-09-03
Hey i recently managed to get my desktop to dual boot ubuntu and win xp, and i got xgl & compiz on ubuntu, and ive only noticed this recently that there seems to be some jerkiness or lag as you may call it when changing workspace, rotating the cube. When i didnt dual boot and just had ubuntu i dont recall that hppening, although  then again thought it could be the recent xgl and compiz updates. So yea can anyone help me with this cause the jerkiness and lag is starting to really annoy me. 

Thanks much, Michael

---

### Post by ayoli on 2006-09-03
If you mean the rotation speed and zooming of the cube when changing desktop, launch gconf-editor and adjust these two keys:

speed:
```
/apps/compiz/plugins/rotate/screen0/options/speed
```
increase number for spdest rotation.

zoom:
```
/apps/compiz/plugins/rotate/screen0/options/zoom
```
set to zero if you don't want zoom on cube rotation.

---

### Post by mt_holden_ss on 2006-09-04
It could be the zoom thats causing the jerkiness and lag but i recall it worked fine when i purely had ubuntu as my main os, but now i dual boot ubuntu and win xp. Its just the initial cube rotate that is the prob...but ill try what u said to see if that helps...

Michael

---

### Post by usergentoo on 2006-09-04
Im having problems too with a recent xgl update. Mine use to be flawless but now when I spin the cube it sometimes hangs and dosent spin at all but it still switches desktops. Sometimes it works fine sometimes it dont.

Is there a way to see the most recent packages Ive updated so I can go back to an older package?

---

### Post by mt_holden_ss on 2006-09-05
try this in the terminal or as a start up script: compiz-start

---

