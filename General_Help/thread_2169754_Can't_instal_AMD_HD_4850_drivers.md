---
title: "Can't instal AMD HD 4850 drivers?"
date: 2013-08-23
forum: General Help
---

### Post by Frentoni_Klaus on 2013-08-23
As the thread title says i can't install hd 4850 drivers. The major problem is that i don't even know if the drivers are installed or not. First of all, in the additional drivers tab i don't have any driver and says "No proprietary drivers are in use on this system." Secondly, when i go to the  System -> Details -> Graphics in the section Driver is written "Unknow" and in the Experience tab it is written "Standard". I've tried to install the driver in 2 ways. By  sudo apt-get purge fglrx  -> sudo apt-get install linux-headers-generic and then reboot , and also i searched another way (don't remember it very well) which, i think , is more complicated. I had to download the driver from amd.com, then i had to write something in the terminal to make a deb file i gues... Sorry if i speak non-sense but i recently switched to ubuntu and i'm a newbie...So any help is more than welcome.

If it matters: Ubuntu version is 12.04 LTS x64

---

### Post by jgcsd on 2013-08-23
Last time I tried using ATI's graphics drivers for my HD 4870, I found out that they no longer supported graphics cards pre HD 5xxx.

Not that the closed source drivers were very good anyway.

Personally, I use the default open drivers on my everyday Ubuntu installation, and the xorg-edgers open driver on my gaming Ubuntu installation, which have always been pretty reliable and perform much better than 12.04's normal graphics drivers in my experience.

But, I'm no expert.

---

### Post by Mark Phelps on 2013-08-23
There are two versions of 12.04 out there: 12.04.1 and 12.04.2.  If you installed when 12.04 first came out or upgraded to it when it first came out, you will most likely have 12.04.1.  That version uses the X-server version that is compatible with the AMD HD 2x/3x/4x-series fglrx drivers.

If you have the 12.04.2 version, that has an X-server version that is NOT compatible with the AMD HD 2x/3x/4x-series drivers -- and in that case, you won't be able to install fglrx drivers.  

AMD dropped fglrx driver support for the HD 2x/3x/4x-series last summer and those drivers won't work with anything newer than 12.04.1.

---

### Post by Frentoni_Klaus on 2013-08-23
The version is 12.04.2 ... So that's that... Damn. I was so excited to swich from windows 8 to ubuntu. 
Thank you Mark.

---

### Post by QIII on 2013-08-23
You can still use Ubuntu!  Just install 12.04.1 and enjoy!
:)

---

