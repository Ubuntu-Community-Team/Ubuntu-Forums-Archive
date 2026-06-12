---
title: "Playing .rm files in linux"
date: 2006-12-20
forum: General Help
---

### Post by Kittie Rose on 2006-12-20
I recently downloaded Linux realplayer, but some .rms I have just downloaded say that they are encoded with an older unsupported audiocodec. What can I do? I can't find any big audio codecs or good RM players for Linux.

---

### Post by zippy028 on 2006-12-20
I dson't know if this will help but the Program Automatix install many many codecs maybe you try that if you haven't already. [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

---

### Post by NT4usB on 2006-12-20
mplayer with all the codecs (w32...?) will play rm (and, anything else I throw at it!)
Stuff that my XP and 2K boxes won't even touch.

---

### Post by Kittie Rose on 2006-12-21
I can't compile Mplayer and the deb is offline. Can someone send me the deb and codecs?

I finally got the deb, now it says it can't install because of a dependancy on libfaac0... ???

---

### Post by hikaricore on 2006-12-21
you could add the new PLF repo to your sources.list

> ## PLF
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free


NOTE: If you're using dapper instead of edgy, just replace ^ the edgy's with dapper.

It has the nonfree codecs and probably mplayer as well... tho mplayer should be in the default repos for ubuntu if I'm not mistaken.

---

### Post by Azakus on 2006-12-21
YES! I had been wondering where the new PLF repos where. Thanks!

---

