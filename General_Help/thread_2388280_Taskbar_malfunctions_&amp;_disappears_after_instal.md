---
title: "Taskbar malfunctions &amp; disappears after installing openssh-server."
date: 2018-03-31
forum: General Help
---

### Post by almostamyth on 2018-03-31
I have been using Lubuntu 17.10 for a few months and installed it on another laptop.  I wanted to network the two machines so I tried installing openssh from answer #1 here: [https://askubuntu.com/questions/156169/how-do-i-set-up-file-sharing-between-two-ubuntu-laptops-on-my-wireless-network](https://askubuntu.com/questions/156169/how-do-i-set-up-file-sharing-between-two-ubuntu-laptops-on-my-wireless-network). 

 I couldn't get it to work so I decided to uninstall openssh client and server from the two respective machines.  The client machine had no problems, but the server machine now has a taskbar problem.  When I reboot the computer the taskbar comes on briefly, it flashes a few times over about 1/2 minute, then it disappears.  While it's visible I cannot right click on it or open the start menu, but I can click the other icons that populate and they work.

It seems like something is conflicting with the taskbar and then the taskbar is shut off as a result.  System startup time is longer due to the flashing taskbar situation and the alt+f2 function is also not working.

Still no progress after uninstalling openssh with this command: "sudo apt-get purge openssh-server".  It removed it the first time, now if I run that command again it says the program is not installed.  So it apparently removed openssh but left fragments that are conflicting with the taskbar?  

I have tried to repair broken packages from the startup menu options during boot, I have also tried to repair broken packages by opening Synaptic Package Manager via terminal.  It found no broken packages.

I don't know what's going on, but since this happened in one sitting, so I know the only thing I did prior to having the problem was install and uninstall openssh-server.

Any assistance would be appreciated.

---

