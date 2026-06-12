---
title: "how to add to repository?"
date: 2008-06-15
forum: General Help
---

### Post by mikkel13 on 2008-06-15
I just installed ubuntu 8.04 LTS. How do I add the Universe and Multiverse to the repository. Everywhere I look, it looks like I already have added it, but theres is a lot of packs that I can't find...how do I find these packs, fx: compizconfig-settings-manager isn't there, and a lot others.
Pleeaase help...
sorry for my english :(

---

### Post by argail1980 on 2008-06-15
usually you go

system -> administration -> synaptic

and in there

settings -> package repositories

there you can check and uncheck the universe/multiverse repos.

maybe the menues are not called exactly like that, mine are in German..

alternatively you can edit the file /etc/apt/sources.list

---

### Post by mikkel13 on 2008-06-15
never mind... after hours, I found out I forgot to "Reload" the synaptic...
this thread should not had been posted...
anyway thank you for everyones help!! :P
Is it possible to remove a thread?

---

### Post by drs305 on 2008-06-15
Well here, we will make it useful. Besides, you may want to include the medibuntu repositories some day:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by argail1980 on 2008-06-15
just mark it as solved, that will do

---

