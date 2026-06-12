---
title: "Getting Avant Window Navigator to work on Hardy"
date: 2008-05-01
forum: General Help
---

### Post by toMeloos on 2008-05-01
I've upgraded Ubuntu from Gutsy to Hardy. AWN worked just fine on Gutsy. Now tried packages from both these repositories:

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

and

```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```

Both result in the same error when starting AWN:

```
$ avant-window-navigator
avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new
```

I think I've read just about every thread on this forum, launchpad and found by Google to find a solution but I haven't found one yet. 
Some people suggested it might be related to libawn being moved or something like that. Maybe this combined with the fact that I've upgraded from a Gutsy version (if I'm not mistaken this was a 0.2x branch version of AWN) causes this problem on my system while the packages from these PPA's seem to work for everyone else.

How do I get this solved & working?

Thanks!

---

### Post by acowboydave on 2008-05-02
Hello..you might want to look at this thread here.. [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) ;)

---

### Post by toMeloos on 2008-05-02
Read the entire thread. The solution is not in there. :(

---

### Post by acowboydave on 2008-05-02
Point is that you might have to uninstall AWN and reinstall...

---

### Post by toMeloos on 2008-05-11
I've removed everything using synaptic, then manually searched for old libraries that were left and purged gconf before reinstalling. Didn't help.

---

