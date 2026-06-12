---
title: "qBitTorrent crashes while checking existing files"
date: 2006-12-07
forum: General Help
---

### Post by Kimm on 2006-12-07
I downloaded qBitTorrent a few days ago, thinking it would better than using uTorrent through wine. (light, with DHT is a must...)

Problem is that qBitTorrent crashes when checking the files of my current downloads (when adding a partially downloaded torrent). It usualy goes up to somewhere around 5% and then crashes.

Has anyone else got this problem? if so... is there a way to fix it?
I'm using the precompiled packages for Edgy found on their site, but I'm thinking about compiling it myself to see if that'll make it work better.

---

### Post by Kimm on 2006-12-07
After a closer look it seems to be a libtorrent issue, since the same thing happens to Deluge.


I'll file a buggreport and check SVN...

---

### Post by Kimm on 2006-12-08
No luck... CVS wount compile and compiling it myself makes no difference.

I've filed a bug report...

Can anyone help me wit this?

---

