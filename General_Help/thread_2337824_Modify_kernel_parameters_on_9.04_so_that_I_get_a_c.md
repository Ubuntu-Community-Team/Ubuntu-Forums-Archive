---
title: "Modify kernel parameters on 9.04 so that I get a console boot rather than X"
date: 2016-09-21
forum: General Help
---

### Post by bbiandov on 2016-09-21
Hi everyone,

I am finding 100% defective information on how to modify kernel boot parameters on 9.04 so that I get a console boot rather than X

There's no /grub configuration files etc in any of the referenced answers I've found so far which are all accurate answers but NOT for 9.04

The /boot/grub/grub.conf contains the following and I need to know how to modify the highlighted in red parameters so that I get plain text console boot:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic uuid            6d60816a-3474-4070-b4a6-e8264932af4c
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=6d60816a-3474-4070-b4a6-e8264932af4c ro **[COLOR="#FF0000"]quiet splash[/COLOR]**
initrd          /boot/initrd.img-2.6.28-11-generic 
quiet 

```

Thank you
~B

---

### Post by TheFu on 2016-09-22
9.04 was EOL in 2010. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Bucky Ball on 2016-09-22
> **bbiandov said:**
> I am finding 100% defective information on how to modify kernel boot parameters on 9.04 ...

Lucky you are finding any at all and you are unlikely to find much here, as

> **TheFu said:**
> 9.04 was EOL in 2010. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

A console rather than an x boot? Not sure what you mean. You want to end up at ... a CLI? Is Ubuntu what you are looking for? I don't know about this stuff, but would [this be any good]("https://help.ubuntu.com/community/Installation/MinimalCD")?

---

