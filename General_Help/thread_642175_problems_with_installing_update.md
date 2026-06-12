---
title: "problems with installing update"
date: 2007-12-16
forum: General Help
---

### Post by josh on 2007-12-16
hi guys!

i couldnt find a solution to my problem on the web. it started when i was installing updates then the power went out. i saw a post somewhere of a guy with the same situation but his was fixed when he issued "sudo dpkg --configure -a". when i issue that command this is what i get:

```
Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault (core dumped)
dpkg: subprocess post-installation script returned error exit status 139

```

i did a search for dpkg: subprocess post-installation script returned error exit status 139 but couldnt find anything useful.

i was wondering if its just a problem with the cache, couldnt i just erase it? then start with a fresh empty cache?

need your help guys...

thanks!

---

### Post by cmnorton on 2007-12-16
This link -- [http://ubuntuforums.org/showthread.php?t=505290](http://ubuntuforums.org/showthread.php?t=505290) -- may not solve your problem, but has some interesting info in it.

---

