---
title: "boot (iso) images with grub"
date: 2007-09-19
forum: General Help
---

### Post by somfi on 2007-09-19
i want to burn a multiboot dvd with a range of linux images. the first grub should load the grub of each image. thats what i tried:

title test
rootnoverify (device,0)/iso/ubuntu.iso
makeactive
chainloader +1

it reports error 13 (unsupported file extension)
img format is also not supported

any idea?

---

### Post by somfi on 2007-09-19
OK, i will ask a more general question:

it is possible to load grubs out of a grub?

---

### Post by tszanon on 2007-09-19
Since I can't answer your questions, I'm going to ask you another question:
Why would you do that? If you want to create something like a multiboot dvd, why don't you put all options under a single menu? Keep in mind that I never did something like it, so I don't know if what I just said can be done.

---

### Post by headchange on 2008-07-12
[http://www.justlinux.com/forum/showthread.php?t=150078](http://www.justlinux.com/forum/showthread.php?t=150078)
hope this helps, i havent personally tried it, i ned to get a hold of some more isos

---

