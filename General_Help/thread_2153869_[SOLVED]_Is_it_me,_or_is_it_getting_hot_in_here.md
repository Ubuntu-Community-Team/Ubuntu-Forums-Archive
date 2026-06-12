---
title: "[SOLVED] Is it me, or is it getting hot in here?"
date: 2013-06-12
forum: General Help
---

### Post by cessanfrancisco on 2013-06-12
Hi,

I'm pretty new to Linux.  I'm running Ubuntu 13.04 on an Asus UL80JT laptop (all stock except for the wifi card--that's an intel).

So far, since walking away from Windows and OSX I've noticed that Ubuntu seems to run the processor considerably harder (hotter) than Windows 7 did.  I can actually feel the heat in the touchpad (nothing major, just warm).  Is this to be expected?

I've run the TLP command and adjusted the power settings but it still seems to get warmer than what I am used to under Windows.

Any input is greatly appreciated.

Thanks.

---

### Post by ajgreeny on 2013-06-12
What graphic card has it got; an nvidia optimus hybrid system?  If so you may need to figure out how to use bumblebee for control of the graphics which I understand can help reduce temps of both graphic card and hard disk.  I have no reason to use it, having a pure intel graphic chip system, so can not help with more detail, but there is plenty of info around about bumblebee and temperatures,so do a search at [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by Kevin S on 2013-06-13
You might check whether the cooling fan is working.  With some laptops, the cooling fan was apparently controlled by Windows.  If this is the case, you can search for ways to make it work under Ubuntu/Linux.  Also, you may wish to get the "PSensor" utility from the Software Center; it will show a graph of whatever temp sensors it can find in your system.

---

### Post by DeMus on 2013-06-13
Thanks for pointing me to that nice programm. Never knew about the existence of Psensor. Thanks.

---

### Post by Yellow Pasque on 2013-06-13
As ajgreeny pointed out, your laptop is an Optimus model: [http://www.asus.com/Notebooks_Ultrabooks/UL80Jt/#specifications](http://www.asus.com/Notebooks_Ultrabooks/UL80Jt/#specifications)
You should install Bumblebee to shut off the nvidia card at idle: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by cessanfrancisco on 2013-07-10
Thanks everyone!

Bumblebee did the trick!

---

