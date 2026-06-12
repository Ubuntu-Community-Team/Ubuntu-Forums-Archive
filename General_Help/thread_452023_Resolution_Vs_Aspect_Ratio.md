---
title: "Resolution Vs Aspect Ratio"
date: 2007-05-22
forum: General Help
---

### Post by TwoEdgeXtreme on 2007-05-22
I have a 51 inch sony projection hd tv (model# ws520). It is connected to an nvidia geforce 7300 video graphics card PCIE architecture. 
The problem is I am only given 2 resolutions, one being 800x600 and the other 600x480 and when I boot to windows the nvidia driver has to use a non standard resolution 1152x648.
Correct me if I'm wrong but from my understanding tvs use "aspect ratio 4:3" and computers use "resolution 1200x800".
Is there a workaround for this issue? (Step by step instructions for a complete newbie would be extremely appreciated.)

Using ubuntu I am unable to see the top and bottom of the desktop which makes it pretty much a guessing game as to what I am doing at any given moment.

---

### Post by magicfab on 2007-05-23
You will most probably need to install the non-free (proprietary, but gratis) nVidia drivers. In Ubuntu Feisty, go to System > Administration > Restricted Drivers Manager and you should be able to enable them there.

Once the nVidia driver has been enabled, you may have to logout - login again or restart the X (graphics) server using CTRL-ALT-BACKSPACE. Then install the nvidia-settings package by using Synpaptic (System > Administration > Synaptic Package Manager ) and searching + choosing + applying for the nvidia-settings package to be installed. 

For some reason this tool is not set up in the menu of Ubuntu Feisty, so you need to open a terminal window and type "nvidia-settings<enter>" then you should see the nVidia setting dialog.

---

