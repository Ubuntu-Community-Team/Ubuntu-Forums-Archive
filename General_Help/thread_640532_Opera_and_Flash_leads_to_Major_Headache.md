---
title: "Opera and Flash leads to Major Headache"
date: 2007-12-14
forum: General Help
---

### Post by Aielyn on 2007-12-14
As most of you no doubt know already, Adobe recently released their newest version of Flash.

Annoyingly, this new version was incompatible with the most recent stable release of Opera, my browser of choice. In my attempts to get everything working again, I upgraded to Opera's normal beta version, Opera 9.50 beta 1.

Thing is, I discovered that beta **2** was necessary for the Flash to work. This caused a bit of a headache, because beta 2 for Ubuntu is not on Opera's site. So, I did a little bit of looking around, and found opera-static on their site, which was beta 2, but more generally debian-based (rather than Ubuntu-specific). Result - STILL no flash, and visually it looked odd (the font of the menus looked strange, for instance). Headache growing.

And so, I decided I would try reverting back to Opera 9.24 and get hold of the earlier version of Flash again. I removed flashplugin-nonfree, then installed Opera 9.24 through synaptic (which automatically removed beta 2). Now, Opera won't even load up - it shows up in System Monitor, but nothing appears. Using Firefox to download 9.24 directly from Opera.com didn't help, either - still nothing. If I run opera from a terminal, I get this:

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
```

Note that this is before I've even bothered trying to get the older version of flash. Also note that switching to Firefox until Opera 9.5 is released properly isn't an option.

Also, note that the fix that daradib keeps posting in threads (such as [here](http://ubuntuforums.org/showpost.php?p=3916097&postcount=4)) did not work, nor did the fixes [here](http://ubuntuforums.org/showthread.php?t=636397). I have Ubuntu Gutsy, 32 bit, and I can't think of anything else that I need to mention.

Please help.

---

### Post by zvacet on 2007-12-14
It looks like you can not downgrade from 9.5 to 9.24 as thay say [here](http://www.opera.com/docs/changelogs/linux/950b1/).I use 9.5b and I don´t have any troubles with flash,so I´m not right person to answer your question.Try Opera forums,because you will get answer faster from them.

---

### Post by Aielyn on 2007-12-14
> **zvacet said:**
> It looks like you can not downgrade from 9.5 to 9.24 as thay say [here](http://www.opera.com/docs/changelogs/linux/950b1/).I use 9.5b and I don´t have any troubles with flash,so I´m not right person to answer your question.Try Opera forums,because you will get answer faster from them.

Thanks. Although I would have thought that applied only to the mail component of opera, and I was able to stop a warning from popping up when running opera from a terminal that would say that the mail system was incompatible, just by deleting the directory /home/<user>/.opera/mail, so I thought I had already addressed that problem.

Just now, I decided to try upgrading back to 9.50 beta 1, and I could at least get opera running, and it seems to at least work with the older flash version, so I have a functional system (although I think that javascript is faulty in this one, which makes 9.50 beta 1 annoying to use).

I just might try the opera forums, if nobody here can give me an answer.

---

