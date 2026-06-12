---
title: "Mouse Click Delay / Lubuntu."
date: 2020-03-22
forum: General Help
---

### Post by scarboro on 2020-03-22
Friends, I made an adjustment to Lubuntu.  I regret having made it, but cannot find the way to undo it.  Lubuntu does something to override standard Linux, to respond to mouse clicks more quickly.  I turned that off.  Can anybody help?

---

### Post by mörgæs on 2020-03-23
Which adjustment did you make and which version of Lubuntu?

---

### Post by coffeecat on 2020-03-23
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by scarboro on 2020-03-26
Thank you [COLOR=#DD4814]mörgæs[/COLOR].  That's just the trouble.  I can no longer find the adjustment that I made. I have Lubuntu 19.04 64-bit.

---

### Post by mörgæs on 2020-03-26
19.04 is out of support and has been since January so the cure is a fresh install of 19.10. 
When that is running you should change all passwords which have been entered while using 19.04.

---

### Post by scarboro on 2020-03-28
I think I found the solution.  Lubuntu LXQt Session Settings > Application Autostart > Spice vdagent sets the following:

[COLOR=#111111][FONT=monospace]Client mouse mode (no need to grab mouse by client, no mouse lag)[/FONT][/COLOR]

---

### Post by mörgæs on 2020-03-28
It's not really a solution if it's based upon 19.04. Security first.

---

