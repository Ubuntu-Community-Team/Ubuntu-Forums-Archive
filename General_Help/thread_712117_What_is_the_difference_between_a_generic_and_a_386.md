---
title: "What is the difference between a generic and a 386 kernel?"
date: 2008-03-01
forum: General Help
---

### Post by Kingoftherings on 2008-03-01
Currently I'm using a generic kernel, but the 386 kernel is showing up in my grub menu too.

What is the difference?  Which is better?
I have an AMD Opteron 170 (Dual Core) if it makes any difference, and I'm also running Hardy Heron Alpha 5.

---

### Post by Glaxed on 2008-03-01
OPen a terminal and type 
```

uname -r

```
That is the kernel you are using. All others save for 'memtest86' are safe to remove. Id just keep them all, no telling what crap could happen.

As far as 'better' goes, generic is what you want to use unless you have compiled your own kernel.
Generic has all of the kernel mods for your computer and has special Ubuntu support + patches. On an alpha, I would feel much safer using a generic kernel.
'386' isnt enough description for me to help you.
~ glaxed

---

