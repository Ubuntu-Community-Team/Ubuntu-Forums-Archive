---
title: "Installing Nvidia proprietary drivers"
date: 2008-02-07
forum: General Help
---

### Post by AvengingAngel718 on 2008-02-07
Ok, this might sound a little weird, but i missed beryl, so i installed feisty in VirtualBox so i could play with it. everything works fine, but the proprietary drivers aren't installed (when i installed ubuntu originally they were, but not in virtualbox). so i need to figure out how to install them. My graphics card is a Nvidia GeForce 6100.

---

### Post by qpieus on 2008-02-07
My understanding is that virtualbox does not use your real video card - it uses a virtual card. So installing the nvidia driver will have no effect since the virtual pc does not "have" an nvidia card - it has the virtual video card.

---

### Post by mrsteveman1 on 2008-02-07
Virtualized OS can't use the graphics hardware directly, they emulate things a bit, hence the native drivers won't work in a VM.

I would bet you won't even see any reference to the nvidia card in that VM if you do: 

```
sudo lspci
```

Probably just a bunch of standard devices the VM emulates.

---

### Post by qpieus on 2008-02-07
I just checked the card in one of my virtual machines and it says it's a "Virtualbox Graphics Adapter". The host pc has an nvidia card.

---

### Post by AvengingAngel718 on 2008-02-08
Actually that makes a lot of sense....so i wonder what my problem is? When i try to start beryl the screen just goes white and i have to shut down the virtual machine :/

---

### Post by kesman on 2008-02-08
Why are you using beryl in virtual box when you could be using compiz-fusion in the real box?

---

### Post by pointone on 2008-02-08
The problem is that VirtualBox uses it's own very generic video driver that doesn't support 3D acceleration (yet). Check out Xen virtualization if you want 3D acceleration in a VM.

---

### Post by AvengingAngel718 on 2008-02-08
> **kesman said:**
> Why are you using beryl in virtual box when you could be using compiz-fusion in the real box?

basically, because i can. i do use compiz fusion, i just miss a few things in beryl, specifically the ungrab wave effect. and i have enough free time to bother doing it

---

### Post by AvengingAngel718 on 2008-02-08
> **pointone said:**
> The problem is that VirtualBox uses it's own very generic video driver that doesn't support 3D acceleration (yet). Check out Xen virtualization if you want 3D acceleration in a VM.

thanks, i'll check it out

---

