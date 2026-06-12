---
title: "Ubuntu Hardy Heron SATA drive issue"
date: 2008-04-26
forum: General Help
---

### Post by mudlord on 2008-04-26
Hi there,

I am having major problems with installing Ubuntu Hardy Heron.

What got me attracted to this release is the new Wubi install option, which is perfect for what I am doing, as I only need around 30GB of HD space allocated to Linux.

I tried installing, yet it had issues detecting my 320GB SATA drive. As in, not detecting it at all. Currently it is running in ACHI mode under Windows, and runs great. Whereas with Hardy Heron, it completely fails to detect it. And all my code and data is on the SATA drive. And Gutsy Gibbon detected it fine.....

I also have a smaller, 80GB IDE hard drive, which has my Windows XP installation on it. So, my 320GB SATA drive is my primary storage for all non OS related things.

Is there anything I can do or is Hardy Heron untolerant of SATA drives in this configuration?

EDIT: Turned on IDE mode in the BIOS, still works great in Windows. :). Hopefully works just as well in Linux.

EDIT2: Yup, managed to solve my own issue.

---

### Post by dokhap on 2008-05-09
Hi

To beginwith, sorry for my english (i'm not a naturally speaker !)

I've the same problem for my ide drive on an old asus motherboard (p4p800e-deluxe)

As i know, for my problem, it comes from the a bad implementation of the kernel module which deals with my controleur (in french !) "ICH5"

And for you, what's your motherboard and sepcifically the "controleur" ?

Bye

---

