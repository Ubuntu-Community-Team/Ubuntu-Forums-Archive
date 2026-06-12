---
title: "Clear apt archives? [Resolved]"
date: 2007-03-18
forum: General Help
---

### Post by raja on 2007-03-18
I am running out of space on my Ubuntu partition and find that /var/cache/apt/archives is taking up about 2.7 GB. Will it be OK to delete the cached archives ? I have a fast internet connection and can always download the packages again if required.

---

### Post by scxtt on 2007-03-18
yes, that'll be fine ... i think there's even a nice little command to do it too (instead of rm /var/cache/apt/archives/*) ...

edit: **sudo aptitude clean** will do the trick :)

---

### Post by raja on 2007-03-18
Thanks for the hint.
```
sudo apt-get clean
``` did the trick.

---

