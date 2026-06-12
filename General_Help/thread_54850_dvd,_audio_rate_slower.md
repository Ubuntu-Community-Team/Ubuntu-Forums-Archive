---
title: "dvd, audio rate slower"
date: 2005-08-06
forum: General Help
---

### Post by blu.gecko on 2005-08-06
Ok the issue at hand is this, I tried for the first time to watch a dvd on xine-ui, it worked but the audio was alsways one step behind, not sure why, I took [these](http://ubuntuguide.org/#codecs) steps and everything worked, the only problem was my audio was choppey.

does vlc have all the audio codecs built in the application like the win32 edition?
if so I will merge to vlc :roll:

---

### Post by kosmic on 2005-08-06
if your dvd is for example /dev/hdd, try to do this in a console

sudo hdparm -d1 /dev/hdd

and then try to see the movie again.

For me the best player is VLC

---

