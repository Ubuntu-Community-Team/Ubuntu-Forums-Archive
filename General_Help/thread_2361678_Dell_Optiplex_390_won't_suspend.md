---
title: "Dell Optiplex 390 won't suspend"
date: 2017-05-19
forum: General Help
---

### Post by patgreen on 2017-05-19
I'm new to Linux. I recently installed Ubuntu and it works fine with all the programs that I want but I can't get it to sleep or suspend.
I'm using a Dell Optiplex 390 desktop computer which works fine and will sleep with Windows 10.
The suspend problem happens with every Linux distro that I've tried, installed or live CD.
If I try to suspend the computer it goes blank for a second and starts back up. I've disconnected everything from the computer except power mouse and keyboard but it won't suspend. I've updated the Bios and tried different sleep settings in the bios.
I'm not having any luck searching for solutions as all the answers seem to relate to problems with computers that won't wake from suspend.

---

### Post by LastDino on 2017-05-19
Which version of Ubuntu? 

post out put of

> uname -r

and out put of

> lsb_release -sr

from your Ubuntu terminal

---

### Post by patgreen on 2017-05-19
pat@pat-OptiPlex-390:~$ uname -r 
4.8.0-36-generic
pat@pat-OptiPlex-390:~$ lsb_release -sr 
16.04
pat@pat-OptiPlex-390:~$

---

### Post by LastDino on 2017-05-19
Can you try this?

Open terminal and type this

> sudo vi /etc/systemd/logind.conf
  
Then uncomment the line (remove the beginning #) containing 'HandleLidSwitchDocked=ignore' and changed the value to be:

  > HandleLidSwitchDocked=suspend
  
Then reboot

Do keep backup of the files just in case

---

### Post by patgreen on 2017-05-19
How to I get to a terminal that i can edit?
I can edit in the terminal but I don't know how to save it?

---

### Post by LastDino on 2017-05-19
Here is easy guide
[https://www.cyberciti.biz/faq/linux-unix-vim-save-and-quit-command/](https://www.cyberciti.biz/faq/linux-unix-vim-save-and-quit-command/)

Doing this should enable you to put your machine in suspend mode when lid is closed..

---

### Post by patgreen on 2017-05-19
I made the changes but it still won't suspend
This is a desktop so there is no lid to close

---

### Post by LastDino on 2017-05-19
I think I missed that desktop part, sorry about that.


Above instructions were meant for laptop. Really sorry mate. Lets wait for someone else for new ideas

---

### Post by patgreen on 2017-05-19
Thanks for trying.

---

