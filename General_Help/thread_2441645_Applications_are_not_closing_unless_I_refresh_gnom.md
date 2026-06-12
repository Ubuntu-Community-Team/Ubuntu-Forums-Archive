---
title: "Applications are not closing unless I refresh gnome-shell, system crashes"
date: 2020-04-25
forum: General Help
---

### Post by tubiflex on 2020-04-25
Installed 19.04 last week and updated to 20.04.  

My system is having issues where when I close an application, it seems to continue running in gnome-shell. The application remains open in the background or  sometimes on the dock. If I right-click the application on the dock to  use the Quit function, gnome-shell completely freezes and I need to  Ctrl+Alt+F3, login and reboot the computer.

 In addition,  sometime when I open an application a 'ghost' application opens in the  dock. For example, I open the terminal and VLC opens the dock, if I  right-click on the VLC icon my system will freeze up.

The only thing that seems to remove these 'ghost' applications as by Alt+F2 + r (refreshing gnome-shell).


[LIST]
[*]OS: Ubuntu 20.04 LTS x86_64 
[*]Kernel: 5.4.0-26-generic 
[*]Uptime: 22 mins 
[*]Packages: 1742 (dpkg), 12 (snap) 
[*]Shell: bash 5.0.16 
[*]Resolution: 2560x1440, 2560x1440 
[*]DE: GNOME 
[*]WM: Mutter 
[*]WM Theme: Adwaita 
[*]Theme: Yaru-dark [GTK2/3] 
[*]Icons: Yaru [GTK2/3] 
[*]Terminal: gnome-terminal 
[*] CPU: AMD Ryzen 9 3950X (32) @ 3.500GHz 
[*] GPU: NVIDIA GeForce GTX 1080 Ti 
[*] Memory: 7351MiB / 32092MiB 
[*]Using ZFS file system 
[/LIST]

**Installed shell extensions**
activities-config@nls1729                             
[EMAIL="noannoyance@daase.net"]noannoyance@daase.net[/EMAIL]
[EMAIL="caffeine@patapon.info"]caffeine@patapon.info[/EMAIL]                                 
[EMAIL="pop-shell@system76.com"]pop-shell@system76.com[/EMAIL]
[EMAIL="dash-to-dock@micxgx.gmail.com"]dash-to-dock@micxgx.gmail.com[/EMAIL]                         
[EMAIL="remove-dropdown-arrows@mpdeimos.com"]remove-dropdown-arrows@mpdeimos.com[/EMAIL]
[EMAIL="drive-menu@gnome-shell-extensions.gcampax.github.com"]drive-menu@gnome-shell-extensions.gcampax.github.com[/EMAIL]  
[EMAIL="sound-output-device-chooser@kgshank.net"]sound-output-device-chooser@kgshank.net[/EMAIL]
[EMAIL="drop-down-terminal-x@bigbn.pro"]drop-down-terminal-x@bigbn.pro[/EMAIL]                        
[EMAIL="status-area-horizontal-spacing@mathematical.coffee.gmail.com"]status-area-horizontal-spacing@mathematical.coffee.gmail.com[/EMAIL]
[EMAIL="gnome-shell-screenshot@ttll.de"]gnome-shell-screenshot@ttll.de[/EMAIL]                        
[EMAIL="transparent-window-moving@noobsai.github.com"]transparent-window-moving@noobsai.github.com[/EMAIL]
[EMAIL="impatience@gfxmonk.net"]impatience@gfxmonk.net[/EMAIL]

---

### Post by CelticWarrior on 2020-04-25
```
GPU: NVIDIA GeForce GTX 1080 Ti
``` needs the latest Nvidia drivers.
Please open Additional Drivers, select and apply the recommended version and reboot.

---

### Post by tubiflex on 2020-04-25
I'm using the latest Nvidia drivers

---

### Post by CelticWarrior on 2020-04-25
If not disabled already, disable Secure Boot in UEFI. And maybe other settings too.

---

### Post by tubiflex on 2020-04-25
Thanks, I disabled secure boot. 

Issue just happened again. I opened the Nvidia X server settings app, closed it but it still appears in the dock. I know if I right click it, gnome-shell will crash.

I right clicked and it crashed again. I started removing extensions.

---

### Post by tubiflex on 2020-04-25
I think the problem is related to the pop shell extension ([https://github.com/pop-os/shell](https://github.com/pop-os/shell)). It may be conflicting with Dash-to-Dock or another extension. 

So far no issues since I removed it.

---

