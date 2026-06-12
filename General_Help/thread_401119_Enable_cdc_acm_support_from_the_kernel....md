---
title: "Enable cdc_acm support from the kernel...?"
date: 2007-04-04
forum: General Help
---

### Post by Seine on 2007-04-04
Hi again o ever helpful Ubunteros!

I'm trying to get files from my Motorola V360 phone. I have compiled moto4lin but am trying to troubleshoot why I can't get a meaningful connection to the phone.

If I go to the [V360 page on moto4lin wiki]("http://moto4lin.sourceforge.net/wiki/V360") it says - "Firstly you have to install cdc_acm support from the kernel."

I have no idea how to do that. What does it mean? Do I need to rebuild the kernel? Is it a dire action? Or is it a single line of config?

Thanks again!
Jem

---

### Post by yaidiot! on 2007-08-13
sudo modprobe cdc_acm 

And remember to change the device name in the preferences of moto4lin.

---

