---
title: "Xubuntu Loads but no icons or any thing"
date: 2014-07-19
forum: General Help
---

### Post by ravisuncar on 2014-07-19
I have install Xubuntu 14.04 on my laptop and it was working good for the past few days. Today when i started by system, i got my login page and after i entered my User Id and Pass i got into a blank screen. Except for the wallpaper and my icon there is nothing. I cant even right click on use short cuts to start terminal. I logged into other users and everything is the same. I had cinnamon installed and it loads up file (few sec delay). Is there a way to fix this issue?

---

### Post by Jesse_Campton on 2014-07-19
Can you Ctrl+Alt+F1 ? Enter Username then Password...```
sudo apt-get update && sudo apt-get upgrade
``` Assuming your using Default Xubuntu ```
[FONT=Ubuntu Mono]sudo restart lightdm[/FONT]
``` then hit Ctrl+Alt+F7 ?

---

### Post by Toz on 2014-07-19
Sounds like your sessions cache is corrupt. Go to Settings Manager >> Sessions and Startup >> Sessions tab and click on the "Clear saved sessions" button. Then you need to log out and back in again, but when logging out, make sure to uncheck the "Save session for future logins" checkbox.

---

### Post by ravisuncar on 2014-07-19
Thanks for your replies. I have able to fix it by

1. Log into Gnome DE[SIZE=2]
2. Removed XFCE completely 
3.sudo apt-get install xubuntu-desktop gksu leafpad synaptic
4. logged out and logged into Xfce DE
5.sudo apt-get remove nautilus gnome-power-manager gnome-screensaver gnome-termina* gnome-pane* gnome-applet* gnome-bluetooth gnome-desktop* gnome-sessio* gnome-user* gnome-shell-common compiz compiz* unity unity* hud zeitgeist zeitgeist* python-zeitgeist libzeitgeist* activity-log-manager-common gnome-control-center gnome-screenshot overlay-scrollba* && sudo apt-get install xubuntu-community-wallpapers && sudo apt-get autoremove
6. So i have a fresh XFCE with no issue.[/SIZE]

---

