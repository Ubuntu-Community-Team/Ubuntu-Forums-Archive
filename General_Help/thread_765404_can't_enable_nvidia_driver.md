---
title: "can't enable nvidia driver"
date: 2008-04-24
forum: General Help
---

### Post by screaminj3sus on 2008-04-24
Just installed ubuntu 8.04 final on a compaq with a 3200+ 1 gb ram and a PCI-E 7600GT. After installation I went into the drive manager to enable the nvidia driver to get compiz. The box for enable is already checked for "nvidia_new" but it says status " not in use " I tried disabling it, re enabling it and restarting but it does the same thing and I cannot get desktop effects. How can I enable it? It used to be as simple as checking the box in 7.10...

screenshot

[http://img255.imageshack.us/img255/2033/screenshotpz1.png](http://img255.imageshack.us/img255/2033/screenshotpz1.png)

---

### Post by Ub1476 on 2008-04-24
When it's checked, restart X: <Control>+<Alt>+<Backspace>

If that doesn't help, see if all the repos are checked in Software Sources.

---

### Post by Syirrus on 2008-04-24
> **screaminj3sus said:**
> Just installed ubuntu 8.04 final on a compaq with a 3200+ 1 gb ram and a PCI-E 7600GT. After installation I went into the drive manager to enable the nvidia driver to get compiz. The box for enable is already checked for "nvidia_new" but it says status " not in use " I tried disabling it, re enabling it and restarting but it does the same thing and I cannot get desktop effects. How can I enable it? It used to be as simple as checking the box in 7.10...

screenshot

[http://img255.imageshack.us/img255/2033/screenshotpz1.png](http://img255.imageshack.us/img255/2033/screenshotpz1.png)

I'm having the same problem :(

---

### Post by screaminj3sus on 2008-04-24
alright managed to solve it. refreshed the package manager (SLOWLY) and it detected it as being not installed and installed it for me :)

Guess the new release is raping the servers.

---

