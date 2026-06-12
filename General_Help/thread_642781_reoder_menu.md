---
title: "reoder menu"
date: 2007-12-17
forum: General Help
---

### Post by irshan on 2007-12-17
i want to reoder the my menu list such as first windows then linux etc....so is there way to make reoder pls help me.

---

### Post by chewearn on 2007-12-17
Here you go:
[Link]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/") (pls note the typo in this article, menu.lst, not menu.ls)

---

### Post by erginemr on 2007-12-17
Hi,

Please read the following help page thoroughly:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Details are given therein, but basically, there exists a section (chunk) of a few lines for each of your boot items in your 
```
/boot/grub/menu.lst
```
file and two relevant lines at the beginning of the file
```
default    0
timeout    5 
```
that lists the "default" operating system (grub item) to load automatically after a "timeout" of specified seconds, counting the available items from zero.

So, following the example above, "default 0" is actually the first item in your list, whereas "default 1" is the second item in your list. And "timeout  5" means to wait for 5 seconds before loading the default selection.

You can also play with the order of items in the grub menu by moving the groups of each item one before the other, but I would recommend you not to do that, because the default order is logical enough and you can easily mess your grub menu and render you system unbootable.

In any case, please take a copy of your original menu file first with:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak
```
which you can restore via a Live CD, in case of any serious problem in the booting process.

---

