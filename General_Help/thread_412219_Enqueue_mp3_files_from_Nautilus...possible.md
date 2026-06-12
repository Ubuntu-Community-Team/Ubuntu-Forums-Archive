---
title: "Enqueue mp3 files from Nautilus...possible?"
date: 2007-04-17
forum: General Help
---

### Post by gejr on 2007-04-17
In Windows with Winamp I could right click a mp3 file in windows explorer and choose "Enqueue in winamp", I really miss such a feature with Nautilus+Banshee/Exaile. Do anyone know if it is possible in some way? When  I double-click a .mp3 in Nautilus it seems to replace whatever song is playing, and I rarely want that. Thanks!

---

### Post by hackerssidekick on 2007-04-17
See if you can find a nautilus script to do it. Google for nautilus scripts, and here's a link to get you started :D:
[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/")

---

### Post by gejr on 2007-04-17
Thanks for pointing me in that direction:)

It seems like Banshee and Exaile aren't able to do this yet. Banshee has a --enqueue trigger, but when I made a tiny script which contained:

#!/bin/bash
banshee --enqueue "$*" 

it appended it to the playlist and started playing it. I wanted it to append to the list, not start playing. Difficult for a newb to figure this out. Exaile doesn't seem to have this --enqueue trigger so i don't even know where to start, and if it's possible.

---

