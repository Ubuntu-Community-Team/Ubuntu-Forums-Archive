---
title: "Grub wont boot windows"
date: 2007-02-07
forum: General Help
---

### Post by sendas on 2007-02-07
Hi, I am having some trouble with a dual boot ubuntu and windows machine. I already had ubuntu installed and working great so I installed Windows XP after ubuntu.

my partition scheme is the following
/dev/sda1 boot
/dev/sda2 swap
/dev/sda3 root
/dev/sda4 windows
on a single hard drive I, 

so I installed windows onto a separate partition


booted a ubuntu live cd and did the following commands

```
# grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

Now I needed to setup the grub menu with a windows entry 

I did this

```
title=Windows XP
root (hd0,5)
makeactive
chainloader +1
boot
```

Grub works if I select ubuntu ,but it gives an Error 22 if I select Windows Xp

any suggestion would be much appreciated.

---

### Post by housam on 2007-02-07
Try to use the [super grub disk]("http://supergrub.forjamari.linex.org/")

---

### Post by raul_ on 2007-02-07
And then read this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22")

---

