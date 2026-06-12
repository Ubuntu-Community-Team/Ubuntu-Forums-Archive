---
title: "Shrink Ubuntu Size on Hard Drive"
date: 2006-12-17
forum: General Help
---

### Post by gblob331 on 2006-12-17
I just checked how much disk space my Ubuntu distro took up, and I found it took up 2.1GB. Are there are packages that I don't need that I can uninstall? I plan to use my computer to only watch videos, surf the web, view pictures, type in TeX and OO Writer, use a computer algebra system, view docs such as pdf, ps, etc.

Also, is there any other way to slim down Ubuntu?

---

### Post by hikaricore on 2006-12-17
You could easily goto the Applications menu and Add/Remove option.
Go through the lists and uncheck items you know for sure you don't need, then hit apply.

This might help a little bit :)

---

### Post by az on 2006-12-17
> **gblob331 said:**
> I just checked how much disk space my Ubuntu distro took up, and I found it took up 2.1GB. Are there are packages that I don't need that I can uninstall? I plan to use my computer to only watch videos, surf the web, view pictures, type in TeX and OO Writer, use a computer algebra system, view docs such as pdf, ps, etc.

Also, is there any other way to slim down Ubuntu?

It's pretty slim already.  Open office would be a candidate to free up some space, but you say you need that.  Maybe use abiword instead?

A lot of the space is used by small bits and shared libraries.  It would be tedious to clean up the small bits (you can remove a few dozen packages using synaptic and still only free up a meg or two) and it would break your system to remove many shared libraries.

---

