---
title: "Mplayer and .bin files"
date: 2005-05-24
forum: General Help
---

### Post by thoms on 2005-05-24
Ok, so I've just downloaded a movie and it came with a .bin and .cue file. My problem isn't playing it, although xine and totem won't, mplayer does but when I do, the image is very small and when I make Mplayer fullscreen, it stays at that size. Any suggestions?

---

### Post by Leif on 2005-05-24
Use vlc

---

### Post by Gouchi on 2005-05-28
Which video output did you use ?
try -vo xv -fs if it didn't work, try with other video output, check -vo help.

#mplayer -vo xv -fs your movie

#mplayer -vo help

---

### Post by arnieboy on 2005-05-29
the solution to the problem is the following:
in a terminal type:
sudo gedit /etc/mplayer.conf
when it opens the mplayer configuration file, look for the line "zoom"
change the line "zoom=no" to "zoom=yes"
save the file and exit.
That will solve your problem

---

