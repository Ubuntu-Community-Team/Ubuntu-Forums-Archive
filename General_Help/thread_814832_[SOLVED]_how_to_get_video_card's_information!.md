---
title: "[SOLVED] how to get video card's information!?"
date: 2008-06-01
forum: General Help
---

### Post by crazyfuturamanoob on 2008-06-01
How do I get information about my video card via console?
I need to know it's "name". I already know its VIA but I
need to know is it for example CN700 or KM400. How to get
that info??

---

### Post by sdennie on 2008-06-01
This should help:

```

lspci | grep -i via

```

---

### Post by crazyfuturamanoob on 2008-06-01
> **vor said:**
> This should help:

```

lspci | grep -i via

```
Doesnt work. It says:
> arho@timo-desktop:~$ lspci |*grep -i via
bash: *grep: command not found
arho@timo-desktop:~$
I's using hardy heron.

---

### Post by sdennie on 2008-06-01
Remove the "*".

---

### Post by Kevbert on 2008-06-01
In Terminal just enter:
```
lspci
```
It should be the last item displayed.

---

### Post by crazyfuturamanoob on 2008-06-01
Doesn't work still.
But when I wrote only "lspci" it
said that it is K8M800, along with
a million lines of useless crap.

---

