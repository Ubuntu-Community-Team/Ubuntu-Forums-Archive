---
title: "HBO Nordic stopped working"
date: 2016-09-01
forum: General Help
---

### Post by intexdk on 2016-09-01
I'm using Ubuntu 16.04 on a Lenovo ideapad s510p Touch. Until a couple of days ago, my HBO Nordic was working just fine on Firefox but now it won't seem to function, at all. When I click something I wanna watch, it gets to this loading screen and then never moves on from there.
[ATTACH=CONFIG]270949[/ATTACH]

I've tried a bunch of different stuff. Installing different packages and all kinds of stuff. I can't really remember, by now, the things that I've tried.
I've tried install libhal1-flash package, ubuntu restricted extras, I've tried installing pipelight and activating the Windows-version of Flash. Tried installing libvdpau packages, as well. I know that this question has been asked before, in various versions, but if somebody has some new light to cast on this problem, feel free to shoot... =)

Si

---

### Post by intexdk on 2016-09-01
By the way, I've also tried in Chrome. Exact same response.

---

### Post by intexdk on 2016-09-01
Found it out. Did a bit more research. If anybody encounters the same thing, take a look at this article:
[https://www.maketecheasier.com/watch-hbo-now-ubuntu/](https://www.maketecheasier.com/watch-hbo-now-ubuntu/)

What worked for me that I hadn't seen before was the "enable-silverlight" line and subsequently the building of mozilla-plugins. Initially got an error on the silverlight plugin in Firefox plugin manager, but "pipelight-plugin --update" took care of that for me.

Have a good one.
Si

---

