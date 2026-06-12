---
title: "Boot issue after bad command"
date: 2020-05-19
forum: General Help
---

### Post by thomassinn on 2020-05-19
I have ubuntu 18.04 on a dell xps computer.

On boot my ubuntu load and then dispalys:
"UBUNTU: clean, 920605/30883840 files, 41324269/123523840 blocks"
And stay stuck here. 
I probably broke something, I did the folowing before rebooting:

I was trying to play mass effect 3 on my computer with lutris.
Lutris showed me the message "vulkan library not found for i386 architecture"
So I followed instruction for Intel on ubuntu 18.04 (I cave Intel uhd 620 graphic card) at
[https://github.com/lutris/docs/blob/master/InstallingDrivers.md](https://github.com/lutris/docs/blob/master/InstallingDrivers.md)
This implies:
sudo add-apt-repository ppa:kisak/kisak-mesa
sudo dpkg --add-architecture i386
sudo apt update && sudo apt upgrade
sudo apt install libgl1-mesa-glx:i386 libgl1-mesa-dri:i386

I may have add:
sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
But I'm not sure 

I would like to have my ubuntu working.
It's not a problem for me to loose files if I have To load a previous save of my ubuntu but I don't know how to do that.

---

### Post by TheFu on 2020-05-19
> **thomassinn said:**
>  
It's not a problem for me to loose files if I have To load a previous save of my ubuntu but I don't know how to do that.

Can't help with anything else, but if you didn't specifically setup a backup - that's what Unix people call "save" - then there isn't any prior version for you to restore.

Backups are critical.
Users are expected to set those up.
There isn't any "automatic" method that just does it ... well if you have 20.04 with experimental ZFS, then a snapshot is taken before every package install, but that will probably run the storage out eventually if there aren't cleanup processes.

Do you have 20.04?  Says 18.04 above.
Did you choose the "experimental" ZFS install method?  I did a ZFS install with a 20.04 desktop just to see it.  All sorts of things just felt wrong, so I wiped it and started over using LVM. ;)   I need to become much more comfortable with ZFS just for data before choosing to have the OS using it.

Sorry, I'm not any help.

---

