---
title: "Update breaking my Ubuntu installation"
date: 2008-01-26
forum: General Help
---

### Post by scweston on 2008-01-26
Hi,

I'm having a serious problem with installing all the updates after a fresh install of Ubuntu Gutsy 7.10 64bit

After I do a fresh install (which goes perfectly smoothly and gutsy runs fine after) I try to install all the updates through the update manager which pops up a bubble after the installation telling me there are updates for my system.  As I understand it is recommended that I install these updates.

However, after the updates have been installed and I have rebooted, the computer just hangs as I'm logging in. I can press CTRL+ALT+Backspace to get back to the login screen and I try to change the session to 'Failsafe GNOME', but still it hangs.

I assume it is one of the updates that is causing this... is there any way I can find out which one to stop it updating?  (It installs 184 updates after a fresh install)

My hardware is below if that helps...

AMD Athlon 64 x2 Dual Core Processor 4200+
FoxConn NF4SK8AA motherboard
Leadtek GeForce 7600 GS 256MB PCI-E graphics
Hauppauge WinTV Nova-T 500 Dual DVB-T card
2GB DDR PC3200 400MHz RAM
160Gb drive for Vista
500Gb drive for Ubuntu (to include mythtv later on)

Any help would be appreciated.

Stephen

---

### Post by eggdeng on 2008-01-26
The most likely candidate is a kernel update. But you should still be able to login to the original kernel by using the arrow keys to choose it from the boot menu. Other than that, it could be an xorg update breaking your graphics drivers.
My personal rule of thumb is to avoid any update with the word linux in the name unless I have a good reason for installing it.

---

