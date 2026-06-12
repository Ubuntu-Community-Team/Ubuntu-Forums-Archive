---
title: "Problems faced by Ubuntu/Linuxmint/Kubuntu on ASUS-X453M Notebook"
date: 2014-12-14
forum: General Help
---

### Post by Arif_Shakil on 2014-12-14
Hello, I recently bought ASUS-X453M (NOT X453MA) Notebook and then I tried installing Ubuntu/Linuxmint/Kubuntu. But sadly I am facing various problems with all the versions. I am listing them below:
[LIST=1]
[*]It freezes on the splash screen when loading Ubuntu. But, I can turn Ubuntu on through recovery mode. But when I do turn it on through that way, I am unable to restart/shutdown ... It freezes again.
[/LIST]

What I tried so far to fix it via searching all over the internet:
[LIST=1]
[*]Updated BIOS to latest version
[*]edit stuffs in GRUB
[*]Recover
[*]Turn off/on fast boot
[*]I use windows 8.1. Tried various stuffs related to that but i forgot what were those.
[/LIST]

Sooo ... What else can be done ?

---

### Post by carl4926 on 2014-12-14
Run it live and get us

```
lspci -nnk
```

Does this machine have hybrid graphics?

---

### Post by Donnie_Albar on 2015-02-06
> **carl4926 said:**
> Run it live and get us

```
lspci -nnk
```

Does this machine have hybrid graphics?

I do have exactly the same problem

This Laptop only use Intel HD Graphics
here is the spesification :
[http://www.asus.com/Notebooks_Ultrabooks/X453MA/](http://www.asus.com/Notebooks_Ultrabooks/X453MA/)

please help I did so many things like grub stuff, acpi, and sudo poweroff, all of them not work.

---

### Post by carl4926 on 2015-02-06
what version of Ubuntu?

Can you, like the OP do > [COLOR=#000000]I can turn Ubuntu on through recovery mode[/COLOR]

Get the info asked for by me in post #2

---

### Post by Arif_Shakil on 2015-04-13
> **carl4926 said:**
> Run it live and get us

```
lspci -nnk
```

Does this machine have hybrid graphics?


It has a Intel HD 4400 graphics card... i dont know if it is hybrid or not.

---

