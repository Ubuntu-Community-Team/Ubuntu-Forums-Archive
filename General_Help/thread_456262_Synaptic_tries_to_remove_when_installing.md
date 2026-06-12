---
title: "Synaptic tries to remove when installing?"
date: 2007-05-27
forum: General Help
---

### Post by cd-r80 on 2007-05-27
When I try install mono with synaptic I got info that many packages are to be removed kb3 etc. Why? How to fix this?

---

### Post by bmartin on 2007-05-27
Let it uninstall K3B; go ahead and install Mono. Then install K3B again. I don't see why you can't have them both installed at the same time. It's probably APT just being its normal stupid self.

---

### Post by cd-r80 on 2007-05-29
It is just that it wants to remove 50 other packages & install new kernel images which I don't want.

---

### Post by bmartin on 2007-05-29
Sounds like you have dependency problems. I recommend the following:

1. Open up a terminal.
2. Enter **sudo aptitude install mono** and your password when prompted.

When you're prompted to add/remove packages, Aptitude will display a list of packages that it intends to add/remove. If it's not what you want to do, select no. Aptitude will often give you a series of options (if you hit no, it'll suggest something else).

Also, I found this command suggested on [this page]("http://ubuntuforums.org/archive/index.php/t-7758.html"):
```
aptitude install mono gtk-sharp sqlite libxss-dev libmono-dev libdbus-cil libgecko-cil
```

I hope that one of those works. I tried installed both Mono and K3B on my computer (Feisty); nothing was marked for removal.

I doubt this is the case, but perhaps Mono requires a different kernel than the one you're using. That might explain the packages.

---

