---
title: "Error: Dependency is not satisfiable:libwxbase2.8-0"
date: 2007-08-28
forum: General Help
---

### Post by bootsbradford on 2007-08-28
I am trying to install a .deb package ([http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download](http://www.rockbox.org/twiki/bin/view/Main/RockboxUtility#Download)) but am currently getting an error message.

It says: "Error: Dependency is not satisfiable:libwxbase2.8-0"

Can anyone tell me what I need to do to solve this?

---

### Post by rsambuca on 2007-08-28
That is strange since it is in the standard ubuntu Feisty repositories.  Try installing it first, using the Synaptic Package Manager.

---

### Post by bootsbradford on 2007-08-28
> **rsambuca said:**
> That is strange since it is in the standard ubuntu Feisty repositories.  Try installing it first, using the Synaptic Package Manager.

I had thought the same but this made no difference whatsoever!

---

### Post by rsambuca on 2007-08-28
Did you try re-installing the libwxbase and then trying the .deb package again?

---

### Post by bootsbradford on 2007-08-28
Yes, I did this but again no difference...

---

### Post by Seisen on 2007-08-28
Did you happen to follow these directions first?

```
echo "deb http://apt.tt-solutions.com/debian/ etch main" >> /etc/apt/sources.list
apt-get update
apt-get install libwxgtk2.8-0


```

---

### Post by bootsbradford on 2007-08-28
I didn't because I'd assumed from reading the info that they applied just to Debian and not Ubuntu.

The first didn't work but the third line solved the problem, so thanks for the prompt!

---

### Post by rsambuca on 2007-08-28
Man!  I guess I wrongly assumed you followed the instructions on the page that you provided!  Did it not occur to you to check the instructions after you kept getting errors?:confused:

---

### Post by apetresc on 2007-08-28
> **bootsbradford said:**
> I didn't because I'd assumed from reading the info that they applied just to Debian and not Ubuntu.
Actually, it did work, it just doesn't do what you probably thought it did. It writes a line to the file /etc/apt/sources.list . It doesn't output anything to the prompt, though, so you probably thought it did nothing.

---

