---
title: "make: *** [flood_round_robin.lo] Error 1"
date: 2007-09-04
forum: General Help
---

### Post by cancaseiro on 2007-09-04
Hi!

Has someone here some experience of installing Apache's Flood on Ubuntu. I am trying to install it but when I enter command make all it says:

```
/usr/share/apr-1.0/build/libtool --silent --mode=compile gcc    -g -O2  -pipe -Wall -g -O2 -pthread    -DLINUX=2 -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql -I.   -c flood_round_robin.c && touch flood_round_robin.lolibtool: compile: unable to infer tagged configurationlibtool: compile: specify a tag with `--tag'
make: *** [flood_round_robin.lo] Error 1
```

How can I make that error dissapear?

---

### Post by Happy_Man on 2007-09-04
I think it wants you to specify with the flag " - -tag" before the tags you want to use.

---

### Post by cancaseiro on 2007-09-04
> **Happy_Man said:**
> I think it wants you to specify with the flag " - -tag" before the tags you want to use.

How can I do that?

---

### Post by Happy_Man on 2007-09-04
Sorry, ignore my last post. I hadn't read through the command properly. I think that there is a modifier in there that the compiler doesn't recognize.

---

### Post by cancaseiro on 2007-09-04
> **Happy_Man said:**
> Sorry, ignore my last post. I hadn't read through the command properly. I think that there is a modifier in there that the compiler doesn't recognize.

Hmmm... Ok, any ideas what should I try to do?

---

### Post by cancaseiro on 2007-09-05
Or does someone have any better program for testing HTTP load? Preferably  free program. Don't wanna pay for that.

---

