---
title: "Weird graphics problems when playing video"
date: 2012-12-22
forum: General Help
---

### Post by ryanyeah on 2012-12-22
So occasionally, I will be watching video in a media player (happens in both VLC, Movie Player etc) and the screen will go all fuzzy. It will then remain like this until I minimize the window to a smaller size. I can still hear the audio fine at this point but can't see any video. The issue can be fixed with a reboot but it pops up regularly. I've tried running it through VLC in a terminal, but could not see any relevant logging. Has anyone ever heard of a similar bug to this? I am also running AMD catalyst drivers. 

This is what the video looks like: [http://i.imgur.com/XwbWl.jpg](http://i.imgur.com/XwbWl.jpg)

---

### Post by ryanyeah on 2012-12-23
Bump. Even if someone wants to throw out some terms that I should research, I'm willing to investigate a bit myself.

---

### Post by lakerssuperman on 2012-12-23
Did you change the video output setup in any way?  I usually leave it at default, but there are other options like X11 and OpenGL that can cause issues with composited desktops which can all in turn not work well with the AMD drivers.

---

