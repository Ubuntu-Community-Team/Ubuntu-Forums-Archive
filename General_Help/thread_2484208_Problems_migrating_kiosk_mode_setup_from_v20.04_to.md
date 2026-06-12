---
title: "Problems migrating kiosk mode setup from v20.04 to v22.04 (not snap cgroup)"
date: 2023-02-20
forum: General Help
---

### Post by marcelgl on 2023-02-20
I have a headless setup with Ubuntu server v20.04, which starts Chromium browser in kiosk mode at startup.  
It is not using a Window manager. The user 'openhab' is a non-root and non-login user. 

A systemd service calls 'startx' 

```

[Unit]
Description=Openhab Kiosk Launcher
After=systemd-user-sessions.service


[Service]
User=openhab
ExecStart=/usr/bin/startx
Restart=always


[Install]
WantedBy=multi-user.target

```

xinitrc (in the openhab user home directory) performs some settings for orientation and starts Chromium in kiosk mode. 

This setup works as expected. Now I am trying to duplicate this configuration (on identical hardware) but based on a vanilla install 
of Ubuntu 22.04.1 and I am unable to get it working. 

The user is the the same, permissions are the same. 'xinitrc' and 'Xwrapper.config' are a copy from the other system. 
When looking into the log I see 2 errors, which I do not see with the working setup: 


```

Feb 20 14:25:29 srv5 startx[2772]: (==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 20 14:25:29 2023
Feb 20 14:25:29 srv5 startx[2772]: (==) Using system config directory "/usr/share/X11/xorg.conf.d"
Feb 20 14:25:40 srv5 startx[2891]: sudo: a terminal is required to read the password; either use the -S option to read from standard input or configure an askpass helper  <===  Not with working v20.04 system
Feb 20 14:25:40 srv5 startx[2891]: sudo: a password is required
Feb 20 14:25:45 srv5 startx[2793]: /system.slice/openhab-kiosk.service is not a snap cgroup           <===  Not with working v20.04 system
Feb 20 14:25:45 srv5 startx[2771]: xinit: connection to X server lost
Feb 20 14:25:45 srv5 startx[2771]: #015
Feb 20 14:25:46 srv5 startx[2771]: waiting for X server to shut down

```
 
Especially the "is not a snap cgroup" error seems to happen a lot, but I couldn't find a solution for this. 

Anyone a suggestion how to solve this ?

---

### Post by MAFoElffen on 2023-02-20
20.04 LTS, Firefox was installed from APT. On 22.04 LTS, FireFox default install is a Snap app.

My suggest would be to remove Firefox as a Snap and install from the Mozilla PPA: [https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22](https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22)

---

### Post by marcelgl on 2023-02-20
Thanks for the reply. 
I was however using Chromium and not Firefox, but indeed I will see if I can find a "non snap" package. 
For a test I replaced Chromium by xclock and that one is displayed after system boot, so it seems the issues are really related to Chromium.

---

