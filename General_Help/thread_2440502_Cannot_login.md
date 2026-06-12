---
title: "Cannot login"
date: 2020-04-11
forum: General Help
---

### Post by lucaskar on 2020-04-11
After a reboot, Ubuntu booted into tty1.
I wasn’t able to start the graphics so I reconfigured it to use lightdm.

When I boot now, I get the login graphics however I always receive a “Failure to start session” after entering my password. I’m not able to open a terminal window at all using ctrl + alt + Fx.

---

### Post by grahammechanical on 2020-04-12
Ubuntu has a recovery mode. Do you get a Grub boot menu? If not, then towards the end of the loading of the motherboard BIOS/UEFI settings screen press the left shift key for a BIOS mother board (older computers) or the Esc key for newer UEFI computers. You will need to press the Esc key several times. That should bring up the Grub menu.

At the Grub menu you can select to load an older Linux kernel or Advanced options for Ubuntu which will give you a recovery mode menu.

Resume = Resume normal boot but without video driver activation.
Networking = Setting up a connection to the router. Necessary if wanting to access the internet to update or install packages.
Root = A Root shell where you can run commands (sudo & password not required). To exit the root shell type "exit" and you will get back to the recovery menu and you can use Resume to see if you can get a desktop. Once at a desktop you can shutdown and reboot as normal and may be get to a desktop with an activated video driver.

You might already know this as you say that you reconfigured it to use LightDM. You might want to consider using recovery mode to back up your data in case a re-install proves to be the easiest way to fix this problem.

You could try updating at the root prompt.

Regards.

---

