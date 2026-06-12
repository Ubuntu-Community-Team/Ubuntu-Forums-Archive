---
title: "Need some help finding/installing gkrellm"
date: 2005-08-29
forum: General Help
---

### Post by jsac on 2005-08-29
uggg hope some1 can help with this.... been trying all day to install gkrellm... im all frustrated with it. figured id post here and see if some1 can give me a walkthrough on the installation of it...... i tried usin apt-get umpteen times with no success.... kept gettin an error about not finding the package :(
TIA!!

---

### Post by arnieboy on 2005-08-29
[QUOTE=jsac]uggg hope some1 can help with this.... been trying all day to install gkrellm... im all frustrated with it. figured id post here and see if some1 can give me a walkthrough on the installation of it...... i tried usin apt-get umpteen times with no success.... kept gettin an error about not finding the package :(
TIA!![/QUOTE]
its in universe
do a:
```
sudo apt-get install gkrellm*
```

---

### Post by jsac on 2005-08-29
this is what im gettin when i tried that:


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gkrellm*




:(

---

### Post by arnieboy on 2005-08-29
[QUOTE=jsac]this is what im gettin when i tried that:


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gkrellm*




:([/QUOTE]
please make sure your */etc/apt/sources.list* looks like the one in:
[http://ubuntuguide.org#repositories](http://ubuntuguide.org#repositories)

---

