---
title: "Graphics Hardware Help!?"
date: 2008-04-25
forum: General Help
---

### Post by thenellt on 2008-04-25
I just recently built myself a descent computer which is running vista but I would like to switch to ubuntu. I tried the new feature in version 8.04 and installed side be side with vista without formatting (cool feature I really like it). Whatever, my hardware question is as follows. 
              My motherboard has a Gma 3100 built on to it and that is what I was using at the time I installed  ubuntu 8.04. When I first started up, ubuntu was using a generic driver for the graphics card, so I opened graphics properties or something, and it came up with this window that had information about changing screen resolution and the window also had a tab that said something like driver. So I clicked on driver, and it was just using a generic, but you could select your graphics card from a list, so I did and restarted, and now it will not start the windows manager and it basically crashes each time I start up. So how are you supposed to go about getting drivers that work? I also would like to know how to get a driver for a Geforce 8600GT and how to install it. Thanks for any help,
*-Tasman*

---

### Post by ztheory on 2008-04-25
Describe crashing? I imagine you get the "Setting up local rc scripts", message, or the loading bar stops or freezes. On your keyboard, use Alt+Cntrl+F1 to switch to command line mode. Once in command line mode, if using an Nvidia or ATI video card, simply download EnvyNG:

#sudo apt-get envyng-core

After this, type:

#envyng -t

You will then be prompted to install the latest ATI or Nvidia drivers. Envy NG will actually find the latest drivers for your video card.

After this is done, restart X by hitting: Alt+Cntrl+Backspace... or simply reboot your computer using reboot

You can switch back and fourth from command line mode to GUI via Alt+Cntrl+F1 or F7

Hope this helps.

---

