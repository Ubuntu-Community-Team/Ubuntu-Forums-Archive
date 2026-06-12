---
title: "dpkg was interrupted"
date: 2007-06-14
forum: General Help
---

### Post by EngMAF on 2007-06-14
hello
i am just installed ubuntu this morning 
& i installed easy ubuntu & tried to install beryl but i couldn't
this night when i try to install any program this message appears 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

note;
 I'm a beginner & dont know about commands 

could anyone help me [COLOR="Red"]please  [/COLOR]

---

### Post by NeoLithium on 2007-06-14
Sure! It's easy to fix. Open up a terminal (Applications -> Accessories -> Terminal) and type in the following command:
```
sudo dpkg --configure -a
```
Let it do it's thing, and then you can continue on as normal :)

---

### Post by az on 2007-06-14
Open a terminal and run

sudo dpkg --configure -a

Or run synaptic and tell it to fix broken packages.

---

### Post by EngMAF on 2007-06-14
it work
thnx a lot but why this problem appears
did i do something wrong ? or what

---

### Post by az on 2007-06-14
> **EngMAF said:**
> i
did i do something wrong ? or what

No.  Something may have interrupted the installation process.  It's not your fault, though.

---

