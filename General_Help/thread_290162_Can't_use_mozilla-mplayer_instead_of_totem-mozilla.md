---
title: "Can't use mozilla-mplayer instead of totem-mozilla? -edgy"
date: 2006-10-31
forum: General Help
---

### Post by nismoskys on 2006-10-31
i'm trying to watch videos with the totem-mozilla plugin but it just gives me an error "totem could not play..."

i have mozilla-mplayer installed, but how can i get firefox to use mplayer instead of totem?

i tried removing the totem-mozilla package but then it tries to remove ubuntu-desktop as well.```
sudo apt-get remove totem-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntu-desktop totem-mozilla
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  totem-mozilla ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 106kB disk space will be freed.
Do you want to continue [Y/n]? 
```

i also tried running sudo dpkg -r totem-mozilla but it just gives me errors ```
sudo dpkg -r totem-mozilla
dpkg: dependency problems prevent removal of totem-mozilla:
 ubuntu-desktop depends on totem-mozilla.
dpkg: error processing totem-mozilla (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 totem-mozilla

```

thanks.

---

### Post by reclusivemonkey on 2006-11-01
> **nismoskys said:**
> i'm trying to watch videos with the totem-mozilla plugin but it just gives me an error "totem could not play..."

i have mozilla-mplayer installed, but how can i get firefox to use mplayer instead of totem?


Try searching the forums? This one has been answered many times before.

---

