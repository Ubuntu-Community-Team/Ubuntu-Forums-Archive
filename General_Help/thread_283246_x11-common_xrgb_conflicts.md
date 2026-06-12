---
title: "x11-common xrgb conflicts"
date: 2006-10-23
forum: General Help
---

### Post by idtt2s on 2006-10-23
I just installed Ubuntu, and I'm trying to get it up to date. When I tried to install kdebase, I got a conflicting set of files, xrgb and x11-common. The dispute is over /etc/X11/rgb.txt, whichever one would be installed last will complain that the file belongs to the other package, so both cannot be installed. However, they are both required packages, so now I basically have a broken system and an apt that won't let me install new packages. What should I do?

---

### Post by Onager on 2006-10-31
I fixed this by doing ```
sudo dpkg --force-overwrite -i /path/to/x11-common/.deb

```
You can get the path to the deb by doing ```
sudo apt-get -f install
```

Didn't seem to break anything, and it seems like a good option until someone smarter than me fixes up the packages ;) 
-Onager

---

