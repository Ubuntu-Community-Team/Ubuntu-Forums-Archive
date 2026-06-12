---
title: "I think I broke Synaptic"
date: 2007-06-11
forum: General Help
---

### Post by Carbon Tiger on 2007-06-11
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried running the above  line and I got this back "dpkg: requested operation requires superuser privilege"

So er any advice I was trying to install Virtual box and the program just hung up and didn't install all the way.....

I'd be grateful for some aid

---

### Post by reidms on 2007-06-11
You need to be superuser(or root)

Just type
```
sudo dpkg --configure -a
```
and then enter your password

That should do it-

Hope this helps!

---

### Post by Carbon Tiger on 2007-06-11
> **reidms said:**
> You need to be superuser(or root)

Just type
```
sudo dpkg --configure -a
```
and then enter your password

That should do it-

Hope this helps!

Thanks that seems to have fixed part of it.

Now I'm getting this message

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I redownloaded the deb file but that doesn't seem to help

---

### Post by zvacet on 2007-06-11
[http://ubuntuforums.org/showthread.php?t=458098&page=2]("http://ubuntuforums.org/showthread.php?t=458098&page=2")

---

### Post by Carbon Tiger on 2007-06-11
> **zvacet said:**
> [http://ubuntuforums.org/showthread.php?t=458098&page=2]("http://ubuntuforums.org/showthread.php?t=458098&page=2")

Thanks :D

That did it. This is by far the most helpful board I've ever been on.

---

