---
title: "Running slow -  ntos_wq?"
date: 2008-03-01
forum: General Help
---

### Post by TheWhatkin on 2008-03-01
Ubuntu has started to run really slowly on my laptop. looking at the top command, there's a process called ntos_wq which is sucking up 50 - 60 % of my CPU much of the time.

What is it? Can I get rid of it?

---

### Post by boucek on 2008-04-05
I am also having this issue. The CPU % used is significant on my IBM a20m (only 500 MHz).

Searching Google, I've discovered that ntos_wq is related to ndiswrapper, the module used to wrap the Windows driver for your wireless card.

In my case, I'm using a Belkin F5D8000 Pre-N PCMCIA card. 

It seems killing the process through top solves the immediate problem (I'm on ethernet right now) but upon restarting the computer and reloading the module, ntos_wq eats up my CPU again.

Anyone know if this is a known bug with the ndiswrapper module?

---

