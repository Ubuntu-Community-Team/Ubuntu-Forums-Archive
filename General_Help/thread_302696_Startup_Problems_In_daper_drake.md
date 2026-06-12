---
title: "Startup Problems In daper drake"
date: 2006-11-19
forum: General Help
---

### Post by c00w on 2006-11-19
I did a fresh install Of 6.06 and The computer booted fine and life was happy. Then I tried to install a game called Tremulous. It was a debian file but I got it to install but it had a problem with my opengl drivers. So I downloaded the Nvidia drivers and tried to install them. It says that it cannot install while X-windows is on. It said to modify your inittab file in /etc so that it boots to run level 2 instead of three and then kill x-windows. I modified the inittab File and rebooted. The computer got to the network interface set up. Said ok and the told me it was sending the Term signal to all proceses. I fixed my inittab file with the live cd but it still refuses to actually boot up. Is there a error or log file I can view to figure out why it does not want to turn on?

---

### Post by David Corrales on 2006-11-19
You probably installed the nvidia drivers along with the restricted modules so there's a driver mismatch.If you're not using any other driver from the restricted package (like intel ipw2200 wireless), you can do the following:
First remove the repository drivers:**sudo apt-get remove nvidia-glx nvidia-kernel-common**
When it completes, run the binary driver you downloaded from Nvidia with sudo and compile the new driver.
Before rebooting make sure the *Driver* section in the file /etc/X11/xorg.conf reads **nvidia**. That's it.

---

### Post by patrick295767 on 2006-11-19
If you mess up your xorg.conf; you could try to dpkg-reconfigure xserver-xorg
and pick up the vesa one. That's will work for fixing; and installing t**he right nvidia drivers**.

---

### Post by c00w on 2006-11-19
Those ideas might work if I had acces to the shell. But I do not. How do I stop x-windows from loading and get acces to the shell? live cd or some other way?

---

### Post by c00w on 2006-11-20
bump

---

