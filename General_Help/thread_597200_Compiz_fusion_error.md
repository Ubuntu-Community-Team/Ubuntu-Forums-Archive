---
title: "Compiz fusion error"
date: 2007-10-30
forum: General Help
---

### Post by kdarkentity on 2007-10-30
I am booting gutsy gibbon on a school computer and i have installed compiz fusion, and when i go to /system/preferences/appearance/ and try to enable  normal extra ot custom effects i get this error.

"The composite extension is not available" 

what does this mean and how may i correct it?

---

### Post by raddmadd on 2007-10-30
Well I am a beginner with Ubuntu, so I could be wrong.  However this worked on my computer:

```
sudo apt-get install xserver-xorg
```

---

### Post by kdarkentity on 2007-10-30
> **raddmadd said:**
> Well I am a beginner with Ubuntu, so I could be wrong.  However this worked on my computer:

```
sudo apt-get install xserver-xorg
```

thanks but the error still persists

---

### Post by rwap on 2007-10-30
I'm new at this as well but on mine, i opened my xorg.conf file (sudo nano /etc/X11/xorg.conf ) and went to bottom of file and changed the option at bottom of file that says Composite and it either had a 1 or 0 or a Enable or Disable, Change it to Enable or 1 and try it, if it worked then great, on mine i had to install the XGL thing by going to SYSTEM->ADMINISTRATION->SYNAPTIC PACKAGE MANAGER
and click search then type xserver-xgl mark the found package for install and you should be good to go, If none of that works, i have read where it is helpful if you run fglrxinfo and post its output.


Good Luck, May the force be with you.

BTW: you will need to restart xserver ( i think thats what its called) by pressing Ctrl + Backspace when your done installing XGL.

---

### Post by kdarkentity on 2007-10-30
well actually i managed to get it working, but i wouldn't say i fixed my problem, i had to disable one of my restricted drivers for my ati card , and supposedly the ati card won't work to its full capacity without it soo if its possible i can use both compiz and the restricted driver at the same time that would be great.

---

