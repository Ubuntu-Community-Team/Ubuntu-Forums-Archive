---
title: "Black screen using Nvidia Geforce 340"
date: 2020-04-25
forum: General Help
---

### Post by rwfnetworking on 2020-04-25
Fresh install of Ubuntu 20.04 on Dell Vostro 3500. Initially it will use the Stock Nouveau driver, but that only supports 1024x768. On first update the Nvidia Geforce 340 driver is listed in additional drivers. I select that and reboot. I just get a black screen with a flashing cursor. I can access all toys, but tty7 is not running the gui. Manually running "startx" terminates a few seconds after I enter it. 

Any suggestions?

I can run Zorin, Linux Mint with the proprietary drivers ok. .....

Robert

---

### Post by linux4me on 2020-04-26
You don't mention the method you used to do the installation, but I'm impressed you got the Vostro to run nouveau. In the [release notes]("https://wiki.ubuntu.com/FocalFossa/ReleaseNotes#Installer_and_live_session"), it says:
> 
Systems with an nVidia graphics card boot the live session by default with the open source video driver 'nouveau'. On some hardware this driver may crash which results in a freeze of the graphical session of the installer. If it happens, on the boot menu, select a 'Safe graphics mode' entry. Then in the installer, on the 'Preparing to install ...' page, select 'Install third party software ...' and continue. This option will install the nVidia proprietary drivers on the target system. Upon installation the proprietary drivers for your card will be loaded and the graphical session should work properly with optimized drivers. (1822026) (1871562) 

With my Inspiron 1567, which has hybrid Intel/Nvidia graphics as I believe the Vostro has, I had to follow those directions in order to get 20.04 to install, which it did flawlessly once I followed them. I wonder if it could be that you're missing the nvidia Prime package, or something similar that's required for the funky hybrid graphics that Dell uses? If it were me, I think I'd re-install using the directions in the release notes if that's not the way you installed initially and see if it works.

---

