---
title: "xwinwrap and electricsheep"
date: 2016-11-30
forum: General Help
---

### Post by mirrar on 2016-11-30
Hi

I try since few hours to send electricsheep screensaver as wallpaper. Each 30-minutes i success a new thing (configure, packets, makes, ....) but now i don't found a solution since two hours.
I've success to install electricsheep on a fresh installation of ubuntu 16.04-1 from github. I've found many tutorials and i've found xwinwrap to send electricsheep to wallpaper (thanks the comunity!!). But i thing that the flag "nf (no focus)" don't works because i can select the wallpaper. I must do alt+tab to switch application. Do you have any idea about it?

My command is inspired from [https://ubuntuforums.org/showthread.php?t=350089&page=4](https://ubuntuforums.org/showthread.php?t=350089&page=4) :

xwinwrap -ni -o 0.3 -fs -s -st -sp -b -nf -debug -- /bin/electricsheep --mplayer -1 -window-id WID

Regards.

---

### Post by jlfh0816 on 2017-02-09
Hello

I had the same same issue as you. I found a solution on this site [https://dolys.fr/forums/topic/electricsheep-des-moutons-electriques-pour-animer-votre-fond-decran/](https://dolys.fr/forums/topic/electricsheep-des-moutons-electriques-pour-animer-votre-fond-decran/)

(Google English translation available on this site)

Good luck and hope it will work for you too!

---

