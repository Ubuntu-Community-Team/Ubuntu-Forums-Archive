---
title: "Ubuntu doesn't start after removing few ordinary packets"
date: 2013-06-29
forum: General Help
---

### Post by dowoshek on 2013-06-29
Hello,
I need help with my Xubuntu (but it affects Ubuntu as well, because I've noticed it before too). I've followed one instruction found in the article:
[http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/](http://*********************.com/2012/09/28/to-do-list-after-installing-ubuntu-13-04-aka-raring-ringtail-operating-system/)

And the result is that I when I try to boot Ubuntu it shows nothing but the black screen or "Loading Initial Ram Disk" when I try rescue mode. The command I've followed was actually removing some useless packets:
```
xubuntu-desktop oneconf software-center python3-oneconf python-oneconf oneconf-common ubuntu-standard python-zeitgeist zeitgeist-datahub zeitgeist rsync zeitgeist-core popularity-contest catfish
```

I already chrooted to the system and reinstalled them, but still the system can't start. Any help would be appreciated as I already spent some time for configuring my system and wouldn't like to reinstall it.

---

