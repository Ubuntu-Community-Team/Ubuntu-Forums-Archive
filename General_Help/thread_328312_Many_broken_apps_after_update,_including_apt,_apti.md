---
title: "Many broken apps after update, including apt, aptitude..."
date: 2006-12-30
forum: General Help
---

### Post by vazzeroni on 2006-12-30
So after a large set of updates recently, this Thinkpad R60e that I'm working on no longer is able to run many apps, most of them seemingly related to apt. I got a crash report relating to python (the little bomb), and sent several crash reports... then I tried to do an apt-get update, which worked, and then apt-get dist-upgrade, which results in a segfault. Trying to run aptitude also results in a segfault, as does trying to run update-manager or synaptic. This also appears to be true on another laptop I'm working on, an X31. Both are running fairly default installs of edgy.

I just figured it out... by removing universe and multiverse repositories from /etc/apt/sources.list, this no longer happens. I don't know why this would suddenly occur, as this has always worked before. Any ideas?

---

### Post by vazzeroni on 2006-12-30
Actually, it looks like it was the apt-src lines, or maybe the multiverse and universe repositories being on the same line as main and restricted, instead of on their own lines. I guess I changed too many things at once to be sure, but in case anybody else runs into this, perhaps this will help them.

---

### Post by Ramses de Norre on 2006-12-30
A wrong formatted sources.list file really shouldn't cause segfaults... But leave it as it is when it's working now ;)

---

