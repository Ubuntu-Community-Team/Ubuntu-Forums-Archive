---
title: "after nvidea driver install, xconfig not there"
date: 2007-02-04
forum: General Help
---

### Post by mad2smile on 2007-02-04
im a newbie.  today i installed Ubuntu 6.10, updated repositories and installed some programs.  i also installed the xubuntu-desktop package and the kde package.  i was loving every minute of it... ubuntu rocks!

everything was going great... until i tried to install a pci nvidea video card.  with the card in the pci slot, the screen would not display anything, no matter if it was plugged into the vga port on the pci card or the vga port built in to the motherboard.  so heres what i did... i removed the pci card, booted into xubuntu and installed an nvidea driver, following these instructions: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29").

now i cant boot into graphical mode (error messages), and when i boot into the terminal and enter sudo dpkg-reconfigure xserver-xorg, it says that xserver-org isnt on my computer (or isnt installed or something like that).  

what should i do?  is there a way to remove the nvidea driver without screwing everything up?

---

### Post by sarc on 2007-02-04
Seach many posts on this forum re. nvidia.  I had same problem until I:
- Donwloaded the LATEST (NOT LEGACY) nvidia driver from Synaptics
- Manually edited Xorg to change the driver name from nv to nvidia

My biggest mistake was to follow the instructions on the nvidia website - cost me 3 days of work.

 Do your search

---

