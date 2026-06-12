---
title: "Having problems with Ubuntu and my graphics card."
date: 2007-04-29
forum: General Help
---

### Post by totes on 2007-04-29
Hi guys, just installed Ubuntu Feisty, and wanna let you know from the beginning I'm a total Linux newb. Well, after the rather speedy installation, I rebooted my computer to be greeted with Xserver or Xorg saying it failed to load. After reading the error message, it read that the nvdia kernel module had failed to load. Someone suggested  I use the command 'dpkg-reconfigure xserver-xorg' and after going through the screens, I managed to load up the Ubuntu login screen. 
I noticed the screen resolution was my native (1440x990 @ 60Hz) and was suprised it had set it, right off the bat. However, once I got into the desktop, the resolution changed to a more fuzzy 1024x768. Going to Preferences > Resolution, it only offered 1024 and lower (800, 640) and only displayed 50Hz for a refresh rate. I have tried editing several times the xorg.conf to no avail and have come to the conclusion I have totally borked it. I also do not know how to do a clean install of the new nvidia drivers (9755), as I'm told the ones included with the cd are terrible. 

What I'd like to know is how to restore the Xorg.conf to its original state, optimise it by getting rid of the useless config inputs, install the new Nvidia drivers and get them to be recognised by Xserver, and most importantly restore my native resolution. Bear in mind, I'm totally new to this OS, which is pleasantly intuitive, so do go ahead and explain this to me as though I'm a complete inebriate. I don't mind being patronised at this point :)

My specs are: Dell Inspiron 9400/E1705
                       Core2Duo 1.83 Ghz
                       1024 Mb of DDR2 RAM
                      Nvidia Geforce Go 7900 GS

---

### Post by orb9220 on 2007-04-29
Did you try Envy script ? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  

It works for me GUI in menu or even if an update breaks x type envy in command line and it fixes it for me.

---

