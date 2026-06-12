---
title: "Xine not playing video dvd iso"
date: 2007-01-15
forum: General Help
---

### Post by Coop on 2007-01-15
Hello
When I try to play an iso image of a video dvd with totem-xine and vlc media player,it plays it fine.
But when I try to play the same iso with gxine and xine movie player,it says something like:```
The xine engine failed to start.No demuxer found - stream format not recognised.
```
How do I make gxine and xine movie player play the video dvd iso?
Please reply to me.
Ahmed

---

### Post by smyrman on 2008-03-29
To open with xine:
try to write this in a console (or in the ALT+F2 menue):

```
xine "dvd://path/to/my/file.iso"
```


To open with mplayer:
Rigth click the iso, choose "open with" and write "mplayer".

or write this in a console:

```
mplayer "dvd://path/to/my/file.iso"
```

Hopes this helps=)
Edit: please write again if this does not solve your problem.

---

