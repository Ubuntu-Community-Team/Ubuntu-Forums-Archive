---
title: "Xubuntu logs me out if I open a terminal"
date: 2007-05-21
forum: General Help
---

### Post by StormGuy on 2007-05-21
Anytime I try to open a terminal, Xubuntu spits me back out to the log-in screen.  I just installed it on an old computer, so the specs for this machine aren't robust at all.  Something like 128 MB of RAM and a really dated video card (not sure about the specifics).

Any idea why the terminal isn't running?

---

### Post by ashz on 2007-05-21
check out the bug report...

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/114124)

Useful since someone else had the same prob and found this on a diff forum....

I would suggest either downloading gnome-terminal 2.something or other lol...or revert back to the edgy version...

[http://cdimages.ubuntu.com/xubuntu/releases/edgy/release/](http://cdimages.ubuntu.com/xubuntu/releases/edgy/release/)

cheers
ash

---

### Post by ashz on 2007-05-21
Hmm seems some people have changed their color depth from 24 to 16 in xorg.conf and this has fixed the problem, you might want to try that first until a bug fix has gone out!!

Cheers
Ash

---

### Post by StormGuy on 2007-05-21
That worked perfectly :)

Thanks a bunch!

---

