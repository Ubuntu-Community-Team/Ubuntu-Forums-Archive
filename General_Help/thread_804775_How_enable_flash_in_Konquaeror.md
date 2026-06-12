---
title: "How enable flash in Konquaeror"
date: 2008-05-23
forum: General Help
---

### Post by Taras on 2008-05-23
Hey guys, i just intalled kubuntu but cant figure out how to enable flash player so i can watch youtube videos, any ideas ?

---

### Post by silvanus2005 on 2008-05-23
what browser are you using? i you install firefox, it will install that plugin  by him himself.

---

### Post by silvanus2005 on 2008-05-23
[http://www.linuxforums.org/forum/debian-linux-help/64255-macromedia-flash-player-konqueror-web-browser.html](http://www.linuxforums.org/forum/debian-linux-help/64255-macromedia-flash-player-konqueror-web-browser.html)
see that link above.

---

### Post by daniel_hh on 2008-06-14
i had a hard time getting konqueror working with flash (kubuntu gutsy), because of the changed version- everytime i tried to install flashplugin-nonfree, i got a md5sum failure notice.

what i did - enable gutsy-updates in adept (important, the standard gutsy repositories don't work), let the system update, then install:
(apt-get purge any old version of both on konsole before that!)
flashplugin-nonfree
konqueror-nsplugins

then:
open konqueror -properties- setup konqueror - plugins

if you have the firefox folder activated there - remove it - find new plugins. then you should have the mozilla folder with the flashplayer.alternate.so file (in the plugin tab)

further (i'm not sure if needed): goto file-associations -applications and for futuresplash and x-shockwave... select "nsplugin" as embedded player.

the most important in my eyes is NOT to use the standard gutsy repository!!!

hope that helps

daniel

---

