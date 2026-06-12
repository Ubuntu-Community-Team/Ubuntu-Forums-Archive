---
title: "Is this possible"
date: 2006-11-01
forum: General Help
---

### Post by ianmacgregor on 2006-11-01
I"m running Ubuntu 6.06.1 LTS (Dapper) and I have a few .mpeg files from a friend's wedding. Her stand-alone DVD player doesn't play .mpeg files so I was thinking about taking these .mpeg's and making a DVD that will play on the stand-alone DVD player.

Question 1. Is this even possible?

Question 2. If this is possible, how would one do it? Which apps are needed? Is there a tutorial for this?

I can't use wine because winfecfg freezes the entire system, so I'll need to do this in Linux.

I did a search in Synaptic for things like mpeg2dvd and "convert mpeg to dvd", but I'm afraid I am not a video guru like some of the good folks who frequent these forums.

Thank you in advance.

---

### Post by lonce on 2006-11-01
Do a search for create DVD's and it will list a couple threads for how to do it.  I have done it a couple times.  Its pretty straight forward.

---

### Post by ianmacgregor on 2006-11-01
> **lonce said:**
> Do a search for create DVD's and it will list a couple threads for how to do it.  I have done it a couple times.  Its pretty straight forward.

Thank you :)

---

### Post by lonce on 2006-11-01
No problem. I am here to help.

---

### Post by ianmacgregor on 2006-11-01
For anyone interested, I found a nice little app called Devede. 
From the Devede homepage:

"DeVeDe is a program to create video DVDs and CDs (VCD, sVCD or CVD), suitables for home players, from any number of video files, in any of the formats supported by [Mplayer]("http://www.mplayerhq.hu/"). The big advantage over other utilites is that it only needs **Mplayer**, **Mencoder**, **DVDAuthor**, **VCDImager** and **MKisofs** (well, and Python 2.4, PyGTK and PyGlade), so its dependencies are really small."

The homepage can be found here: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

Devede is a Python app with a glade gui and comes with its own install.sh and uninstall.sh scripts. I verified these two files and it appears safe to install (doesn't install/replace/uninstall any files it shouldn't).

Devede is currently converting some .mpeg's and .avi's to a playable DVD for me. I'll know how it turns out when I burn the DVD to a DVD+R.

[COLOR=Red]UPDATE[/COLOR]: It worked. I used Devede to create a DVD from all the wedding .mpeg files my friend had and the DVD plays flawlessly in a stand-alone DVD player.

---

