---
title: "Tool to search howtos? (similar to apropos)"
date: 2006-11-27
forum: General Help
---

### Post by olejorgen on 2006-11-27
Hi, I'v installed the "doc-linux-text" package which provides a set of howtos. Problem is that I can't find any usefull way of searching this. I could of course slap together something that searched the HOWTO folder. Problem is that the files are gz'ed and the filenames are pretty short. (not to talk about the speed issue)

I would think there exist some tool similar to "apropos" for howtos? Preferably one that kept a separate index for the head or something.

Thanks

PS: It should be a software forum here (?)

---

### Post by Jussi Kukkonen on 2006-11-27
If you end up grepping the howtos, you should take a look at zgrep...

---

### Post by olejorgen on 2006-11-27
hm.. that wasn't dreadfully slow either. Although 6-7 seconds is a little long (zgrep linux * > /dev/null), but maybe there are ways to optimize this? eg. stop after first match.

---

