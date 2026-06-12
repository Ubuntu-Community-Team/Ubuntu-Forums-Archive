---
title: "Question: Boot XP if Linux crashes (dual boot)?"
date: 2007-01-28
forum: General Help
---

### Post by arodvb on 2007-01-28
Ok, I'm going to order a new harddrive since this one keeps popping up a message saying I should replace it. I want to get atleast 100 gigs for XP, but figured if I will be doing a fresh install now is the time to give Ubuntu a try so I want to dual boot XP and Ubuntu. I am going to install XP first, then Ubuntu 2nd using the Grub boot loader. Now if Ubuntu would happen to crash, meaning Grub would no longer boot, can I still boot XP? Would I just need to put the XP disc in to boot from the disc? And could I then set it up to just boot XP normally or would I need to constantly put the disc in to boot from if I choose to not install Ubuntu again?  I just want to find out before I order a 160 gig harddrive instead of a 100 gig.

Any help is appreciated! :guitar:

---

### Post by arodvb on 2007-01-28
Anyone know for sure?  I'd like to order this harddrive today. :D

---

### Post by dexter on 2007-01-28
If you want to remove grub just put in your windows cd, go to recovery mode and type: fdisk /mbr. This will remove grub from the mbr (master boot record) and replace it with the windows boot manager which automatically boots to windows.

---

### Post by arodvb on 2007-01-28
Awesome, thanks for the help.

So I just need to install XP, then pop in the Ubuntu CD and set it for the 2nd partition, and it will setup Grub?  I remember trying this before and it seemed like a piece of cake.  Just glad if Ubuntu fails I can run XP normally.

---

