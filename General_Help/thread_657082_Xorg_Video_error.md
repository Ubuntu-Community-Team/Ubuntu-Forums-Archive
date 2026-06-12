---
title: "Xorg Video error"
date: 2008-01-03
forum: General Help
---

### Post by Bablefish on 2008-01-03
This  all goes back some weeks ago when I crashed Xserver, I did manage to get my computer back up and running once again. But unfortunately I made a mistake in the settings and I can't get back into Xorg to reset them. You see I have a 16 bit video card and I accidentally set it for 24 bit. 

I tried when Ubuntu 7.04 is up and running and I try this command

sudo dpkg-reconfigure xserver-xorg 

and it puts me into not the settings I want 

I also tried that same command line when I go into grub when I stop it from going into a normal boot.
I just an error message saying unknown command error 27.

Does anybody here know a work around so I can get in to Xorg and finally fix my mistake?

---

### Post by geirha on 2008-01-03
Boot up in recovery mode, which should bring you to a root shell, then either run ```
nano /etc/X11/xorg.conf
``` and change the file manually, or run ```
dpkg-reconfigure xserver-xorg
```

If you edit it manually, it's probably just a matter of browsing down to **Section "Screen"** and change the value of **DefaultDepth** from 24 to 16.

---

### Post by PmDematagoda on 2008-01-03
You can execute:-
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

This will revert the settings of the X-Server back to defaults and should be able to get your GUI back.

---

### Post by Bablefish on 2008-01-03
Did this but how do you save the new setting there is no obvious way to do this

Boot up in recovery mode, which should bring you to a root shell, then either run
Code:

nano /etc/X11/xorg.conf

HOW DO YOU SAVE THE NEW SETTING????

---

