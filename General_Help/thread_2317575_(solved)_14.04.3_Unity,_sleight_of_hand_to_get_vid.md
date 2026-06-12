---
title: "(solved) 14.04.3 Unity, sleight of hand to get vid card working :)"
date: 2016-03-17
forum: General Help
---

### Post by Kris_M on 2016-03-17
My 650 started freezing - took me a while to realize it was not driver but 650 itself. finally had to pull the card to allow a boot using the 4600 in the intel i5-4670K.
:-({|=:-({|=:-({|=  much upset for my old gtx ti. rats!!!
So off to MicroCenter and picked up an XFX Radeon R7 240 - I wanted to try a Radeon because of the prob/confusion around Nvidia - also since it's been forever since I had an AMD.

It was fairly easy getting win7 to accept the 240 and install and use the drivers and run 3dmark11.

Getting Ubuntu to boot to desktop was another thing.  It would either sit there with a blank screen, or not connect to the monitor.  I thought to trick it by booting to the Intel display to remove any Nvidia drivers but it said there were no additional drivers.

I finally tricked it by using advanced boot and choosing an older kern (41 I believe) and voila it booted (Intel display but 240 card plugged). went to additional drivers and chose ... fglrx-updates (why? I have no idea!) . changed first display again in bios (did this many times) to 240 and booted. Nothing. tried the older kern trick and voila. Booted again and it booted (51?) fine.

I had/have no idea what I'm doing, but I played around and got it to work.

:biggrin::biggrin::biggrin:

---

