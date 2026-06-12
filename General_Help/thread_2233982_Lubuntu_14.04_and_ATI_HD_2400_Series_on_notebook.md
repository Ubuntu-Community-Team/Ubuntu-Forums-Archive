---
title: "Lubuntu 14.04 and ATI HD 2400 Series on notebook"
date: 2014-07-11
forum: General Help
---

### Post by Portaro on 2014-07-11
I try the two options try install fglrx with Optional drivers search tool and find nothing, then I try manually make the installation->
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
> 
sudo apt-get install fglrx-updates fglrx-amdcccle-updates

then

> 
sudo aticonfig --initial

but the command return that dont find any card.

Then I try download directly the driver here - [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86)

I install kernel headers and other tools based on web instructions, but I cant 
install nothing for some reason the headers isn't identify by installer.

What i the method to install this drivers, I need this because my game Medieval total war have bad graphics without this drivers on Ubuntu 12 works well,
but rvently I replace to the new release.

---

### Post by QIII on 2014-07-11
Unfortunately, that card is no longer supported by ATI and there is no fglrx driver that will work for it for any version of Ubuntu after 12.04.1.

You will need to use the open source Radeon driver that was installed by default when you installed Ubuntu.

You will have no better luck with other recent distributions, as they also use the newer X Server.

---

### Post by Portaro on 2014-07-11
My god , I have only one option come back to 12.04!

Puff I love Medieval is a problem.

Many , many thanks for your help.

Greetings.

---

