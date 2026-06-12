---
title: "Graphic dizzle after suspend ubuntu 16.04"
date: 2017-03-26
forum: General Help
---

### Post by amimaro on 2017-03-26
After I open my laptop lid some weird dizzle appear at the border of some windows. It normalize after restart the computer. 
Same thing is happening with this guy [http://stackoverflow.com/q/42570598/7539844](http://stackoverflow.com/q/42570598/7539844) 
and here is my screenshot [https://drive.google.com/open?id=0B4WVE7_dnjVlcTRlQXBsNDA1djg](https://drive.google.com/open?id=0B4WVE7_dnjVlcTRlQXBsNDA1djg)
What can it be?

---

### Post by ajgreeny on 2017-03-26
Do you also have an nvidia graphics card, and if so, which one using which driver?

---

### Post by billysutomo on 2017-03-29
if i could help answer his question.
im having the same problem as he is.
i also have nvidia GPU and i use the proprietary driver.
this graphic dizzle happen after i suspend my laptop.
to restore it to normal state i have to restart my laptop.
mabye you have the solution to fix this.
thank you before

---

### Post by bickhaus on 2017-03-31
I had the same issue this morning after updating to kernel 4.8.0-45 (HWE) on my 16.04 machine w/ an nVidia 650ti.  I tried booting with the previous kernel (4.8.0-41), but I had the same issue.  I tried the Noveau drivers, but for some reason they would not recognize either monitor properly (stuck at 1024x768 res on single monitor), so that was unusable.  I then tried using switching from the 375.39 proprietary drivers to the 340.102 drivers and that worked (on the latest HWE kernel 4.8.0-45).

---

