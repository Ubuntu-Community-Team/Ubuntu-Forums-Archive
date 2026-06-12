---
title: "Black screen for 2 min after ubuntu spash"
date: 2008-01-29
forum: General Help
---

### Post by Marco Ceppi on 2008-01-29
Hey all.

I think something has gone wrong in my Ubuntu installation. After the Ubuntu Splash screen the screen goes black with a single blinking cursor. After about 2-3 min of no typing and just the blinking GDM launches


I think a script or services is stalling the startup process, how can I go about finding out what is slowing my startup down and how I can rectify it.


Thanks,
Marco

---

### Post by Marco Ceppi on 2008-01-30
7.10 Gutsy Gibbon
HP Compaq nc6220 Laptop

This problem just recently started.

---

### Post by nick_h on 2008-01-30
Remove the word "splash" from your kernel boot options next time you boot.

From the grub menu, press "e" to edit a line.  Then press "b" to boot.

You will see messages scroll up the screen which should give you an indication at which stage the problem occurs.

---

### Post by essexboyracer on 2008-01-30
something similar to what I had, perhaps to do with usplash which gets messed up, I also had a slow shutdown problem due to turning off power management on a desktiop machine

---

