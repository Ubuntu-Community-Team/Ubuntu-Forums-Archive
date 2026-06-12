---
title: "Private Internet Access (PIA) Icon missing after 18.04 automatic install"
date: 2018-04-30
forum: General Help
---

### Post by Old Jimma on 2018-04-30
Hi Ubuntuers:

I installed Ubuntu 18.04 from scratch on an old machine and then installed Private Internet Acciess (PIA)... and the PIA icon is not in the old machines upper bar.

The icon in the upper bar is important since it provides a way of knowing the the PIA VPN is working! :popcorn:

However, after doing an automatic upgrade of another machine on which PIA had been installed, there isn't a PIA icon in the upper bar.

How do I either uninstall PIA or figure out how to get the PIA icon in the upper bar? ;)

Thanks,
Old Old Old Jimma

---

### Post by n8461y on 2018-06-14
Ubuntu 18.04 ALT+F2, type in r, press enter.Temp fix.

---

### Post by dev1968 on 2018-10-29
I tried this and it works.
But I have to do this every time after a restart.

So how do I make this permanent?

---

### Post by twburger on 2018-11-23
Start a terminal session


Go to the applications directory: **cd ~/.local/share/applications**


Change the text file pia_manager.desktop with: [B]nano pia_manager.desktop

[/B]
adding **env XDG_CURRENT_DESKTOP=Unity**  to the setup:


Type=Application Name=Private Internet Access
Exec=**env XDG_CURRENT_DESKTOP=Unity** /home/***YourUserName***/.pia_manager/pia_manager/run.sh
Icon=/home/***YourUserName***/.pia_manager/pia_tray_files/img/***the[I]_*pia_logo.png[/I]**

The actual entry for ***the_app_logo.png*** need not be changed

After saving the changed file press Alt-F2 type r and enter to restart to desktop

---

### Post by vin0209 on 2019-02-25
Alt+F2 works temporarily. However, that directory is not correct for version v.1.0.2 of PIA.

[COLOR=#000000]adding [/COLOR]**env XDG_CURRENT_DESKTOP=Unity** basically means that you want to change the desktop environment to Unity.

Therefore the solution is:
1. go to 'Startup Application Preferences' app, which is pre-install with Ubuntu
2. select and edit 'Private Internet Acess', which you should have if you set it up to launch on start-up
3. add '**env XDG_CURRENT_DESKTOP=Unity '** in front of whatever URL that already there.
e.g: <**env XDG_CURRENT_DESKTOP=Unity /opt/****piavpn****/bin/pia-client --quiet**>
4. save -> close, then reboot to test it.

---

### Post by Cavsfan on 2019-02-28
It should install automatically if you get it from [https://www.privateinternetaccess.com/pages/download](https://www.privateinternetaccess.com/pages/download).

On my 18.04 install, just a while ago it asked me if I wanted to update to version 1.1.1 and when I clicked yes, it did it automatically.

---

