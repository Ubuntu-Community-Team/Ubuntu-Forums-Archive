---
title: "Can't see login window"
date: 2008-03-27
forum: General Help
---

### Post by Touch.Code on 2008-03-27
Hi,

I cannot see my login window any more. Since I have had problems with my graphics card and compiz-fuzion.

From installing Ubuntu I could not see the Ubuntu loading screen and now I can't even see my login window. Any help?

Thanks,
James

---

### Post by ajgreeny on 2008-03-27
What graphics card have you in your machine?  It may be possible to get things running better if we know which driver you are using for which card.
For now try Ctrl+Alt+F1 to get to a console and then login with username and password (password won't show on screen).
Now type ```
sudo dpkg-reconfigure xserver-xorg
``` and go through the various bits until you get to graphic driver.  If you have an ati card use the ati driver, if a nvidia card use nv driver, if intel use intel driver.  If you don't know use the vesa for now and change it later.  Now continue to the end of the configuration and then reboot.  Hopefully you should have at least some form of gui and can then try to get things running properly with your hardware.

---

### Post by Touch.Code on 2008-03-27
NVidia GeForce 5200.

Just doing the command :)

---

