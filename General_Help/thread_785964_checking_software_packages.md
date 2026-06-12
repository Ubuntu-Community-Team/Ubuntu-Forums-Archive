---
title: "checking software packages"
date: 2008-05-07
forum: General Help
---

### Post by gishaust on 2008-05-07
hi everyone


I have over the last six months beening doing alot of sudo apt-get install of different software packages. What i want to know is from the commandline how do I find out what i have installed, how do remove the things i don't want and is there any other things I should do  after removing some of the packages?

gishaust

---

### Post by Monicker on 2008-05-07
Installed:
```
dpkg --get-selections
```

Remove
```
sudo dpkg -r packagename or sudo apt-get remove packagename
```

Its good to run these once in a while

```
sudo apt-get autoclean or sudo apt-get clean
```

---

### Post by gishaust on 2008-05-07
thanks for your help

I have remove a couple of programs and it work fine

but I remove iceape but it is still in the xfce gui and if click on it starts up.
so I tried to sudo apt-get remove iceape agian and said that it was not installed.
Does anyone know what i can do next?

---

