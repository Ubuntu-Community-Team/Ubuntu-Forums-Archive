---
title: "Compiling a program missing kde headers"
date: 2007-11-03
forum: General Help
---

### Post by Sir_Sid on 2007-11-03
I am trying to compile Kcometen but during the ./configure I get an error stating that I am missing KDE headers. What are these exactly and what do I need to get first. 

The exact error messeges I get are as follows 

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

---

### Post by tubasoldier on 2007-11-03
in a terminal type
```
sudo apt-get install kdebase-dev
```

That should do it for you.

---

