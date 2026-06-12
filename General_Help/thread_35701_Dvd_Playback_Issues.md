---
title: "Dvd Playback Issues"
date: 2005-05-19
forum: General Help
---

### Post by djpharoah on 2005-05-19
hi...have read the forums quite a bit and have found taht dvd playback is really a big issue on here. I have switched my laptop form Gentoo to Ubuntu, but am still keeping gentoo for my amd64. 

Anyways, i have followed the numerous guides on the ubuntuguide.org site, the forums, the HOW-TOs but i still cant play a dvd!!

WTH am i doing wrong??
the closest i get is with xine-ui playing the audio but having a BLUE screen as video output..

any ideas would be great...

---

### Post by kori.mendocino on 2005-05-21
make sure you have libdvdcss2 installed, and try some other players other than xine, for example vlc, mplayer, ogle, etc. btw my personal favourite is vlc [aka videolan], it is in the repos

---

### Post by JaF on 2005-05-21
[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)  :)

---

### Post by davidgypsy on 2005-05-21
[QUOTE=djpharoah]hi...have read the forums quite a bit and have found taht dvd playback is really a big issue on here. I have switched my laptop form Gentoo to Ubuntu, but am still keeping gentoo for my amd64. 

Anyways, i have followed the numerous guides on the ubuntuguide.org site, the forums, the HOW-TOs but i still cant play a dvd!!

WTH am i doing wrong??
the closest i get is with xine-ui playing the audio but having a BLUE screen as video output..

any ideas would be great...[/QUOTE]

The only issue I have had with playing DVD's has been the DMA settings on my DVD Rom. By running the following script, which I got from someone on this forum  :) it got sorted out and doesn't jump any more. If your problem is with jumpy playback, try this.

sudo hdparm -k1 -c3 -d1 /dev/hdc

This, of course, is after installing the libdvdcss2 that kori.mendocino was talking about.

I have had great success with Xine as a DVD player.

---

