---
title: "Curl in Gutsy"
date: 2007-10-21
forum: General Help
---

### Post by woekele on 2007-10-21
Hi,

I just did a clean install of Gutsy (live cd) and noticed that Curl wasn't installed by default? It used to be in Ubunty by default. Is this the case for everybody?

If so, why was it removed? Games like ioquake3 depend on it and now gamers will have to manually install it (via the package manager) and thus give them extra 'work' before they can play a popular linux game, doesn't make sense to me.

---

### Post by woekele on 2007-10-23
Is it just me, or is curl not installed for anybody with gutsy live cd?

---

### Post by movil on 2007-12-20
Same here. 

sudo apt-get install libcurl3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl3 is not available, but is referred to by another package.

Not installed by default (64 bits) I guess I'll have to install it manually.

---

