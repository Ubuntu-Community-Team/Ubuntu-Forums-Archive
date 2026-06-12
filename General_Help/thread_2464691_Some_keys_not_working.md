---
title: "Some keys not working"
date: 2021-07-09
forum: General Help
---

### Post by videoclocknet on 2021-07-09
Hi guys, 

Since I applied some updates in my Ubunt 18.04, some keys stopped working in all applications, specifically a s d f j k l and Enter keys.

I upgraded it to 20.04 but the issue remains. 

I've tried to run 'sudo apt-get install xserver-xorg-input-all' , with no success.

Do you know how to solve this?

Kind Regards

---

### Post by Autodave on 2021-07-09
I would d-l and make an .iso install medium and boot from that and see if your keyboard works.  Or try another keyboard: they do go bad.  You could also have a stuck key: unplug the keybaord and pound (lightly) on all of the keys: ALL of them.  Turn keyboard upiade down and pound some more.

---

### Post by Impavidus on 2021-07-09
+1: check on a live disk.

You can also check the keys using the xev tool. You can start it from a terminal window. It will print some information in the terminal about every key or mouse event. It will show you whether the keypress was detected and as which character.

A few keys not working, in particular if all are on the same row (assuming this is a qwerty keyboard), sounds like a hardware problem

---

### Post by Unguidedone on 2021-07-09
i would say this is 95% chance of a hardware problem, test with a alt keyboard.  always keep a spare on hand you have no idea when you need to smash a keyboard during gaming and scream in german.

also it could mean the keyboard needs to be cleaned, i use compressed air and disassemble it from time to time to make sure and replace worn buttons.

---

### Post by videoclocknet on 2021-07-12
Hey guys,

I confirm this is a hardware issue. I've bought an external keyboard and works perfectly, while the laptop keyboard fails with any Operating System

Thanks for all your support

---

