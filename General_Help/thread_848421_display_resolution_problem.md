---
title: "display resolution problem"
date: 2008-07-03
forum: General Help
---

### Post by enuckon on 2008-07-03
Yesterday morning, after weeks of stable work, display resolution on gutsy 7.10 desktop has switched itself to a lower resolution mode upon system startup.   There is no right resolution/frequency option in the display controls any longer.   Any ideas how to fix that?   Do you know if this is a bug/virus/hardware malfuntion?    In trying to fix the problem I got to a state when the screen in scramled to a total mess of lines, so only the recovery mode is usable right now.   Is ther ea way to avoid system re-install?  Appreciate any suggestion.

---

### Post by wolfen69 on 2008-07-03
try
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot

---

### Post by enuckon on 2008-07-03
Thanks a lot for your help!   Is there a reason for random changes in configurations like this?

---

### Post by wolfen69 on 2008-07-03
computers are not an exact science. i've seen it happen on every OS i've used. there are so many things working at once, (hardware and software) that i'm surprised it works as well as it does.

---

### Post by Pyrophorus on 2008-07-03
I had major problems with resolutions.

I switched my Acer monitor with a LG, and eveything was fine

---

### Post by enuckon on 2008-07-03
Yes, it is Acer, how do you know?  Well, as I said, it was fine for weeks until it had changed by itself.   It wasn't perfect (like, the terminal window size numbers do not resolve, when you stretch/shrink the window), but it was okay.  Thanks for info.

---

