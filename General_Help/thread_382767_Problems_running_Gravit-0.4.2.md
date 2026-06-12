---
title: "Problems running Gravit-0.4.2"
date: 2007-03-12
forum: General Help
---

### Post by Commodore Guff on 2007-03-12
Okay, so I've tried to get [Gravit]("http://gravit.slowchop.com/") working for a while now.  It will configure, make, and install just fine, but crash immediately upon being started.
If anyone could try this for themselves, it would be greatly appreciated.

Just hoping I posted this in the right place.

---

### Post by Commodore Guff on 2007-03-12
Sorry if I sound impatient, but can anyone help me?

---

### Post by Commodore Guff on 2007-03-13
> **Commodore Guff said:**
> Sorry if I sound impatient, but can anyone help me?

Please?

---

### Post by redDragonx on 2007-08-05
I am also having the same problem.  I did not receive any errors when building it either.  
Just in case I missed something,  I have attached the terminal out put for building gravit, the output when running gravit and the gravit.cfg file.  any help on this would be greatly appreciated :)

---

### Post by Anexus on 2007-10-24
In main.c change this line in main function

if (init(argc, argv)) {

for this

if (!init(argc, argv)) {

;)

---

