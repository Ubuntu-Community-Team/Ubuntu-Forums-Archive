---
title: "Can't remove old kernel"
date: 2021-11-03
forum: General Help
---

### Post by ugjka on 2021-11-03
I think I  have the same problem on my VPS instance; got the new kernel but the autoremove isn't removing the old one

---

### Post by QIII on 2021-11-03
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2468579").

Please do not hijack the threads of other users to insinuate your issues into their request for help.  Yours was not an attempt to help the OP, but a question of your own.

---

### Post by VMC on 2021-11-03
Dont know what VPS is, but try this:```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```
If your satisfied with the results remove the "---dry-run", then run again.

---

