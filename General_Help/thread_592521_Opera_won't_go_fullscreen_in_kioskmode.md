---
title: "Opera won't go fullscreen in kioskmode"
date: 2007-10-26
forum: General Help
---

### Post by godrox on 2007-10-26
I'm running Xubuntu and am trying to turn it into a kiosk. Opera kiosk mode seems to be exactly what I need, so I installed it through Synaptic. The first time I ran it in kioskmode just to see what it looked like and it worked fine. So I closed it, made the customizations I wanted and then tried to run it again, but now it won't go fullscreen or apply any of the other switches I included. In normal Opera mode, I can hit F11 and it'll go fullscreen, but in kiosk mode it won't. I even removed all my switches and just went with "opera -kioskmode" and it still won't do it anymore. I've tried uninstalling and reinstalling Opera, but apparently it still keeps all of your previous settings. Any ideas on how to fix this?

---

### Post by pcadic on 2008-02-14
> **godrox said:**
> I'm running Xubuntu and am trying to turn it into a kiosk. Opera kiosk mode seems to be exactly what I need, so I installed it through Synaptic. The first time I ran it in kioskmode just to see what it looked like and it worked fine. So I closed it, made the customizations I wanted and then tried to run it again, but now it won't go fullscreen or apply any of the other switches I included. In normal Opera mode, I can hit F11 and it'll go fullscreen, but in kiosk mode it won't. I even removed all my switches and just went with "opera -kioskmode" and it still won't do it anymore. I've tried uninstalling and reinstalling Opera, but apparently it still keeps all of your previous settings. Any ideas on how to fix this?


I solved the problem 5 minutes ago
Use the save session option

Start opera in classical mode, go to preferences and select START USING SAVED SESSION mode
Go to your default home page and save  FILE > SESSION > SAVE SESSION

You may now open opera in fullscreen in kioskmode.

(LOL: I did not ever think I would give an advise on a ubuntu forum one day :) as I'm a newbie)

---

### Post by LaRoza on 2008-02-14
> **godrox said:**
> I'm running Xubuntu and am trying to turn it into a kiosk. Opera kiosk mode seems to be exactly what I need, so I installed it through Synaptic. The first time I ran it in kioskmode just to see what it looked like and it worked fine. So I closed it, made the customizations I wanted and then tried to run it again, but now it won't go fullscreen or apply any of the other switches I included. In normal Opera mode, I can hit F11 and it'll go fullscreen, but in kiosk mode it won't. I even removed all my switches and just went with "opera -kioskmode" and it still won't do it anymore. I've tried uninstalling and reinstalling Opera, but apparently it still keeps all of your previous settings. Any ideas on how to fix this?

The .opera directory in your home directory is where the settings are stored. If you delete it, it will create a default.

(Press Ctrl + h to see the hidden directories)

---

### Post by fujikofujio on 2008-04-25
This thread is really old but I just wanted to add my experience with kiosk + ubuntu.

Don't even bother with firefox, opera is so much more kiosk friendly. For the kiosk that I made I used the server iso for ubuntu 8.04, I used old Dell pc that were headed to the junkyard, 400mhz, 128mb, 10gb HD.

* install ubuntu server, add ssh for remote administration if you like.
* configure networking, some of the kiosk had to be wireless, I used wpa_supplicant on those. "wpa_passphrase ssid key" is a lifesaver.
* the basic things you need to install is xorg, xterm and opera 
* you can also install xscreensaver so that it doesn't burn out your screen.
* create your limited user: adduser kiosk
* login to kiosk and do startx
* launch opera
* configure your settings, your homepage, disable the wand, disable popups etc. take the time to also configure xscreensaver
* logout
* edit or create .xinitrc
xscreensaver &
opera -kioskmode -nomenu -nosysmenu -noexit
NOTE: you can always quit opera by pressing ctrl+q, you need to have a master password set under preferences.
* after you've configured opera parameters to your liking create a script to call startx.

kiosk.sh
#! /bin/bash
startx
clear
exit

* edit .bashrc and call kiosk.sh at the end of the script.


Your done! Now when the kiosk user logs on x starts with only opera running, no need for window managers etc. And if it crashes or somehow the user manages to make it quit, it brings them back to console logon screen.

I tried for days with firefox, most of the extensions written for it were only for windows, I say most but I think all of them were for windows.

[http://sitegeisha.blogspot.com/2008/04/ubuntu-kiosk-opera-ftw.html](http://sitegeisha.blogspot.com/2008/04/ubuntu-kiosk-opera-ftw.html)

Hope this helps someone in the future :)

---

