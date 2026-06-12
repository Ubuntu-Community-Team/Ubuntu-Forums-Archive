---
title: "swiftfox/gdebI screwup"
date: 2008-06-11
forum: General Help
---

### Post by editrix on 2008-06-11
So, because of all my problems with firefox, I installed swiftfox from here:[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm).

Downloaded it to Desktop and then clicked on it. Gdebi had a terrible time with it, and nothing seemed to be happening. So I used the old-fashioned 
sudo dpkg -i swiftfox_3.0pre-4_pentium4.deb

(Note: This is copy/pasted direct from the website and I have a P4) and it looked as if it installed okay.

Except, once it launches, if I go someplace else on my desktop and try to alt-tab back to it, the picture of all running programs on that desktop just freezes. If I'm on another desktop, I can click on the program name in the panel (this is KDE) but again, nothing happens.

Eventually, I get the top of the window frame with the program name and I can ctrl-alt-esc kill it from there, but why can't Kubuntu 8.04 run anything from mozilla?

When I tried to remove swiftfox I got:
```

sudo apt-get remove  swiftfox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package swiftfox is not installed, so not removed

```

Um, it's still there:
```
~$ which swiftfox
/usr/bin/swiftfox
```

Now what do I do?

---

