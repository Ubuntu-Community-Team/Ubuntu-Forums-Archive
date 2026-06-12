---
title: "Ubuntu 16.04.4 major graphics glitch Acer Aspire One (GM450 graphics)"
date: 2018-03-27
forum: General Help
---

### Post by piwikiwi on 2018-03-27
Hi, 

I finally ditched my win10 install. Unfortunately both latest Ubuntu and Lubuntu LTS build have a graphics problem on Acer Aspire One ZG5 Intel GM450 netbooks (among others).

The problem has been reported by several others over the last few months, but the (temporary?) fix is not documented very clearly, especially for a fresh Windows 10 convert like myself. 

Apparently some grub editing is required, which doesnt seem terribly hard...but I’m not doing it right apparently.

This is an example of a possible fix: [https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

Can someone please help me with step-by-steps? Assume I speak no Linux-ese &#128540;

Thanks for any help, I have Googled and downloaded and installed all day......&#128077;

---

### Post by malangaman on 2018-03-27
Did you try this?
1. Power on computer.
2. Hold down both SHIFT keys while the computer boots.
3. The GRUB menu should appear.

There will be kernel choices displayed. The numbers are in chronological order from newest down. Try selecting the next lowest until the the system boots.

---

### Post by piwikiwi on 2018-03-27
Yes, that way I can get into recovery mode, but also means I would have to do that at each startup...which seems undesirable.
Or am I missing something?

thx.

---

