---
title: "Specify when to use swap."
date: 2006-11-24
forum: General Help
---

### Post by w3bmast3r101 on 2006-11-24
I was wondering if any one knew of a way to tell the system to swap when x% or xMB of ram is left? Just wondeirng.

thnx,

the w3b

---

### Post by VinylPusher on 2006-11-24
I think doing so would defeat the purpose of having the swap file in the first place.

Linux only retires old/unused tasks to swap space rather than trying to keep every single application and background service in RAM. It prefers using RAM as a cache for files, which gives a very good speed advantage to the system overall.

This could easily spill over into "I have 4GB RAM, do I need swap?" territory. Most of the issues would be the same, I'd wager.

Do you have a specific application in mind, though?

---

### Post by po0f on 2006-11-24
w3bmast3r101,

You're referring to the kernel's "swappiness".  Read [here](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29) for more info.

---

