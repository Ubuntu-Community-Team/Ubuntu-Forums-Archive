---
title: "does anyone have Atlantis working?!"
date: 2008-05-10
forum: General Help
---

### Post by iwallet on 2008-05-10
hi everyone! 
i would really like to have the atlantis plugins on my laptop... 
however.. i cant get it to work.. does it even work on the latest ubuntu?!
lemme know!!! thnks

---

### Post by Enlitend on 2008-05-11
Hi

I just tried out the atlantis and atlantis2 plugins and I can confirm you they work with Hardy Heron. Most of the plugins will work except the cubeaddon.

This might be useful for you
[http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)

:)

---

### Post by iwallet on 2008-05-12
you wanna know something weird.. it says i dont have compiz installed.. but i do.. 
what the hell!!!? :S
im following all the instructions... :(
what should i do?!

---

### Post by Kevbert on 2008-05-12
> **iwallet said:**
> hi everyone! 
i would really like to have the atlantis plugins on my laptop... 
however.. i cant get it to work.. does it even work on the latest ubuntu?!
lemme know!!! thnks

It may be that you need to set the Desktop Cube - Transparent Cube - Opacity During Rotation to something like 25%.  I had the same problem.

---

### Post by graniteburm on 2008-06-24
where can i find the plugins for atlantis

---

### Post by Forlong on 2008-06-24
You need to compile them yourself.
```
sudo apt-get install build-essential compiz-bcop compiz-dev git-core libcairo2-dev libglu1-mesa-dev libtool libxss-dev 
```
```
mkdir $HOME/compiz-plugins && cd $HOME/compiz-plugins
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
```
```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
```
```
cd $HOME/compiz-plugins/atlantis
```
```
make && make install
```
```
cd $HOME/compiz-plugins/atlantis2
```
```
make && make install
```

---

### Post by rico002 on 2008-06-24
> **Forlong said:**
> You need to compile them yourself.
```
sudo apt-get install build-essential compiz-bcop compiz-dev git-core libcairo2-dev libglu1-mesa-dev libtool libxss-dev 
```
```
mkdir $HOME/compiz-plugins && cd $HOME/compiz-plugins
```
```
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
```
```
git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
```
```
cd $HOME/compiz-plugins/atlantis
```
```
make && make install
```
```
cd $HOME/compiz-plugins/atlantis2
```
```
make && make install
```


in that order or just type in the terminal 
git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis

---

### Post by blazercist on 2008-06-25
I have a problem in that I can pull the plugins from git and compile them and install them but when I click to enable them in ccsm the checkmark appears and then goes away after a few seconds.

---

### Post by blazercist on 2008-06-27
shameless bump

---

### Post by iPCGuy on 2009-11-18
lol this is no hope

---

