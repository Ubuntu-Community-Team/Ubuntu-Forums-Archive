---
title: "rescue data of a screenless laptop"
date: 2008-06-27
forum: General Help
---

### Post by songshu on 2008-06-27
hi all,

i promised someone to give a hand with their broken laptop this evening and i want to make sure i can get this prepared since i will not have an internet connection or access to all of my gear.

the problem is that the laptop has a broken screen, it boots alright but the screen stays black.

i will replace the broken laptop with a new one and i need to get an extensive music collection copied over from the old to the new laptop.

the simplest thing i could think of (although i never tried it) is to use a crossover cable when booting the old from a live-cd (it had windows 98 installed) and then ssh in to the box.

i know how to make a custom install cd to include ssh so that will not be a problem.

but is there any other i should think of?

what about the crossover connection? how do you set it up, i could also set up a router and a small network.
what user does the live-cd run as?

anybody some tips and hints to think of?


much obliged

---

### Post by justleen on 2008-06-27
pfoe, thats a tricky one... doesnt the laptop have an external monitor connection by any chance?

Im not sure wehter ssh is on the live cd. If it is, i would use cross over, but a router/hub, and let dhcp do the work..

Personally, i would just take the drive out, and hang that in your PC (you can buy adapters to normal IDE for a few euro/dollar)

---

### Post by enchesss on 2008-06-27
yeh get a monito cable and hook it up if you can just like justleen says.
you clould also put the drive into another laptop and then backup to an external drive which would also keep the files safe for transfer later.

---

### Post by songshu on 2008-06-27
> pfoe, thats a tricky one... doesnt the laptop have an external monitor connection by any chance?

don't know, and neither does the laptop owner ;) besides i don't really feel for dragging along a monitor.

> 
Im not sure wehter ssh is on the live cd. If it is, i would use cross over, but a router/hub, and let dhcp do the work..

ssh isn't, but i can make my own image that does.
DHCP might be the safest bet indeed

> 
Personally, i would just take the drive out, and hang that in your PC (you can buy adapters to normal IDE for a few euro/dollar)
i don't have the time to go back and forth

---

### Post by Taxman415a on 2008-06-27
OpenSSH server, which is what you need to ssh into a box is not installed by default. No servers are open by default in fact. I agree with justleen that the external monitor port or pulling the hard drive out are your best bets. 

Otherwise you could try hitting the perfect sequence of keys needed to get a terminal open to install OpenSSH server (Alt-F1 gets you to the Applications menu by the way then t then down arrow should get you a terminal). For fun if you enable accessibility from the boot screen (F5 then down a couple to screen reader) the computer will speak outloud what you type into the terminal so you know if you mistyped it. Hard to get used to though since it speaks everything.

---

### Post by justleen on 2008-06-27
> **songshu said:**
> 


i don't have the time to go back and forth

erm.. then go up there, setup the new laptop, take the old one with you.. 

This is most likely one of those "little things" that end up eating hours f your time..

- or -

get the replacement laptop , place th old drive in there, burn what you need, swap back to the new disk?

---

