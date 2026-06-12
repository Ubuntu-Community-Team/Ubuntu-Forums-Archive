---
title: "Need help installing Flash"
date: 2008-01-03
forum: General Help
---

### Post by m0j0j0j0100 on 2008-01-03
I'm fairly new to ubuntu linux, and I'm trying to install flash, following the ubuntu guide wiki instructions for a tar.  The instructions tell me this:

flashplayer.xpt -> ../../flashplugin-nonfree/flashplayer.xpt
libflashplayer.so -> ../../flashplugin-nonfree/libflashplayer.so

I tried copying and pasting those in the terminal, but I dont reckon they're commands.  Can anyone tell me what I need to do?

---

### Post by -Zeus- on 2008-01-03
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by m0j0j0j0100 on 2008-01-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

---

### Post by -Zeus- on 2008-01-03
```
sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

try running those 2 commands

---

### Post by oldb0y on 2008-01-03
If it's a fresh install, you might need to update your repos.

---

### Post by -Zeus- on 2008-01-03
OK, try this then.

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by jespdj on 2008-01-03
Even if you have the right repository enabled it will most likely not work, because of a known bug with Gutsy. Search the forums for "flashplugin" and you'll find lots of threads about the problem.

For example:
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
[http://ubuntuforums.org/showthread.php?t=656428](http://ubuntuforums.org/showthread.php?t=656428)
[http://ubuntuforums.org/showthread.php?t=632322](http://ubuntuforums.org/showthread.php?t=632322)
[http://ubuntuforums.org/showthread.php?t=656047](http://ubuntuforums.org/showthread.php?t=656047)

[size="1"](please search before you post)[/size]

---

