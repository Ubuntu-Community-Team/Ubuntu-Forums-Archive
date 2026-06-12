---
title: "[SOLVED] Pidgin wont log in ICQ. Version too old ??"
date: 2008-07-01
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-07-01
Pidgin says that the version is too old and it wont login in ICQ.
> The client version you are using is too old. Please upgrade at [http://pidgin.im/](http://pidgin.im/)
...
```
$ pidgin --version
Pidgin 2.4.2
$ 
```
So the version is the newest.
[ATTACH]75951[/ATTACH]

I saw this on 2.4.1 so I installed 2.4.2, but no change.
I downloaded it from [http://GetDeb.net](http://GetDeb.net).

---

### Post by soccerboy on 2008-07-01
[http://ubuntuforums.org/showthread.php?t=846279](http://ubuntuforums.org/showthread.php?t=846279) thread seems to have possible solutions

---

### Post by LinuX-M@n1@k on 2008-07-01
> **soccerboy said:**
> [http://ubuntuforums.org/showthread.php?t=846279](http://ubuntuforums.org/showthread.php?t=846279) thread seems to have possible solutions

You're fast! Thanks, I'll check it ;).

---

### Post by LinuX-M@n1@k on 2008-07-01
How do I apply the patch? In which directory must I be?

edit: sorry, i'll post it in the other thread

---

### Post by soccerboy on 2008-07-01
I'm not quite sure.  Someone else could help with that.

---

### Post by LinuX-M@n1@k on 2008-07-01
```
patch -p0 < pidgin-2.4.2-icq.patch
```

Thanks soccerboy ;).

---

