---
title: "Laptop holds on battery power"
date: 2008-03-28
forum: General Help
---

### Post by orduek on 2008-03-28
OK, its a long story but please, i need your help here.
I'm using Ubuntu (and Mint) on an HP500, 1gb RAM, 60Gb HDD and Intel 915 graphic card.

when I'm on battery power or with AC but battery is loading the computer hold for few seconds, every few minutes.
I use the System monitor applet so when it happens I see it goes to 100% CPU but not with blue color but with transparent blue (i hope you understand what I mean).

from what I gathered, it looks like something with the power manager.
this happens on Ubuntu 7.10, Linux Mint 4.0 and even the Hardy Heron beta version (upgraded from Ubuntu 7.10).
If Anyone has any idea... please help - its really frustrating.

---

### Post by danwood76 on 2008-03-28
I dont understand the problem.
What do you do before the CPU goes 100%?

This could be an ACPI issue, you could try booting the kernel with acpi turned off, this isnt good for battery consumption on laptops but if yours isnt loading (cant tell from your description) then its probably your better option.

---

### Post by orduek on 2008-03-28
I tried giving the best description.
this is a part of the problem - thats I wasn't able to find a reason.
I thought it was firefox but that thing happens with openoffice or almost any act I do - it just holds. and it doesn't happen everytime but looks like when I'm on battery power it happens a lot.
The computer is loading and everything is ok except when it hold for few second every once in a while (CPU on 100%).

---

### Post by danwood76 on 2008-03-28
How much RAM do you have in this system?
if you have a low amount of RAM ubuntu will start using the swap and will use a bit of CPU power doing it.

-- edit --

sorry didnt realise you already said the ram amount.
how much ram do you have free during this hang?

---

### Post by orduek on 2008-03-29
its hard to tell because i can't access the system monitor during the hold.
but usually i stand on 400-500mb. so i don't think it reaches that high amount.
and why is it happening on battery? is it takes more RAM?

OK, I have some more helpful information.
When this happens the system monitor applet indicates 100% usage of** I/O Wait**

---

### Post by danwood76 on 2008-03-29
Myabe its the CPU frequency scaling thats doing it?
Do you know what processor you have?

If you do have CPU frequency scaling on your CPU load up the pannel applet which tells you what speed your CPU is running at and see if it corolates.

---

### Post by orduek on 2008-03-29
my processor is Intel Pentium M 1.73GHz.

I didn;t understand your suggestion, can you tell me that in simpler words?
Thank you very much.

---

### Post by danwood76 on 2008-03-29
Your processor does support frequency scaling.
Basically when your Laptop is idle the CPU slows down to save power

If you right click the top panel and select 'add to panel' and add the 'CPU Frequency Scaling Monitor' this will then display your CPU speed at the top.
If when you remove your AC cord and the frequency drops see if your PC goes to 100% during this time.

---

### Post by orduek on 2008-03-29
OK great.
I'll try that and see what happens.
Thanx.

---

### Post by ramjet_1953 on 2008-03-29
Try this:

Open a terminal and type in the command [COLOR="Red"]top[/COLOR]

This will give you a list of running processes and you should be able to monitor what process is hogging things.

We will then have something to work with.

Regards,
Roger :cool:

---

### Post by orduek on 2008-03-29
Well. I tried. IQWait usage was 100% but no change in CPU frequency.
any other ideas?

---

### Post by orduek on 2008-03-29
> **ramjet_1953 said:**
> Try this:

Open a terminal and type in the command [COLOR="Red"]top[/COLOR]

This will give you a list of running processes and you should be able to monitor what process is hogging things.

We will then have something to work with.

Regards,
Roger :cool:

the problem with that is I can't show you the situation right when it happens because then everything hold up.
whenever I can watch it - its after the computer is back to normal.

---

### Post by orduek on 2008-04-01
OK, after using the Top command I noticed that when this happens (CPU goes to 100% as I/O Wait) - I see some process that names ata /0 as one of the top ones.
after that goes down, everything is released.

Any ideas?

---

### Post by orduek on 2008-04-04
I would be thankful for some help about this problem.
ata/0 - how can I fix it?
thanx.

---

### Post by orduek on 2008-04-11
anyone?

---

### Post by orduek on 2008-04-22
up.

---

