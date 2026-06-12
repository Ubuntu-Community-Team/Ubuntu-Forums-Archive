---
title: "Help me install compiz"
date: 2008-01-21
forum: General Help
---

### Post by jeff132413 on 2008-01-21
I am trying to install compiz 0.6.2 which is a tar.gz file but I have no idea how to install it. I know you go into the terminal but what from there?  I am a total noob and I would really appreciate your help. Thanks!

---

### Post by tgm4883 on 2008-01-21
Is the default compiz fusion in gutsy not enough?  It's installed by default

---

### Post by wolfen69 on 2008-01-21
if you are using ubuntu 7.10, you already have compiz. install your video card driver.(restricted drivers manager) then go to system>preferences>appearance>visual effects. you may want to install compizconfig-settings-manager also (in synaptic)

---

### Post by jeff132413 on 2008-01-21
no it is not enough!

---

### Post by ntowakbh on 2008-01-21
> **jeff132413 said:**
> no it is not enough!
...there is no need to shout...

assuming what you have is from source

open terminal

```
sudo apt-get build-dep compiz
```
Get build dependencies.

```
tar -xf compiz* && cd compiz*
```
Extract it and go into the new compiz directory

```
./configure
```
Congigure script

```
make
```
Build it

```
sudo make install
```
Install

```
make clean
```
Clean it up

I haven't installed compiz from source, so I am not sure if this will work exactly.

---

### Post by tgm4883 on 2008-01-21
> **jeff132413 said:**
> no it is not enough!

Wow, the hostility really makes me want to help you.

Perhaps you should try enabling gutsy-backports which has 0.6.2 in it.

---

