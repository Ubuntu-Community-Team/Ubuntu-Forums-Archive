---
title: "Any alternative to Windows' Deskview program for list items on desktop?"
date: 2008-05-03
forum: General Help
---

### Post by nintennuendo on 2008-05-03
[http://www.howtogeek.com/howto/windows/change-xp-desktop-icons-into-smaller-list-view/](http://www.howtogeek.com/howto/windows/change-xp-desktop-icons-into-smaller-list-view/)

That website has a program that I always use on windows machines when I can.  It lists the items on a desktop as, well, a list, instead of icons.   I'd really love this in ubuntu, either that or a way to get the icon name to cut off after two lines, to conserve space, not displaying the whole long name.

Is there anything like this in ubuntu?

Edit:  also, is there something like this(  [http://technet.microsoft.com/en-us/sysinternals/bb897557.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897557.aspx) )  that embeds information onto the desktop?  Like version, hard drive space, IP address, stuff like that?

---

### Post by z0mbie on 2008-05-03
For the latter what you're looking for is conky:

```
sudo aptitude install conky
```

Then there are tons of [conky scripts]("http://ubuntuforums.org/showthread.php?t=281865") to choose from. The configuration file for conky is stored in **~/.conkyrc**

Here are some [screenshots]("http://conky.sourceforge.net/screenshots.html").

---

### Post by nintennuendo on 2008-05-05
Thanks.

Otherwise, I'm stuck with Ubuntu's fat icon names?

---

