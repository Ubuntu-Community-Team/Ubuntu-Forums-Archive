---
title: "User rights"
date: 2007-08-10
forum: General Help
---

### Post by SNWBRDR on 2007-08-10
I Played a bit with my user rights in System - Administration - Users and Groups and I think I unchecked the box next to administrator rights.
Now there are any options gone under Administration like Synaptic etc. also Users and Groups, so I can't check that box again to undo it.
I assume there is another way to do this (terminal?), but I don't know how.
Can anybody help me please?

greetings,

SNWBRDR

---

### Post by zvacet on 2007-08-10
In terminal type this

```
sudo adduser username admin
```


replace username with your username of course

---

### Post by bodhi.zazen on 2007-08-10
Boot to recovery mode and follow zvacet's advice, without the sudo

---

