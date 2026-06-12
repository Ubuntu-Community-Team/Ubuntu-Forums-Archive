---
title: "Initial black screen then disk encryption password entry problem"
date: 2016-11-05
forum: General Help
---

### Post by Paul_Berry on 2016-11-05
Greeting!

This morning I woke to a boot into a blackscreen, ok driver problem probably. Nvidia GTX750 Ti. Last year I used to load the driver from command line but Ubuntu eventually things changed and the GUI was fine. Has been fine for a year.  Ok so tried, nomodeset in grub, no go, blackscreen. Ok tried boot into graphical failsafe, the option panel ok is locked up, can not enter ok, no go.  

Ok advanced options in grub, boot previous kernel, boots to disk encryption login and then onto desktop login, login at desktop and the graphical interface crashes after password accepted, black screen. 

Ok reboot to same point, using previous kernel, but instead of logging in I went into consol command line.  Purged Nividia drivers and reinstalled drivers from ppa edgers. 

Ok restart with latest kernel (ubuntu 16.04), this time the boot takes me to the graphical encryption login with screen in low resolution, thats better than black screen, but the real problem is now the encryption login now has no focus, I can not enter anything in encryption login. Ok looked online and see something similar on launchpad 2014 but with no solution that I could see.  I have saved all my files manually so its no biggy, I am a little nervous doing a fresh install because I am on a dual boot machine with UEFI bios, Im a bit nervous that I may lose access on my oother drivewhich is windows.  Not sure what to do. Any advice would be much appreciated.

---

