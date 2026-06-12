---
title: "Can't boot to windows"
date: 2007-11-24
forum: General Help
---

### Post by Zenharu on 2007-11-24
I first installed Kubuntu 7.10 Gutsy Gibbon on my PC, then decided to dual boot with windows, and when I installed windows I couldn't boot into Kubuntu anymore, so I reinstalled grub, and now when I go into grub to try and boot into windows instead of Kubuntu, Windows doesn't show up on the OS list.

---

### Post by eggdeng on 2007-11-24
Basically you did things the wrong way round. The The simplest thing to do is start over, first W*nd*ws, then Ubuntu. That way grub will recognise the W*nd*ws install and give you the option to boot into either OS.

---

### Post by Zenharu on 2007-11-24
> **eggdeng said:**
> Basically you did things the wrong way round. The The simplest thing to do is start over, first W*nd*ws, then Ubuntu. That way grub will recognise the W*nd*ws install and give you the option to boot into either OS.

Any way to fix this problem without formatting?

---

### Post by Bablefish on 2007-11-24
If you have to start all over again you should look in to [https://launchpad.net/lubi](https://launchpad.net/lubi)

---

### Post by meierfra on 2007-11-24
No reason to reinstall. You just need to  edit one file.  I need some information  and then I will be able to tell you exactly what to do.

Open a terminal (Applications->Accessories->Terminal) and type

```
sudo fdisk -l
```
 
and 

```
cat /boot/grub/menu.lst
```

(all "l" are lowercase L, not the number one)

Copy the content of the terminal and post it here.

---

