---
title: "amarok and external browser"
date: 2005-08-03
forum: General Help
---

### Post by foxy123 on 2005-08-03
I wonder if anyone like me also uses amarok as a main audio player without KDE? The problem is that if I click on Add/Search Lyrics or MusicBrainz buttons, I've got 
```
Could not launch the browser
Could not find service 'kfmclient
``` 
Basically 'kfmclient' is a part of konqueror, which I do not want to install, since it tails a lot of dependencies (almost a whole KDE). I wonder if there is a walkaround to open external web browsers from amarok without installing konqueror?

I asked at amarok forum and even in irc but have not got any solution... :(

---

### Post by maubp on 2005-09-27
I was just looking for an answer to the exact same problem.

I guess [this was you](http://amarok.kde.org/component/option,com_simpleboard/Itemid,/func,view/catid,8/id,6926/).  Another [related post](http://amarok.kde.org/component/option,com_simpleboard/Itemid,/func,view/catid,9/id,7899/).

It sounds like Amarok will try to ask KDE what the default browser is, and failing that its hardcoded to assume its konqueror.

Anyone?

---

### Post by maubp on 2005-09-27
Found a [ubuntu bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=10448) filed for this, and its [KDE brother](http://bugs.kde.org/show_bug.cgi?id=106015).

---

