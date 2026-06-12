---
title: "preventing upgrades of packages"
date: 2006-12-28
forum: General Help
---

### Post by jsvidyad on 2006-12-28
Hi!!!


   Is there any way to prevent just certain packages from being upgraded in ubuntu???

---

### Post by Rui Pais on 2006-12-28
Hi,

on synaptic you could select the package you want to hold, go to menu 'Package' and set 'Lock Version' on.

---

### Post by jsvidyad on 2007-01-03
I tried that. It doesn't seem to work.

---

### Post by 23meg on 2007-01-03
Make sure you hit the "Reload" button after doing it.

---

### Post by Divan Santana on 2007-01-11
still doens't work. apparently there is some bug with this.
Not sure how to fix it...

---

### Post by cmost on 2007-01-11
edit your /etc/apt/preferences file.  You can PIN packages there and set the file to read only thus preventing Synaptic from modifying it further.  For all the information you need on how to do this, including syntax, see here:  [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

Example:
Package: bayonne
Pin: version 1.0.8*
Pin-Priority: 1001

Good luck!

---

### Post by argotnaut on 2007-03-01
When pinning by version numbers, do I need to include the number before the colon? For example, I want to keep xorg from upgrading to 7.2. The package I have installed is listed as

[INDENT]xorg 1:7.1.1ubuntu7[/INDENT]

So does that first '1' need to be included, or do I just start with the 7?

Thanks!

---

