---
title: "Packages are installed but won't work..."
date: 2007-10-15
forum: General Help
---

### Post by WanderingKnight on 2007-10-15
A couple of days ago, I've found a big issue with several packages: Even when they're supposedly installed, they won't run. Whenever I try to run one with a bash command, I get prompted to download it from the apt repositories. When I try to download them, it says I already have them installed. I tried to run the small "fortune" program, which is default in the installation, and won't run. When I try to run the script directly from the shell, I get "Permission denied". I set all of the permissions to max level, but I still get the same result. It's happened with a couple more packages, like with most multiverse packages I've tried. Other packages, though, seem to work just fine (I'm betting it's the officially supported the ones that are working right, but I'm not too sure).

I must clear up that, a couple of days ago, the fortune program was running perfectly.

Any ideas?

EDIT: I just remembered something... I installed Enlightenment a day or two ago. Could this be due to that? I'm not using it, though.

---

### Post by ruibernardo on 2007-10-15
Generally when a problem occurs with APT or dpkg during some installation, you get a message error saying to type:

```
 sudo dpkg-reconfigure -a
```Another one is 
```
 sudo apt-get install -f
```What happens when you try this commands?

---

### Post by Shazaam on 2007-10-16
Another one...
```
sudo dpkg --configure -a
```

---

