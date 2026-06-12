---
title: "Can't Uninstall Program"
date: 2007-08-02
forum: General Help
---

### Post by CheeseQueen452 on 2007-08-02
I installed GYachE(messenger) some time ago, but I didn't like it so I don't use it. I want to uninstall it, but it's not even listed in "add/remove" or synaptic. How do I get rid of it? HELP!!!

---

### Post by greybit on 2007-08-02
Do you mean gyachi?

You should be able to remove it with:

```

sudo apt-get remove --purge gyachi

```

If it is gyache, try:

```

sudo apt-get remove --purge gyache

```

---

### Post by Hospadar on 2007-08-02
How did you install it? 
if you built it yourself (like with ./configure, make, make install) you will have go to the folder where the source was (the folder where you did ./configure, make, make install) and try a ```
sudo make uninstall
```  It may be the case that the creator of the software didn't put an uninstall script in their makefile, in which case you are sort of out of luck, and you can try manually uninstalling it by hunting down the files it installed and manually deleting them, I would guess they are in /usr/bin and /usr/lib, but running ```
sudo make install
``` and paying attention to the output will show you exactly where the files went.

If you deleted the folder where the source was from where you installed it, try re-downloading the source and do ```
./configure
make
sudo make uninstall
```
in the folder where you unpacked the code.

If you installed it from a package that you manually downloaded and installed (like a .deb file) you may be able to use dpkg to remove it.

---

### Post by CheeseQueen452 on 2007-08-02
Thanx!!

> **greybit said:**
> Do you mean gyachi?

You should be able to remove it with:

Code:
sudo apt-get remove --purge gyachi

If it is gyache, try:

Code:
sudo apt-get remove --purge gyache

---

