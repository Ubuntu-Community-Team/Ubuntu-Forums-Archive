---
title: "Overheat -&gt; Crash while Updating"
date: 2007-04-03
forum: General Help
---

### Post by bazald on 2007-04-03
So, I did a fresh install of edgy on a friend's computer.  Then, when updating, about 2/3 of the way through, it overheated and forcibly shut down.  Now on boot it kernel panics.  Is there any reasonable way to salvage this?

I ask, because his optical drive doesn't work, and I swapped hard drives with him to get it installed - a painful experience I don't have time to do again.

Thanks in advance.

---

### Post by ndefontenay on 2007-04-03
So, you mean you've installed Linux Edgy on his hard drive with your PC because his CD ROM is not working. Is that right?

I would prefer to exchange my CR ROM with him and install Linux on his PC with his hardware. I think your overheating and kernel panic problem could well be related to the fact that linux has detected a certain amount of hardware and is now in an environment he doesn't know.

Imagine you wake up one day in a place you don't know. Pretty scary! I would kernel panic too!

Potential solution: swap CD ROM drive with your friend's PC and install again.

---

### Post by bazald on 2007-04-03
Interesting idea, but we're both using laptops.  Thanks though.

Edit:  By the way, your assumption was right.  Also, the kernel panic only took place after the crash mid-update on his computer.

---

### Post by Ubluedog on 2007-04-03
acpi is the problem by the sounds of it , linux doesnt handle the speed control of the cpu cooler in laptops very well, on the compaq laptop here i hardwired the fan onto 5 volts to run it flat out as turning off the acpi didnt work
do a search in the  laptops section for info about what files to modify using sudu gedit etc. that will hopefully stop the laptop overheating.
good luck , but if you both have similar laptops i would swap the cdroms and see how it goes on instal.
report back how you go
cheers

---

### Post by bapoumba on 2007-04-03
Hello :)
My little story here: happened to me when installing feisty (I've been fresh installing ubuntu since warty with no problem). My laptop is 2 years old, and had been overheating recently. It did not go through the install (about 80% of it). It did go through a text mode install (so you end up with no X), the temps were 90 and 95°C at the end of it.
As still under warranty, it's gone back for repairs. One of the fans is dead.

---

