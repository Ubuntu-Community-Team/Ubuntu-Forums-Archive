---
title: "Splash screen hangs"
date: 2007-04-05
forum: General Help
---

### Post by vav on 2007-04-05
I had to change my laptop LCD panel, to one with a different resolution, and after that my boot up splash screen always hangs. I've upgraded to edgy and now to feisty, but the problem persists. 
Before installing feisty I had run the live CD, and the splash screen from that worked perfectly. So it seems to me that there might be some package to reconfigure which would fix the problem.

The issue I have is that every time I upgrade my kernel, the splash option is default and hence my computer hangs on reboot. I guess I could edit menu.lst to give a default nosplash option or something but I'd rather fix this problem than work around it...

Any  ideas anyone?
Thanks

---

### Post by vav on 2007-04-05
huh... had a eureka moment
Turns out there exists a /etc/usplash.conf

The only contents of this file are the screen resolution. So I did
sudo vim /etc/uslpash.conf

and changed the resolution. This fixed shut down splash

then I did 
sudo dpkg-reconfigure usplash

That fixed the boot up problem :P. I will post this as a bug.

---

