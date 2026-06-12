---
title: "Sync podcasts with a shell script?"
date: 2006-12-04
forum: General Help
---

### Post by Brunellus on 2006-12-04
I'm trying to use rsync to sync podcasts from my home directory (~/Podcasts_ to my iRiver H340 (/media/H300/Podcasts).

Rhythmbox aggregates & downloads the podcasts just fine, but podcasts with shell characters (like : or -- in their titles) don't work in rsync.  

Is there a way to use rsync to synchronize the two directories while stripping away special shell characters?  

I've documented my workaround (a VERY inelegant shell script) on [this blog post](http://ouij.livejournal.com/191715.html).

---

