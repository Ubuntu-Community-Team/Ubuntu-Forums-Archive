---
title: "kernel name"
date: 2012-10-31
forum: General Help
---

### Post by gleble on 2012-10-31
What is the full name of the latest lucid lynx  kernel as shown on the grub screen?

---

### Post by Vaphell on 2012-10-31
2.6.32-44-generic on my box

---

### Post by gleble on 2012-10-31
Come on Easy question

---

### Post by HiImTye on 2012-10-31
that depends on the kernel you have in use. you can find which one you are using by
```
uname -r
```
or if you have aptitude installed
```
aptitude search linux-image~i
```
will show you any kernels you have installed, while
```
sudo apt-get update; aptitude search linux-image
```
will give you a list of all available kernels

---

### Post by Cheesemill on 2012-10-31
You can always check the Ubuntu package website:

[http://packages.ubuntu.com/lucid/linux](http://packages.ubuntu.com/lucid/linux)

---

### Post by gleble on 2012-11-05
The answer will be of  the form linux-image.....
I need this info to boot withour a grub screen

---

### Post by gleble on 2012-11-05
Can someone please just look at their grub screen 
and tell me the names of the kernels there.My grub screen
is broken and when I start  up I get boot :_  It wants the
name of a kernel to boot from

---

### Post by dino99 on 2012-11-05
boot on a livecd, open a terminal and reinstall grub:

```
sudo grub-install /dev/sda
```

otherwise the solution has already been given, re-read your posts

---

### Post by gleble on 2012-11-05
Thats what  I get when I try to boot from a flash drive. No disk drive on an Acer One

---

### Post by rnerwein on 2012-11-05
> **gleble said:**
> Thats what  I get when I try to boot from a flash drive. No disk drive on an Acer One

hi
here my version for recovery mode
linux   /boot/vmlinuz-3.2.0-33-generic root=UUID=2d7726aa-e04a-4265- b5b9-a5cce53b46e2 ro recovery nomodeset

bye

---

### Post by gleble on 2012-11-05
that gives Could not find kernel image: linux/boot/vmlinuz-3.2,0+
-33-generic

---

