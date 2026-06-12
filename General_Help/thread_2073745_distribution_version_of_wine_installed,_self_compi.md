---
title: "distribution version of wine installed, self compiled one not working"
date: 2012-10-20
forum: General Help
---

### Post by Kasper Janssens on 2012-10-20
Hello,

I installed the distribution version of wine, through aptitude, but I wanted to have the latest commits to try a game which doesn't work yet with the 1.4 version in the distribution's repos. So I cloned, compiled and installed, in /usr/local/bin, and now it's complaining about another version of the wineserver being on the path, which is true, the distribution's one, in /usr/bin. So, I thought I'd remove it with apt-get remove, but that doesn't seem to remove the wine binaries of /usr/bin.

So, my question is, is this normal behaviour for aptitude? If so, how can I remove the wine binaries from /usr/bin short of manuall deleting them from /usr/bin, which I don't think is the appropriate way to go (I could be mistaken of course).

Kasper

---

