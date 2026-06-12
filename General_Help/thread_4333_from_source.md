---
title: "from source"
date: 2004-11-14
forum: General Help
---

### Post by FISH on 2004-11-14
I want to compile software from source and I want it to be for my architecture. How do I change it from i486?

---

### Post by Razvan on 2004-11-14
usually, you do ./configure && make && make install, right?

the adjustments all happen with ./configure ... some good configure scripts automatically look your architecture up and use it, others want you to tell them

its allways a good idea to open a configure script in gedit and skim through ;-) most of them   are well commented and tell you what options you can give then

good luck

---

