---
title: "Random lockups"
date: 2007-06-14
forum: General Help
---

### Post by sheetzam on 2007-06-14
I recently installed Ubuntu server 7.04 on a Shuttle SS31T, running 2.6.20-16-server. I've been having problems with the box since day 1, and I'm hoping someone can point me in the right direction to troubleshoot.
At seemingly random times, the box will lock up and become unresponsive.  I can ping the box, but can't ssh to it, apache stops answering, and the terminal stops working.
I've tried disabling all processes, removing any drivers I don't need, and it hasn't helped.  I've read through all the logs, and haven't found any clues as to the reason for the lockup.  I don't get to see any oops, since the attached monitor is blanked.
Any hints on next steps?

---

### Post by tgalati4 on 2007-06-14
When was the last time you cleaned out the machine and reseated everything?

---

### Post by trippinnik on 2007-06-14
What GPU do you have?  Are you using Beryl?  does the command "dmesg | grep error" give you anything?

---

### Post by sheetzam on 2007-06-14
Isn't it always the case that you realize you have more info to share after a few posts?
tgalati4 - it's a brand new machine, so no dust or seating problems to worry about, in theory.
trippinnik - it comes with a SiS 661 PCIe built in, but I'm not using X, since it's a server.

I've run memtest86 for a day, with no errors.  I've run burncpu to stress the cpu cooling, with no ill effects.

---

