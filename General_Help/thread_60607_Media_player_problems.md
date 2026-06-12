---
title: "Media player problems"
date: 2005-08-28
forum: General Help
---

### Post by pierreski on 2005-08-28
Hi there,
I just set up Ubuntu linux on a Sony PCV-RX860 (additional installed PCI cards= Linksys WMP11 v27 and Nvidia Geforce 4 card).  Everything on my system works like a dreams except the media playing.

Whenever I try to play any media file or DVD, I always get an error or an instant program freeze.  I've tried using xmms, mplayer, totem, and the included music player for almost every type of file.  Sound and video work fine in the Ubuntu desktop environment...  What could be causing this problem?

---

### Post by eivind on 2005-08-28
A way towards solution may be to start the media playing applications from a command line, and see if they produce some informative output when they crash or freeze. If you post those messages here, it could do a bit of good. 
But you are saying that sound and video function *in* the Ubuntu desktop environment? Could you specify a bit more?

Also, a possible solution is to use media players and addons from backports. I've used the howtos on [www.ubuntuguide.org](www.ubuntuguide.org) - they are simple enough for me, and they work.

---

### Post by pierreski on 2005-08-29
Great, I got everything fixed!  I found out how to play mp3 files at 
[http://ubuntuforums.org/archive/index.php/t-33071.html](http://ubuntuforums.org/archive/index.php/t-33071.html)

I used ubuntuguide.org backports to get xine so I could play DVDs and movie files.  Thanx!

---

