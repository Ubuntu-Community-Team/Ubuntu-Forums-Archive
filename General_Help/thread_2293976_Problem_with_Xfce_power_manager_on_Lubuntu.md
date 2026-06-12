---
title: "Problem with Xfce power manager on Lubuntu"
date: 2015-09-08
forum: General Help
---

### Post by ross4 on 2015-09-08
I am running Lubuntu Saucy Salamander (alternate install) on a very old laptop (see below). When I leave the machine running for a while, the screen goes blank and then becomes frozen at the blank screen. I thought I had fixed this through choosing the correct options in Xfce power manager. However. the problem returned and so I went back to try some other options. When I went to the Xfce PM tab "General", I unchecked the option "Monitor power management control". This resulted in the keyboard & mouse becoming almost completely frozen. I say almost because while the mouse cursor would not move & ctrl-alt-T will NOT open a terminal, "Raising Elephants..." etc. will reboot it and so will alt-sys-b.

When I reboot, I can sign on as guest and everything is fine. I can even open a terminal and then su to my usual ID and there is no problem at the command line level but starting the GUI of the power manager from the command line results in everything freezing up again.

Can anybody suggest how I can undo / or reset the Xfce power manager settings for my usual ID? Hoping someone can help. I don't want to re-install Lubuntu for a third time. Takes a looong time on that old machine.

My system:
   Toshiba Laptop Satellite 5000

 Intel Pentium III processor

1.10 GHz, 512 MB of         RAM, available hard  drive space 26.7 GB
 Video Card: NVIDIA GeForce4 440 Go

---

### Post by mörgæs on 2015-09-09
Saucy Salamander (13.10) is out of support so you should indeed reinstall. I recommend 15.04.

A [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") takes less time and bandwidth to download.

---

