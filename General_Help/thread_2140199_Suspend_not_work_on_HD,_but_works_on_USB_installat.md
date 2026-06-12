---
title: "Suspend not work on HD, but works on USB installation"
date: 2013-04-28
forum: General Help
---

### Post by jbarr on 2013-04-28
I am running Ubuntu 12.04 on an Asus u43jc with a NVIDIA® GeForce® 310M graphics card. When I click on suspend, the computer does not fully suspend, but will disconnect networking, then reconnect networking. 

Oddly, I have an installation of 12.04 on a USB drive that, when booted on the same computer, will suspend and resume just fine any number of times.

I have tried copying the USB installation files from etc/pm/sleep.d to the HD installation, but after booting from the HD, the computer will suspend, but upon resume the fan will go to high speed and will blow very hot air. The only solution at this point is to shut down the computer. Upon rebooting from the HD, all is back to normal.

Files on the USB installation are 10_grub-common, 10_unattended-upgrades-hibernate, and novatel_3g_suspend.

From what I have read, I suspect the nVidia graphics card is somehow to blame. How can I get this computer to suspend and resume normally?

---

