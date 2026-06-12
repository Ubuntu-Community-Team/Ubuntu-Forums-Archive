---
title: "New monitor"
date: 2008-03-25
forum: General Help
---

### Post by Alias- Human on 2008-03-25
I just got a new monitor and this one is a wide screen. How would I tell Ubuntu that I have a new monitor and what it is, (CHIMIE CMV 937A) so that I can chose a refresh rate and resolution that is approprate?

Thank you for any help, 
Alias- Human

---

### Post by overdrank on 2008-03-25
> **Alias- Human said:**
> I just got a new monitor and this one is a wide screen. How would I tell Ubuntu that I have a new monitor and what it is, (CHIMIE CMV 937A) so that I can chose a refresh rate and resolution that is approprate?

Thank you for any help, 
Alias- Human

Hi and you can try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the ctrl, alt, backspace keys

---

### Post by Alias- Human on 2008-03-25
Thank you.
That worked very well... (after I realized that the space bar selected and unselected the options and not the enter command, I do amuse myself sometimes. :) )
I'm marking this as 'solved'.
Thanks again Overdrank,
Alias- Human

---

### Post by overdrank on 2008-03-25
> **Alias- Human said:**
> Thank you.
That worked very well... (after I realized that the space bar selected and unselected the options and not the enter command, I do amuse myself sometimes. :) )
I'm marking this as 'solved'.
Thanks again Overdrank,
Alias- Human

Thank you and good luck!:KS

---

