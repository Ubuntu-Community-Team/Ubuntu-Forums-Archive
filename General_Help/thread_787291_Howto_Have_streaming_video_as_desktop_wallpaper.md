---
title: "Howto: Have streaming video as desktop wallpaper"
date: 2008-05-08
forum: General Help
---

### Post by jubalj on 2008-05-08
Hi guys,

I'm running hardy on my desktop, and learnt that its really simple to have a live stream as your desktop background.

I am basically streaming a live feed of the auckland city skyline as my desktop wall paper - it saves me looking out of the window to see what the weather is! This particular feed is a good wallpaper since it doesnt have much distracting movement (Except for occasional ships/aircrafts/birds, which make it quiet cool). The downside is that the quality isnt great.. [screenshot of desktop attached,50% actual]

I used instructions from [http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html](http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html)

The steps are as follows:

1. Get some libraries
> sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs

2. Get xwinwrap from cvs, make it, and place it in /usr/bin
> cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap && cd xwinwrap && make && sudo cp xwinwrap /usr/bin

3. run the live feed using xwinwrap and mplayer
> xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound  mms://202.8.47.38/aklwebcam

NB: mplayer seems to have some bug where it crashes if i give it a hostname in the stream URL, so just lookup the hostname (nslookup) and provide a URL with an ip adrees.

Another thing to note is that you cant have icons on your streaming desktop, this isnt a problem for me, since I have dualhead with the other screen showing the icons.

Usage for a 128kpbs stream works out to about 340MB/month, if my calculations are correct. (assuming 24/7 uptime).

Hope you find this useful!

cheers
Jubal

Edit: quoted the commands, so they dont show up as smiley faces. I've created a custom launcher that runs in terminal to launch this.

---

### Post by macaholic on 2008-05-08
I may try this tomarrow when I have more time, and report back on my findings. Will be testing with 64-bit, ATI (8-4), AIGLX, and Compiz-fusion git.

---

### Post by tuomi on 2008-09-29
> **macaholic said:**
> I may try this tomarrow when I have more time, and report back on my findings. Will be testing with 64-bit, ATI (8-4), AIGLX, and Compiz-fusion git.

How did this work out? I have a similar setup and I'm interested in implementing this.

---

### Post by jubalj on 2008-09-29
still working fine for me.. its actually really easy to setup.. i'm using compiz/desktop effects as well..

---

### Post by easybake on 2008-09-29
You should still be able to keep your functional icons. The only way you would lose them is if you told nautilus to stop drawing the desktop. Xwinwrap just layers a root window over(under) your desktop. 

You can do a lot of cool things with xwinwrap. *(insert shameless plug)* Anyone can check out my tutorial on using your own webcam feed as wallpaper. NOTE: there is a toggle script in there that you would find very useful in this situation. [http://ubuntuforums.org/showthread.php?t=883176]("http://ubuntuforums.org/showthread.php?t=883176")

---

