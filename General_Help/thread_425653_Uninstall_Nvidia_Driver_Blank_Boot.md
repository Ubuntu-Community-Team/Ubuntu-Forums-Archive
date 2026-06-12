---
title: "Uninstall Nvidia Driver Blank Boot"
date: 2007-04-27
forum: General Help
---

### Post by filam on 2007-04-27
After installation of Feisty I attempted to run the compiz graphical effects. I was prompted to install nvidia drivers, which I accepted. After it was installed I rebooted the machine. The loading screen transitioned to a blank screen.

I found this in another thread by*energiya*. I edited the file (like he writes), but his explanation did not explain how to save the file. I simply held the power button to force my computer to power down. Any suggestions?

>  Alt+Ctrl+F1 and login. Open /etc/X11/xorg.conf and scroll to the "Device" section and modify "Driver" from "nvidia" to "nv" and save.
[QUOTE]sudo vim /etc/X11/xorg.conf
or use nano as an editor.
Hit Alt+Ctrl+Back Space and you will have X. You just need to uninstall the nVidia binary drivers.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=421806](http://ubuntuforums.org/showthread.php?t=421806)

---

### Post by kev000 on 2007-04-27
what is your video card?  you can change your driver back to the open source "nv" driver and see if it will work.  Make sure also that your nvidia card is supported by the driver.  Hope that helps.

---

