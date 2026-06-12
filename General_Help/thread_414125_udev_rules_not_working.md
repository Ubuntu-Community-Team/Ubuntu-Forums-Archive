---
title: "udev rules not working"
date: 2007-04-19
forum: General Help
---

### Post by vionescu on 2007-04-19
Hi,

I'm using qemu+kqemu. I would like /dev/kqemu to be created automatically when kqemu module is loaded, so i wrote the following udev rule (in /etc/udev/rules.d/50-kqemu.rules):

KERNEL=="kqemu", NAME="%k", MODE="0666"

The problem is it is not working, /dev/kqemu is not created. I also modified 50-kvm.rules to look like this:

KERNEL=="kvm", NAME="%k", GROUP="kvm", MODE="0666"

However /dev/kvm is still created with 0660, just as before. Am I missing something? Why aren't my rules working?

Thank you!

LE: forgot an = sign
LE2: I'm using Ubuntu Feisty Fawn

---

### Post by vionescu on 2007-04-19
Up

---

### Post by vionescu on 2007-04-20
Up

---

### Post by haypo on 2007-04-23
Ok, I found the reason why the node is not created! udev requires major to be 0 whereas kqemu-common forces the value 250. See my comment on the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/kqemu/+bug/105933](https://bugs.launchpad.net/ubuntu/+source/kqemu/+bug/105933)

---

### Post by vionescu on 2007-04-23
Yes, this works. Thank you for your help!

---

