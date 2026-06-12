---
title: "[SOLVED] Yet another GPKG error thread."
date: 2007-09-19
forum: General Help
---

### Post by Nackma on 2007-09-19
I've been browsing many similar threads trying to get an answer without directly asking, but I am at a loss.  When I try anything (Install / Uninstall / etc.) with the add/remove... interface I get the following:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I also get this whenever I attempt to use the Synaptic Package manager.

Also
```
sudo apt-get update
AND
sudo apt-get upgrade
AND
sudo apt-get install -f
```
give me the same thing sans the second line.  They give this error before and after I attempt 'sudo dpkg --configure -a', which fails in it's own special way:

```
nackma@Kitsune-Kees:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `
nackma@Kitsune-Kees:~$ 
```

Does anyone know how to debug this one?

---

### Post by Nackma on 2007-09-22
I figured it out.  It seems that the above parse error can be taken care of buy selecting that directory and deleting the contents.  It's the cache for updates and it rebuilds itself if you update with apt-get update or by running 'Applications > Add/Remove...  Commands found below:
```
cd /var/lib/dpkg/updates/
sudo rm *

```

as always, be careful using the sudo rm * command, it kills everything in the directory.

---

