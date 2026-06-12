---
title: "Resource monitor?"
date: 2005-08-05
forum: General Help
---

### Post by chadwick359 on 2005-08-05
What does everybody here use for a resource monitor?

---

### Post by astronerd on 2005-08-05
Well there are a few resource monitors out there, I guess it depends on how many things you want to monitor and how fancy you want them.  I use gkrellm, which can be gotten from synaptic(I recomend the transparent theme) but I have also used gdesklets and the system monitor that comes with gnome.  I found that if you leave your computer on for a while gdesklets just eats too much memory.  I have 1 Gb ram and gdesklets would eat like 20% of it after 3-4 days uptime.  But it has a much "prettier" look then gkrellm with more eye candy and things that can be adjusted.  This is obviously only a few of them out there, those are just the ones Ive used. 
hope this helps a little, 
Charles

---

### Post by chadwick359 on 2005-08-05
I have used gkrellm, but i found that I didnt like any of the themes that were available at the time. I do want somehitng that looks nice, but your right, 20% RAM consumption is a lot. I'll still d/l and check it out.

---

### Post by craigevil on 2005-08-05
There is also torsmo and xosview. Both use very few resources. They are not as pretty as gkrellm or gdesklets.
Both are available via Synaptic.

---

### Post by chadwick359 on 2005-08-05
wow, after checking out both of them I all but fell in love with torsmo. just have to figure out how to move it, and how to get it to stop only half drawing.
Thanks a ton.

---

### Post by astronerd on 2005-08-05
Chadwick, if you manage to get torsmo working on gnome can you tell me how you did it?  I got it from synaptic to try it out and every time I try to click on it it dissapears, but only partly.  Then it says it cant find my ~/.torsmo file so I cant go in and change things up.  It looks cool, but on the readme file it said that it doesnt work well on gnome at all.  Anyone else got it working?

---

### Post by bdamon on 2005-08-05
[QUOTE=astronerd]Anyone else got it working?[/QUOTE]

I have it working. I started working on my torsmorc some time ago and never got around to finish it. what I have seems to be fine under Gnome. To move the display  hold down the alt key and left click, you can then drag it anywhere on the desktop.

Ben

---

### Post by astronerd on 2005-08-05
[QUOTE=bdamon]I have it working. I started working on my torsmorc some time ago and never got around to finish it. what I have seems to be fine under Gnome. To move the display  hold down the alt key and left click, you can then drag it anywhere on the desktop.

Ben[/QUOTE]
 Did you get it from synaptic or compiled it from source?  Cause I still cant edit anything because it cant find my ~/.torsmo file.  Should I just copy yours and add one?

---

### Post by ow50 on 2005-08-05
Hardware Monitor and Netspeed panel applets. Note that the Hardware Monitor package in Hoary repositories is broken.

---

### Post by bdamon on 2005-08-05
[QUOTE=astronerd]Did you get it from synaptic or compiled it from source?  Cause I still cant edit anything because it cant find my ~/.torsmo file.  Should I just copy yours and add one?[/QUOTE]


I installed from synaptic. Yes use my .torsmorc for a starting point if you wish.


Ben

---

### Post by chadwick359 on 2005-08-05
Astronerd, you will actually be looking for a file called .torsmorc it isnt installed by default, however, so you need to extract it from /usr/share/doc/torsmo/examples/torsmorc.sample.gz
 and rename the torsmo.sample to .torsmorc and move it to your home folder. For it to work properly, you will also need to edit that file to draw in it's own window. by changing the 'own_window" line to read yes.

---

### Post by deancolinux on 2005-08-11
Hello on the Torsmo webpage it shows a screenshot "PiX's torsmo" How do you monitor the weather and music that is playing??

The site is at [http://torsmo.sourceforge.net/index.php](http://torsmo.sourceforge.net/index.php)

---

