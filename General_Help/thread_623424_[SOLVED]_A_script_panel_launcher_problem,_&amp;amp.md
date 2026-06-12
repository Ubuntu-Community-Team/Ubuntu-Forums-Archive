---
title: "[SOLVED] A script panel launcher problem, &amp;amp; an update annoyance"
date: 2007-11-25
forum: General Help
---

### Post by YAOMTC on 2007-11-25
**EDIT:** This first problem has been resolved! Now for the second one.
[COLOR="Gray"]There's two things I need to bring up. First, while this script works from the terminal, it doesn't work when I link an application launcher in the panel to it. Anybody know why this is? This script is supposed to mute and unmute the headphones, but when run from a launcher, it only works for unmuting.[/COLOR]
```
#\bin\bash
       aumix -Wq |grep -q 100
        if [ $? == 0 ]; then
          aumix -W mute
       else
          aumix -W 100
        fi

```

[COLOR="Gray"]Second, the latest package of aumix doesn't quite work right with Ubuntu, it seems. Is there a way that I can get the update manager to always ignore the "update", without ignoring everything in the "distribution updates" category?[/COLOR]

**EDIT(2):** Now they're both solved! Look at the last post on this page.

---

### Post by YAOMTC on 2007-11-26
.

---

### Post by YAOMTC on 2007-11-28
.

---

### Post by YAOMTC on 2007-11-28
.

---

### Post by YAOMTC on 2007-11-28
.

---

### Post by YAOMTC on 2007-11-29
.

---

### Post by geirha on 2007-11-29
#\bin\bash should be ```
#!/bin/bash
```

Any reason why you're not using amixer instead? (I've never used aumix and have no idea how it works)```
man amixer
```

---

### Post by YAOMTC on 2007-12-02
Script panel launcher problem fixed. Thanks! :D

---

### Post by YAOMTC on 2007-12-02
Now for the update thing. Hopefully somebody out there has something to say about that.

---

### Post by zvacet on 2007-12-03
I´m not sure that I understand you but if you want not to upgrade some package go to **synaptic>find that package>mark it>package>lock version**

---

### Post by YAOMTC on 2007-12-03
That was it exactly. Thanks a lot!  [img]http://img.photobucket.com/albums/v256/attack_mayo/little/thumbsup.png[/img]

---

