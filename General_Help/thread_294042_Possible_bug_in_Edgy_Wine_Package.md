---
title: "Possible bug in Edgy Wine Package"
date: 2006-11-06
forum: General Help
---

### Post by musther on 2006-11-06
Just discovered what I assume must be a bug in the wine package in the Edgy repos.  Just want to get a couple of people to confirm it.

If you've got wine installed go into a terminal and type:

```
wine wcmd
```

If you have something like this:

```
musther@dominus:~$ wine wcmd
WCMD Version 0.9.20

Z:\home\musther>
```

Then this bug doesn't really exist and there's just something odd about my setup.  If however you get something more like this:

```
musther@dominus:~$ wine wcmd
wine: could not load L"C:\\windows\\system32\\wcmd.exe": Module not found
```

Then there is a bug.

The bug is that wcmd.exe.so isn't installed in /usr/lib/wine

I have attached wcmd.exe.so, so to fix the bug, download it and extract it to /usr/lib/wine and all will be fixed.

Good luck

---

### Post by thalt on 2006-12-12
I also ran into this issue. Turns out the edgy wine package is updated as follows:

[https://lists.ubuntu.com/archives/ubuntu-patches/2006-October/003020.html](https://lists.ubuntu.com/archives/ubuntu-patches/2006-October/003020.html)

"WCMD Winelib app renamed to CMD for compatibility."


So doing: wine cmd

gives the desired results.

---

