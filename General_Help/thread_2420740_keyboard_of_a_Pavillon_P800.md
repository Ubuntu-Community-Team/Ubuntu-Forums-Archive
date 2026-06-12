---
title: "keyboard of a Pavillon P800"
date: 2019-06-10
forum: General Help
---

### Post by catonano on 2019-06-10
it doesn' t work

it only reacts with the function keys and the ctrl, fn and alt keys

but with no other keys

the machine is a Lenovo W 540

on Ubunto 18.04

What can I do ?

Thanks

---

### Post by emre-atakuru08 on 2019-06-10
We try to install driver maybe it can be useful

```

sudo apt-get install xserver-xorg-input-all
```

and don't forget to reboot your system.

---

### Post by catonano on 2019-06-15
thank you

I tried but it didn' t help

I even tried a non wayland session

doesn anything else come to your mind ?

Thanks

---

### Post by catonano on 2019-06-15
it might be helpful knowing that a Logitech wireless keybord is working like a charm

---

### Post by emre-atakuru08 on 2019-06-16
Okay &#305; searched something about that so &#305; found like that;

Firstly you have to learn kernel with uname -a 
we suppose your kernel version 4.19.0-kali1-amd64 (&#305; am using kali but doesn't matter because both os using debian)
and you have to check this directory;
```

/lib/modules/4.19.0-kali1-amd64/kernel/drivers/input/keyboard

```
please share output :)

---

