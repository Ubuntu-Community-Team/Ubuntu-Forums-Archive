---
title: "Firefox missing icons."
date: 2014-08-10
forum: General Help
---

### Post by mastertonone on 2014-08-10
Not sure of the best terminology to describe the issue so here's a picture to explain. 
[ATTACH=CONFIG]255384[/ATTACH]

Left: Firefox Right: Chromium 

For some reason certain icon's do not display on Firefox. It's just annoying really. Is there a fix for this problem?

---

### Post by FriedMicro on 2014-08-10
Off the top of my head could be a problem with the cache, javascript, or plugins. Try clearing the cache and then disabling your addons to see if it corrects the problem otherwise maybe ```
sudo apt-get update && sudo apt-get upgrade
``` might help.

---

### Post by Dennis N on 2014-08-10
One possible cause of missing icons:

[https://support.mozilla.org/en-US/questions/975612](https://support.mozilla.org/en-US/questions/975612)

---

### Post by vasa1 on 2014-08-11
I used DOM Inspector and I see:
src="https://s.ytimg.com/yts/img/pixel-vfl3z5WfW.gif"
src="https://s.ytimg.com/yts/img/pixel-vfl3z5WfW.gif"
src="https://yt3.ggpht.com/-A4qbfc-FvgM/AAAAAAAAAAI/AAAAAAAAAAA/2Lwqwjaxxlc/s88-c-k-no/photo.jpg"
etc

My suspicion is that OP has some overzealous ad blocker or stylesheet.

---

### Post by mastertonone on 2014-08-13
Thanks for the help. The adblock idea reminded my that I had a user agent add on running. Once I turned it off all was resolved.

---

### Post by vasa1 on 2014-08-13
Interesting that modifying the UA string was responsible. (I know that "mobile" pages can be different than "desktop" pages.)

---

