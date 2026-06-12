---
title: "Offical ATI drivers chrash/Edgy Eft"
date: 2006-10-31
forum: General Help
---

### Post by svencbir on 2006-10-31
I'm currently running Ubuntu 6.10 and have Ati Radeon 9550 Agp.
I have tried to install offical ATI drivers.

I started with:
sudo apt-get update
sudo apt-get install xorg-driver-fglrx

than continued with:
sudo depmod -a

To do the configurationf for my grapihcal card i entered: 
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Then I changed file /etc/X11/xorg.conf... I have added thease lines to the end of the file:
Section "Extensions"
Option "Composite" "0"
EndSection

Because I wanted to test wheter my installation was successful or not i ran fglrxinfo.... A soon i had ran the fglrxinfo my screen went black with notice - no input signal . Since then I can't run  graphical enviroment.As soon the error happened, i restarted my computer and went into recovery mode and deleted the changes previously added in /etc/X11/xorg.conf But it didn't help. What should I do to repair my ubuntu?

---

