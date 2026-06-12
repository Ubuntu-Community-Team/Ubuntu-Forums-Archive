---
title: "Burg Splash Screen"
date: 2016-09-03
forum: General Help
---

### Post by Quarkrad on 2016-09-03
I'm running Mate 16.04, installed from an iso (I also dual boot with win10) - I have also installed 16.04, in virtualbox using the same iso, on the same machine.  I prefer the Burg splash screen to the standard Mate splash and installed Burg (note - maybe wrong, but it seems you cannot install super-boot-manager yet in 16.04.  Although there is an Askubuntu that gives details of how to do it - I cannot get it to work).  So .... having installed Burg on my main machine it still boots to the (Plymouth) standard Mate screen - on my virtual machine, I installed Burg the same way, and it does indeed boot to the Burg boot screen.  (One difference between the two environments is that my main machine dual boots but the virtual one doesn't - but I would not have thought that is an issue here).  Why does the virtual machine boot to Burg but my main machine not?   I can run **sudo burg-emu** on my main machine and I get the burg splash emulation - and all the various files appear to be in the right place. My naive thought process is that there is a config file somewhere that points to the boot process and on my main machine it is (still) pointing to the standard Mate (plymouth) screen - whereas on my virtual machine the config file is pointing to burg; but I do not where this is, it it works this way.  The other (might be relevant) difference is that my main machine boots uefi and the virtual machine bios.  Any pointers appreciated.

---

