---
title: "mozilla-mplayer problem"
date: 2005-04-13
forum: General Help
---

### Post by Cyclonis on 2005-04-13
whenever I click on a movie link in firefox, no matter which file format (.avi .mpg .wmv .mov), the mplayer plugin loads up till 99% and then simply stops

what can I do to solve this problem?

---

### Post by Marc Higgins on 2005-04-13
same deal here, but i forced the mplayer install though some of the libs were the wrong venison (i mean version, must eat soon). anyway have followed [http://ubuntuguide.org/](http://ubuntuguide.org/) guide & .avi .mpg .wmv .mov play in xine 100% ok. yes it's not as sexy as mplayer in firefox but it works & you can tell firefox under edit preferences to use xine as your default (i'm not doing that cause i guess this will be fixed in the next few days... whats with the xine Christmas tree thing???)

---

### Post by darkaudit on 2005-04-13
I grabbed mplayer-plugin from the cerkinfo repository. Works much better than the mozilla-mplayer one. Just watch out for dependency issues with his repo. He's redone a lot of the codec packages, and his mplayer isn't working too well right now.

---

### Post by Cyclonis on 2005-04-14
thanx, that did the trick

lol

---

