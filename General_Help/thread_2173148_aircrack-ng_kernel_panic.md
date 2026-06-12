---
title: "aircrack-ng kernel panic"
date: 2013-09-08
forum: General Help
---

### Post by hotshot247 on 2013-09-08
when i try to run the aircrack-ng suite by starting off with ```
airmon-ng start wlan0
```,  the whole OS  crashes and i get a kernel panic error and i have to  actually turn the PC off then back on for it to work again. i'm using  ubuntu 13.04. do you think that it's compatibility issues with the  latest ubuntu? i also have a broadcom card so i thought it might have  been that but i used an external wifi adapter with a different driver of  course and it still does it. i tried searching google and this site for the issue but i didn't see anything on it. any help would be awesome! thanks!

---

### Post by Nil_Pointer on 2013-09-08
Quite strange. Does anything interesting appear in logs prior to kernel panic? Something related to wlan0? What are models of adapters and which drivers do they use? Kernel panics suggest there is either problem with drivers or they could be incompatible with used kernel.

---

### Post by hotshot247 on 2013-09-08
nothing really appears. ubuntu just gets unresposive to everything. i can type commands in the terminal afterwards but they don't do anything after it starts acting weird. it happens right after i try to put my card into monitor mode. i know my card supports monitor mode because i've used kali linux and it works. i have the dreaded broadcom card, LOL i've even tried to compile aircrack-ng from source thinking it might be a compatibility thing. their is not much info on this. if google don't know then it's going to be really hard to find, LOL

---

### Post by Nil_Pointer on 2013-09-08
> **hotshot247 said:**
> i can type commands in the terminal afterwards but they don't do anything after it starts acting weird

Well, if I'm not mistaken, when true kernel panic occurs, keyboard LEDs start to flash. Moreover, system will not allow any kind of interaction, since after kernel panic anything could be inconsistent and it's risky to do any operations to avoid any damage. So, it doesn't seem to be a case of kernel panic.

UPDATE: More specifically, Caps and Scroll lock will flash.

---

### Post by hotshot247 on 2013-09-08
The keyboards lights do flash but when it first started doing it, it would black screen on me saying something about kernel panic but now, it's just non responsive, it makes no sense.

---

### Post by Nil_Pointer on 2013-09-08
Well, sadly, I don't think I can help with this problem, but at least there is now more info in this topic, so maybe someone with more experience on wlan drivers will be able to help you.

---

### Post by hotshot247 on 2013-09-08
it's ok thanks for trying though. yea, i'm not an expert either on the subject

---

### Post by mikewhatever on 2013-09-08
> **hotshot247 said:**
> when i try to run the aircrack-ng suite by starting off with ```
airmon-ng start wlan0
```,  the whole OS  crashes and i get a kernel panic error and i have to  actually turn the PC off then back on for it to work again. i'm using  ubuntu 13.04. do you think that it's compatibility issues with the  latest ubuntu? i also have a broadcom card so i thought it might have  been that but i used an external wifi adapter with a different driver of  course and it still does it. i tried searching google and this site for the issue but i didn't see anything on it. any help would be awesome! thanks!

Which Broadcom adapter do you use, and which driver?

---

### Post by oldos2er on 2013-09-08
If you need help with aircrack please use the Backtrack/Kali forums, we don't support it here.

Closed.

---

