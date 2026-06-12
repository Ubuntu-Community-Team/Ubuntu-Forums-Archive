---
title: "[SOLVED] Poorer movie video quality"
date: 2008-02-12
forum: General Help
---

### Post by camini on 2008-02-12
Hello,

Dual boot machine Ubuntu & Vista.

I noticed that the video quality of movies I watch under ubuntu is not as good as when I watch these under Vista.

I basically use vlc under both OS.

What I see under ubuntu is some kind of 'raster' line or fault in the video.
As it does this under VLC, Mplayer and totem I figure it has to do with the video driver (nVidia) more than with the players or codecs..

Has anyone noticed this too and what can be done about it?

I really don't want to go back to Vista too often - enjoying uberuntu too much!

Thanks in advance

---

### Post by Sokertes on 2008-02-15
I haven't had that problem but I can tell you this. I ended up using Nvida's drivers right from nvidia site and the video play back was a lot better for me. Of course this was after installing kernel 2.6.24 

I used the steps at [http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel) for compiling and installing the nvidia driver and it worked like a charm.


Sokertes

---

### Post by camini on 2008-02-18
Could be something to consider.
What were you using before as a driver? Standard restricted driver method or envy or something else?

---

### Post by camini on 2008-03-04
bumping

Does anyone have a hint on how to make (windowed) video quality better with an nVidia card?

Maybe nVidia settings or a certain set of codecs to install?

All help appreciated..

Ubuntu rulez

---

### Post by camini on 2008-03-05
Solved the video problem - which was actually 'tearing', affecting the whole X.
Had to set Sync to VBLANK in nvidia settings and ccsm as well as setting my monitor's refresh rate in both to 75hz.
Not sure which of the settings solved the tearing but my X and videos are now smooth like they should be - happy!

---

