---
title: "hud-service creates high load when Firefox is used"
date: 2012-11-15
forum: General Help
---

### Post by temmokan on 2012-11-15
Hello,

Ubunru: 12.04, latest updates installed.

Several days ago I noticed hud-service creates high CPU load (for several seconds) when I am using Firefox (I use Xmarks and keep quite a number of bookmarks).

I followed an advise and took the following steps:
- in Privacy (Files tab), forbade recording Website activity
- in Privacy (Applications tab) added Firefox to the applications whose activity isn't logged

However, after the Firefox has upgraded to the latest versions, the high load spikes returned. As a result, it's extremely uncomfortable trying to use Firefox for real.

Could someone suggest something to solve the problem? Purging the bookmarks list isn't an acceptable solution.

Thanks.

---

### Post by radiobuzzer on 2012-11-22
Hi, I am not sure that universal ubuntu logging creates the problem. I would rather think it has to do with hud trying to index your bookmarks. The only thing I am sure that would solve the problem is disabling globalmenu addon from the firefox extensions menu

This has already been identified as a bug, so better look there 
[https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174]("https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174")

---

### Post by temmokan on 2012-12-19
> **radiobuzzer said:**
> Hi, I am not sure that universal ubuntu logging creates the problem. I would rather think it has to do with hud trying to index your bookmarks. The only thing I am sure that would solve the problem is disabling globalmenu addon from the firefox extensions menu[]("https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174")

Thanks for the reference to bug tracker.

However, I do not use the mentioned add-on, even though I use quite a lot of bookmarks.

---

### Post by halfbeing on 2013-12-03
I seem to have solved the problem by ditching Unity and going back to XFCE. It's drastic I know, but Unity is such an appalling piece of bloatware that I had no choice. Not only is Firefox now working properly, but I also no longer find that my machine becomes unusable for periods of 5-10 minutes several times a day because of insane disk thrashing. In any case I found the unity panel so slow and unresponsive that it simply wasn't worth using, so I've lost nothing really.

---

### Post by oldos2er on 2013-12-04
Old thread closed.

---

