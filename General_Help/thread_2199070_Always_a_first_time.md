---
title: "Always a first time"
date: 2014-01-12
forum: General Help
---

### Post by mayagrafix on 2014-01-12
I turned off System settings<<Security&Privacy<<<files&applications<<<<off
I erased clear usage date for all time

now desktop refuses to load

---

### Post by grier-devon on 2014-01-12
get to a command line usually through ctrl+alt+F1 and then type
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
```

EDIT: I also forgot to mention that once your done retart the machine
> sudo reboot

---

