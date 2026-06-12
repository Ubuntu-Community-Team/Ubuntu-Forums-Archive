---
title: "Mplayer can't resize video"
date: 2005-04-23
forum: General Help
---

### Post by wolf0403 on 2005-04-23
I've searched in this forum but seems no one has got this problem 

I've just install Ubuntu Hoary 5.04 on my Athlon XP box. Everything worked smoothly except for Totem (is that because it's Totem-gstream and I've disabled gstream in gconf?). I had a really good experience running mplayer in my old FC3 system so I decided to replace Totem with mplayer. After installing it from synaptic, it works just fine for mp3s and other audio files. Videos are fine to play but the view can only be the original size. I tried the 'f' key which should make it fullscreen, also I've tried to resize the view in gmplayer mode. For both actions, I get a really big black screen but the picture is still at the original size in the middle. What should I do with it?

My box: Athlon XP 1600+, 256M DDR, nVidia GeForce MX 400 and the mplayer package I installed was mplayer-k6 1:1.0-pre6-0.3ubuntu6

Any ideas?

---

### Post by Pluk on 2005-04-23
use a different video ouput driver or use zoom

open /home/username/.Mplayer/config with a texteditor and add:

vo= xv
or 
zoom=1

---

### Post by wolf0403 on 2005-04-23
[QUOTE=Pluk]use a different video ouput driver or use zoom

open /home/username/.Mplayer/config with a texteditor and add:

vo= xv
or 
zoom=1[/QUOTE]

Ye, got zooming working fine with xv=gl2. Thanks for that

---

