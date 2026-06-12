---
title: "Slow boot times in Gutsy"
date: 2008-04-17
forum: General Help
---

### Post by revelationman on 2008-04-17
I know this is has been an issue for many laptop users but for me  it takes  1:48 just to boot or get the login screen. 
That is not acceptable, for laptop user's going through customs especially Canada an US were there is very stringent security checks you are asked to boot your laptop. So after a long flight you have to deal with a slow boot up  and believe me folks the customs officials their  have very little patience.
That being said what is the solution or will there be a solution with Hardy I hope so,  I mean XP and Vista booth load faster then  Ubuntu on a laptop
My Laptop has 1.5 gig of Ram and Sempron Mobile Processor 1.8 3500  so I know it is not a hardware issue. 

I have attached my boot chart for anyone  to have a look 

:confused:

---

### Post by Diabolis on 2008-04-17
From where you got that chart?

You can see which process is the one that takes more time to complete by removing temporarily the ubuntu splash screen while booting.

Reboot your pc and while at grub menu press **e**, edit the line that says kernel and remove the word **splash** then press **b** to boot.

You can read what all this letters do on the bottom part of the grub menu.

---

### Post by warp99 on 2008-04-17
You can find more information on how to here:

[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

Please next time search first for your answer since there are numerous threads in the 'Tutorials & Tips' forums on how to increase performance and reduce boot times.

---

