---
title: "Install as Microsoft Virtual PC"
date: 2007-10-11
forum: General Help
---

### Post by atkinsm on 2007-10-11
I installed Unbuntu successfully as a virtual PC under the latest Microsoft Virtual PC software.

Everything seemed OK until I was booting up after the install.  I had chosen a screen resolution of 1024 x 768, and when I boot up again Virtual PC could not display in Fullscreen mode, and the display was distorted.  is there any way that I can change the screen resolution without logging on to the GUI?  I could do a fresh install, but would prefer not to.

---

### Post by vapore0n on 2007-10-11
[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004?highlight=%28virtualpc%29](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004?highlight=%28virtualpc%29)

Step 1: Boot Live CD, press F6 (Other Options)
Step 2: Go near the end of the line and remove the word splash, then press Enter.
Step 3: After Ubuntu 6.10 boots, Press Crtl-Alt-F1 to get to a command line interface.
Step 4: Type in the following command to reset defaultdepth from 24 to 16:

sudo sed -e 's/DefaultDepth.*24/DefaultDepth 16/g' -i /etc/X11/xorg.conf

Step 5: Press Ctrl-Alt-F7 to return to the Ubunto Desktop.
Step 6: Press Ctrl-Alt-Backspace to reload the Ubunto Desktop.
Step 7: Graphics should be adjusted, and now you can perform an installation under VPC.

---

