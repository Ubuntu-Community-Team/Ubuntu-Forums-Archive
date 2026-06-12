---
title: "Kodi auto-start"
date: 2020-07-17
forum: General Help
---

### Post by SoronZero on 2020-07-17
Hello all I need some help with my Ubuntu Server 16.x to auto-start Kodi/XBMC, long story I made the server with 14.x and it auto-started fine, upgraded to 15.x had issues with the sound system that I have fixed, now it is currently on 16.x (with no upgrade path at the moment, as I cant wipe and load new OS due to movie library on same hdd) and here is where it gets interesting as I have been trying to fix this for awhile now and i'm at my wits end.

The problem is Kodi/XBMC will not auto-start at boot using the script I have used for years, yet if I login as root or use sudo to manually type the contents of the script and execute it runs fine, I can execute the script manually as root and it runs fine, but when I put the script to be called in rc.local (or even the contents of it) it does not auto-start, just sits at a login prompt. I posted the question on /r/Linux last night on reddit and they just removed the post (even though there were other posts asking for help for other things), any input would be greatly appreciated!

---

### Post by ActionParsnip on 2020-07-17
What script do you run to start the applicaition?

---

### Post by SoronZero on 2020-07-17
Sorry for the delay, I was at work when I posted this, this is what is in the main script when it starts up just titled "XboxMediaCenter"  in home

> 
#!/bin/sh

# Start XBMC

export PATH=/usr/bin:/usr/local/bin:/usr/bin/X11
export HOME=/root

case "$1" in
start) echo -n "Starting XboxMediaCenter"

setterm -blank 0

/usr/local/bin/XboxMediaCenter.sh

esac
exit 0


This is the contents of the /usr/local/bin/XboxMediaCenter.sh file

> #!/bin/bash

#Script to start x server and XBMC

#/usr/bin/X11/xinit /usr/bin/X11/xbmc-standalone -q &
/usr/bin/X11/xinit /usr/bin/kodi -q & irexec -d /root/.lircrc &


Using the one in the home directory to call the other one doesnt really do anything, but calling the /usr/local/bin/XboxMediaCenter.sh file or typing its contents works to execute Kodi but will not work in rc.local to auto-start.

---

### Post by ActionParsnip on 2020-07-18
Are you using the default Ubuntu desktop environment? There is an option in settings to add startup items. It basically makes a ".desktop" file in $HOME/.config/autostart (I think) in the normal desktop file manner.

---

### Post by TheFu on 2020-07-18
If you want kodi to autostart from boot, the kodi wiki has the needed steps. It requires setting up 'autologin'.  
[https://kodi.wiki/view/HOW-TO:HOW-TO:Autostart_Kodi_for_Linux](https://kodi.wiki/view/HOW-TO:HOW-TO:Autostart_Kodi_for_Linux)

Kodi isn't a normal end-user application when run in this way.

---

### Post by SoronZero on 2020-07-18
> Are you using the default Ubuntu desktop environment? There is an option in settings to add startup items. It basically makes a ".desktop" file in $HOME/.config/autostart (I think) in the normal desktop file manner.
I am using the server version of ubuntu, I have no desktop environment, CLI only.

> If you want kodi to autostart from boot, the kodi wiki has the needed steps. It requires setting up 'autologin'.
[https://kodi.wiki/view/HOW-TO:HOW-TO...Kodi_for_Linux](https://kodi.wiki/view/HOW-TO:HOW-TO...Kodi_for_Linux)

I will take a look at this again as steps may have changed since I built it years ago (when it was still XBMC), the components are all there and they work if you login and either execute the script or manually type in the commands either as root or sudo, but does not work when autostarted which is the weird thing, that guide does specify "this page assumes booting into a desktop OS, not a server distro." which is what I have as I have no desktop environment but it does give me a place to start, step 4 should be a good starting place for me, I will let you know later on today if it works.

---

### Post by SoronZero on 2020-07-18
Ok finally got it to work again, I have no window manager just the X-Window system, the guide didn't really help as it already works if I just start it manually and nothing wrong with the script so no additional components needed to be installed and none of their scripts seemed to work for me, what worked for me was to create a systemd service to start it, (as I thought nothing else was wrong, only how it got called on boot)  so here is the steps I did to fix it in case anyone else has this problem.

I created a file in /etc/systemd/system named kodi.service with the contents below:

> 
[Unit]
Description=Kodi Media Center
After=systemd-user-sessions.service sound.target

[Service]
User=root
Group=root
Type=oneshot
ExecStart=/usr/local/bin/XboxMediaCenter.sh

[Install]
WantedBy=multi-user.target


then I reloaded the daemon using "sudo systemctl daemon-reload"
then I enabled it using "sudo systemctl enable kodi.service"
Finally I rebooted and it went right in! Thanks for the help for everyone involved!

---

### Post by TheFu on 2020-07-18
Happy you found a working solution, but 

Running any GUI programs as root is a really, really, really, bad idea.  Logging in as root is a bad idea on Ubuntu. There are side effects, usually undesirable, when doing either.  Did you really intend to run Kodi as root?  Not a great idea.

But it is your box. Do as you like.

---

