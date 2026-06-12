---
title: "realplayer problem"
date: 2008-04-14
forum: General Help
---

### Post by Dawa on 2008-04-14
I installed RealPlayer 10 Gold for linux via the .bin file from their site.  It works well enough I guess, but the problem is it agressively took over the media on my system.  All of my mp3s were set to open with realplayer (which was easy enough to change back), but more annoyingly, all of my mp3s now have realplayer filetype icons.  I've looked around and for the life of me cannot figure out how to switch them back to the default "orange music note" icons.

any suggestions?

---

### Post by mattress on 2008-04-14
What desktop environment are you using ?

Personally I would have just installed the win32 codecs and used Totem or Mplayer...
Realplayer is nasty...

-m

---

### Post by Dawa on 2008-04-14
I solved the problem!

/home/[me]/.local/share/icons/**hicolor**

that "hicolor" folder was full of all the mimetype .png files.  I removed it and everything returned to normal.

I haven't used RealPlayer in years; I figured I'd give it another chance.  Should've known better. :-|

---

