---
title: "Installing my GFX card driver."
date: 2008-05-16
forum: General Help
---

### Post by Syroco on 2008-05-16
I found a website with good steps.  I just don't understand it:(  Can someone make his steps a little more user friendly? Thx

I downloaded the new beta driver that supports my card, and I found a website to help me install it. It gives me these steps, but I have no idea what he's talking about. I tried his commands in terminal and they didn't do anything, invalid commands, or not found, etc.

Can someone give me a bit more detailed walkthrough? Thanks

1) Make sure that you don't have any of the following packages installed on the system: nvidia-glx or nvidia-glx-new
2) If any of these files exist, delete them: /etc/init.d/nvidia-glx, /etc/init.d/nvidia-kernel, and /lib/linux-restricted-modules/.nvidia_new_installed
2) Install the packages for some of the more common development tools if they aren't already: gcc, linux-headers, pkg-config, and xserver-xorg-dev
3) Modify the /etc/default/linux-restricted-modules file and add the following line to the bottom of it: DISABLED_MODULES="nv nvidia_new"
4) Download the latest driver from NVIDIA. I had to click on the "Beta and Archived Drivers" link to find version 173.08, which said that it added support for the GeForce 9600 GT GPU. Later version will likely work too.
5) From a root console window (CTRL-ALT-F1), run "/etc/init.d/kdm stop" if you are using KDE, or "/etc/init.d/gdm stop" if you are running GNOME.
6) Execute the binary driver that you downloaded from step 4 above. It will walk you through a few screens necessary for setting up the driver on the system. When it asks if you want it to auto configure your xserver, choose "yes."
7) If everything was successful, you might want to edit your /etc/X11/xorg.conf file and check the "Device" section. If you don't see any mention of "AddARGBVisuals" or "AddARGBGLXVisuals", add the following lines to that section:
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
8) You can start up your xserver again. Run "/etc/init.d/kdm start" if you are using KDE or "/etc/init.d/gdm start" if you are running GNOME.

---

### Post by Syroco on 2008-05-16
Please..anyone.

---

