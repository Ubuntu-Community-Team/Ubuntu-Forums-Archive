---
title: "MP3 Codecs without having internet"
date: 2005-08-03
forum: General Help
---

### Post by cyberdancer on 2005-08-03
I have ubuntu installed on my computer but i dont have internet(my wireless network card doesn't work at all). 
So I want to play MP3 but when I follow the guides on internet it doesn't work. I presume that it is because my network doesn't work.

Has anybody an solution for me ?

Sorry about my crappy english

---

### Post by Zelut on 2005-08-03
well it sounds like you do need the packages for the MP3 support.  It looks like you have some access (whether thru another box or via Windows I don't know).  If you just want MP3 support I'm sure someone can attach the package needed.  Let us know if you want any other packages as well.

---

### Post by cyberdancer on 2005-08-03
Yes my wireless network card works in windows bu not in linux.

I want to play mp3. Avi or mpg, is that also included? These codecs would be usefull too.

---

### Post by Zelut on 2005-08-03
It'd probably be the easiest to use a wired connection just to install those packages & then move the notebook back to its un-wired connection afterwards.  If you can plug it in for five minutes I'm sure you can get the packages.

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

---

### Post by cyberdancer on 2005-08-03
I know but it is an standalone computer(no notebook) and i dont have a wire of 20meters.
I hope there is an easy way(download the codecs in windows and "say" apt-get where he must seek the codecs). I am a beginner, I don't know if that is possible.

Using wired lan is the last option(because it costs a lot of work to unplug the computer, bring it to the router, pluging in, pluging out, bring it upstairs, pluging in)

---

### Post by artinla on 2005-08-03
See my thread from today about the Unofficial Extras CD that can be downloaded.   I can't remember the URL but it installs most of what you want.

Art

---

### Post by cyberdancer on 2005-08-04
Looks nice, I will try this tonight.

Thanks !

---

### Post by Joeb on 2005-08-04
[QUOTE=cyberdancer]Yes my wireless network card works in windows bu not in linux.

I want to play mp3. Avi or mpg, is that also included? These codecs would be usefull too.[/QUOTE]

Others have answered about your codecs problem.  I thought I would ask if you have looked at the ndiswrapper package?  It seems to work for many people with wireless adapters.

I have not used it personally, however, so if you try to use it an run into problems, you might check the networking forum.

Joeb

---

### Post by cyberdancer on 2005-08-04
I have no time tonight, it will be tomorrow.

I have tried ndiswrapper, but it didn't work.
But i have found an linux driver, I will try this also tomorrow. But its for kernel 2.4 i think, and I have 2.6. But these questions will be answered tomorrow, if i find the time to do it :wink:

---

