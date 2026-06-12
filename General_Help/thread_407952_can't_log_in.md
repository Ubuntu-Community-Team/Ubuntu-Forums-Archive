---
title: "can't log in"
date: 2007-04-12
forum: General Help
---

### Post by dbbolton on 2007-04-12
it would appear that the recent kernel update has caused some serious problems. first, it erased my custom GRUB menu which was a minor annoyance. it also broke X. i ran dpkg-reconfigure xserver-xorg, still no X. i ran it again, and reverted to the 'nv' driver, and now X works.

once i get to the GDM login screen, i enter my username and password. next, a black screen comes up with a flashing underscore in the upper left corner for about 4 seconds, then the GDM comes up again. 

i'm not using beryl or anything.

here is ~/.xsession-errors

[http://pastebin.ca/437312](http://pastebin.ca/437312)

---

### Post by barney_1 on 2007-04-12
Make sure that your root partition isn't full.  This could prevent you from logging in.

---

### Post by cmost on 2007-04-12
Why does everyone suggest checking for a full disk whenever this problem occurs?  The more likely problem is that you need to recompile your nvidia or ati driver.  The problem is especially prevalent for those running compiz or beryl.

---

### Post by dbbolton on 2007-04-12
> **barney_1 said:**
> Make sure that your root partition isn't full.  This could prevent you from logging in.

is the root partition the same as "/"

> **cmost said:**
> Why does everyone suggest checking for a full disk whenever this problem occurs?  The more likely problem is that you need to recompile your nvidia or ati driver.  The problem is especially prevalent for those running compiz or beryl.

i'm using the "nv" driver.

---

### Post by taurus on 2007-04-12
Yes, root partition is the same as /.

```
df -h
```

---

### Post by dbbolton on 2007-04-12
i deleted about 2GB of files that i didn't "need," and now i can log in. thanks !

---

### Post by barney_1 on 2007-04-19
Glad it worked out for you.


> **cmost said:**
> Why does everyone suggest checking for a full disk whenever this problem occurs?

I think "everyone" suggests this as the first issue because it's the most common solution to the problem.

---

