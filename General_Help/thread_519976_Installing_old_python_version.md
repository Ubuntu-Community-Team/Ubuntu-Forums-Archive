---
title: "Installing old python version"
date: 2007-08-07
forum: General Help
---

### Post by olejorgen on 2007-08-07
Is it possible to install an python2.2 without building from source?

I guess no since I can't find it in the repos, but I though I'd check. Need it to run pyplayer for helix realplayer.

---

### Post by apetresc on 2007-08-07
If it's not in the Ubuntu repository, your best bet is to grab a Debian package from here: [http://packages.debian.org/oldstable/python/python2.2](http://packages.debian.org/oldstable/python/python2.2)

However, I'm not sure I recommend doing this. It may mess up and conflict with your existing Python installations. Then again, it may not.

May I ask, what happens if you try to run pyplayer with a more recent version of Python? The best solution may be to get it working with 2.4 or 2.5. It shouldn't be too hard; Python is pretty good at backwards compatibility (well, at least until 3.0 is ready :))

---

### Post by olejorgen on 2007-08-08
```
__main__:1: RuntimeWarning: Python C API version mismatch for module hxplay: This Python has API version 1013, module hxplay has version 1011.
```
Now that I look again, this is only a warning.

Thanks for the reply. I also figured installing a unofficial deb could break my system so I compiled and installed to my home folder. This worked, but it seems pyplay does not like the newest version of realplay :(
(And for some reson readline support was missing)

I tried buiding pyplay, but got tons of errors. ([https://helixcommunity.org/projects/pyplayer/](https://helixcommunity.org/projects/pyplayer/))

I'd wish mplayer would get perfect real support, then I could just use that in slave mode.

I'm trying to hack together video bookmark support (for lecture reviews), and most lectures are in realvideo.

---

