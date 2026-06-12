---
title: "Installation error.  Can't install anything"
date: 2008-01-13
forum: General Help
---

### Post by rutilajw on 2008-01-13
E: The package mplayer-386 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


I really need a solution to this error.  It prevents me from installing anything, be it from synaptic, command line, or add/remove programs.

---

### Post by santaslittlehelper on 2008-01-14
Hi 

Try the following from terminal,
```
sudo apt-get update
```
Post if it gives any errors.

then,
> remove-reinstreq: Remove a package, even if it’s broken and marked to require reinstallation. This may, for example, cause parts  of
the package to remain on the system, which will then be forgotten by dpkg.
```
sudo dpkg -r --force-remove-reinstreq mplayer
```
followed by,
```
sudo apt-get update && sudo apt-get install mplayer
```

Not sure, but hope it does the trick.

---

