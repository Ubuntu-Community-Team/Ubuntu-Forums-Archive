---
title: "Weird behaviour of mozilla-mplayer"
date: 2005-05-17
forum: General Help
---

### Post by Morimando on 2005-05-17
Something is wrong with the mozilla-mplayer plugin over here.
I first tried the one from synaptic (only the hoary version is installable here), but had to experience that it won't work, it loads the video but views it in the upper left and in the upper middle of the screen (yes, 2 "windows") the video then is a) smallo and b) totally pixeled/unviewable. Second i tried the mplayer testing package from Debian which i installed using dbpk -i .. unfortunately it produces the same weird view as the synaptic-version.
Mplayer itself works almost normal, although it crashes from time to time with error 11 which i suppose is because it has issues with memory (which is kind of fully used because of Azureus *damn new version*). Running mplayer-586 without Azureus in background runs okay most times. Any ideas?

---

### Post by harryc on 2005-05-17
Open /etc/mplayerplug-in.conf in gedit and uncomment the following line - 

#vo=xv,x11

Try the following options one at a time;

vo=xv

vo=x11

---

### Post by Morimando on 2005-05-17
unfortunately both won't work. I also tried vo=gl and vo=gl2, still not working.
In fact, it ceizes to show anything now.

---

### Post by harryc on 2005-05-17
Did you install exactly per the ubuntuguide? If not, uninstall and reinstall Mplayer-386, mplayer-fonts, and mozilla-mplayer. It works fine for me here and I did nothing more than follow the guide...unless you are having some sort of video driver issue. Did you load a video driver? Try unloading it if the above fails. 

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by Morimando on 2005-05-17
i had mplayer-586 installed (sarge version) uninstalled and installing mplayer-386 now (ubuntu hoary version).. maybe that does it, we'll see in a minute.

Nope.. same issue.. maybe i shall see to installing hoary version of libavcodec and such stuff?

edit2: changed libavcodec and libpostproc to the woody version, but didn't help at all :( unfortunately there's no hoary version of libavcodec so i can't apply hoary versions of both. it's a PITA that one has to mix sarge woody and hoary versions to get a multimedia system that's of use, i think that's a big flaw of ubuntu..

---

### Post by Morimando on 2005-05-18
<bump>

---

### Post by lorap on 2005-05-18
hi!
if you install VLC plugin for firefox(mozilla) the problems you being facing will go :-)
have a nice day.
pavel

---

### Post by Morimando on 2005-05-19
Thanks, i'll give it a try :)

---

### Post by ohman11 on 2005-05-19
Mine d/ls the movie and then just hangs and now if I right click to save a file it closes the browser

---

### Post by Morimando on 2005-05-20
[QUOTE=ohman11]Mine d/ls the movie and then just hangs and now if I right click to save a file it closes the browser[/QUOTE]
sounds similar. I'd suggest you give vlc plugin a try, i love it ^^ just have to figure out how to tell it to use esd sound server

---

