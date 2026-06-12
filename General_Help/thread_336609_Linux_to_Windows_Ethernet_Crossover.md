---
title: "Linux to Windows Ethernet Crossover?"
date: 2007-01-11
forum: General Help
---

### Post by ianthepetrock on 2007-01-11
I have a windows computer that has working wireless right now and a linux computer without wireless in the same room. Is it possible to network these two together so that i can get internet on the linux computer via ethernet crossover? Do I really need a **crossover** cable?

---

### Post by kebes on 2007-01-11
In principle you should be able to activate Windows Internet Connection Sharing (ICS) on the Windows machine, and it will provide a DHCP+NAT internet access on your ethernet connection. Ubuntu should then immediately connect to this without issues.

Yes, you need a crossover cable. Actually, I believe some newer ethernet cards with automatically switch modes when required, so a normal cable might work if one of the two computers has the right kind of ethernet card... but you might not be so lucky and might need to get a crossover cable.

Good luck.

---

### Post by anthro398 on 2007-01-11
No, you don't need a crossover cable.  You could use a hub, a switch, or a usb kit made for that.

---

### Post by n3gbz on 2007-01-11
I believe some sort of a crossover "device" is needed.  That can be a cable, switch, router, etc. 

So the answer is: No a crossover "cable" is not needed.

But Yes a crossover "device" or "mechanism" is needed.

---

### Post by Hanzerik on 2007-01-11
If you have the tools to make cables, here is a diagram.

[http://www.cisco.com/warp/public/135/bbsm_lvl2spprt3.gif](http://www.cisco.com/warp/public/135/bbsm_lvl2spprt3.gif)

---

### Post by scrooge_74 on 2007-01-17
Another great solution could be this [http://www.thinkgeek.com/gadgets/tools/7470/](http://www.thinkgeek.com/gadgets/tools/7470/)

---

