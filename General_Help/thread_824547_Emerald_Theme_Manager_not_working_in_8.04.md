---
title: "Emerald Theme Manager not working in 8.04"
date: 2008-06-10
forum: General Help
---

### Post by kavoura on 2008-06-10
I have installed the latest Ubuntu 8.04 on my new AMD64 PC. All seems to be okay, except for the Emerald Theme Manager. I installed the Compiz Manager and Emerald, and I can get all the fancy wobbly windows effects, etc., but the Emerald theme manager is currently doing nothing. I have selected and created a theme based on vrunner, but when I click on it, nothing happens. On my older PC, which is running Ubuntu 7.10 (32-bit), I created the same theme a while ago and it has always worked on this PC. I compared settings between the two and could not see any differences in either Compiz or Emerald.

Is there a problem enabling Emerald in 8.04? Is there something else I need to install to get it to work?

I have installed the latest nvidia drivers via Synaptic. The graphics card has 256 MB RAM, the PC has 4 GB RAM.

---

### Post by Forlong on 2008-06-10
Run ```
emerald --replace
``` via [Alt]+[F2]

---

### Post by nickdbliss on 2008-06-11
furthermore to start it automatically, go to compizconfig setting manager and under effects,open windows decorator. In the command box type emerald --replace. ;)

---

