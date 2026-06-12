---
title: "Major Problem"
date: 2007-04-06
forum: General Help
---

### Post by HessiaNerd on 2007-04-06
Well I guess there's a first for everything.  This is the first time Linux has taken a major dump on me.  Admittedly I haven't been using it for very long but this was pretty nasty.

I got into a login loop after a random crash, where every time I would try to log-in It would bring me back to the same login screen...  I tried some random sudo dpkg-reconfigure gnome-stuff as well as sudo aptitude clean... but no dice... finally I just did a sudo aptitude purge beryl and that did it....


I will try cleaning up and reinstalling beryl, 

has anyone else had this problem????

any advice?

Ive had some random little bugs lately, I just kinda ignored... like the clock stopping, and the task bar not showing the windows open....  and these would happen with metacity as well as beryl...  I just wrote them off as annoyances, but now....

any advice?

I will definitely do a clean install once fiesty drops but this has me a bit worried...  advice as to what to do to prepare for a reinstall would be helpful as well...

---

### Post by dbbolton on 2007-04-06
you might try ```
sudo dpkg-reconfigure xserver-xorg
```.

---

