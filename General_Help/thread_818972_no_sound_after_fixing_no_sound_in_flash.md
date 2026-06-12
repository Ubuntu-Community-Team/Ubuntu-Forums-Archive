---
title: "no sound after fixing no sound in flash"
date: 2008-06-04
forum: General Help
---

### Post by mastermatt63 on 2008-06-04
Hey guys. After I fixed my sound in Flash using these solutions:

[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

 I get no sound from anything else. What could be the problem? and how can i fix it? Thanks for your help in advance.

---

### Post by werries on 2008-06-04
thats a very outdated guide. for dapper, several versions ago. use something more for hardy heron.
my opinion, is to remove that package again, change back the other thing
and then do a 
```
sudo apt-get remove libflashsupport --purge
sudo apt-get install flashplugin-nonfree
```

and then go to System > Preferences > Sound and set your defaults to alsa.

---

### Post by mastermatt63 on 2008-06-05
but will my sound in flash still be there?

---

### Post by Plasma_NZ on 2008-06-05
Yes it should... werries is right... follow what he's said to do.. it should resolve all your issues...

Side-note, if flash fails to close properly it can also "hold-on" to control of sound i found, so unticking "ESD" in System > Preferences > Sound
 can also help solve other issues, like playing 2 audio streams at a time..

---

