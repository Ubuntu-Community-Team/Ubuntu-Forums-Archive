---
title: "Screen goes black when playing YouTube video on Google Chrome"
date: 2014-11-03
forum: General Help
---

### Post by jhay3 on 2014-11-03
I'm on Ubuntu 14.04 + Google Chrome ver 38 and every time I play a second YouTube video on a different tab, the entire screen goes black, the keyboard and mouse becomes unresponsive yet I can still hear the video playing.

Any help would be greatly appreciated.

---

### Post by coldcritter64 on 2014-11-03
Just noted this suggestion in another thread that may help you, [http://ubuntuforums.org/showthread.php?t=2205892&p=13159423#post13159423](http://ubuntuforums.org/showthread.php?t=2205892&p=13159423#post13159423).
I don't use it just noted the suggestion there.
> A status bar application able to temporarily prevent the activation of both the screensaver and the **"sleep" powersaving mode.**My highlighting of the text from the ppa's description, this should suit your situation as well. Good luck.

Edit: a direct link to the ppa, [https://launchpad.net/caffeine](https://launchpad.net/caffeine)

---

### Post by pqwoerituytrueiwoq on 2014-11-03
i wrote a script to turn the screensaver on/off
also made one to disable the screensaver when flash is running, that does not work on html5 and chrome's pepperflash though (by test CPU usage of process)
here is my toggle script
```
#!/bin/sh
if [ $(xdg-screensaver status) = "enabled" ];then
   arg="suspend"
else
   arg="resume"
fi
xdg-screensaver $arg $(xwininfo -root | grep 'Window id'|awk '{print $4}')
echo "Screensaver $(xdg-screensaver status)"
exit
```

---

### Post by bodo bootlin on 2014-11-16
I had a similar problem and solved it by disabling the screensaver completely in the system settings - in the screen section and the energy savings section. I decided to go with the X server built-in screensaver and wrote two tiny scripts to configure it to my needs. Check out the manpages for ***xset*** to see what it can do.
The first script I named "xscreensaveron.sh". It is configured to run after log-in in the system settings.:
```
xset s on
xset -dpms
xset s 120
xset s blank
```

The other - even smalller - script i named "xscreensaveroff.sh":
```
xset s off
```
For both I created an icon the desktop to toggle between screensaver off and back on again. Not a big deal and works like a charm.

---

### Post by rogerpack2005 on 2014-12-18
no amount of turning off sleep seemed to help here (though disabling hardware acceleration in chrome did at least help) [http://askubuntu.com/questions/548309/youtube-causing-black-screen-in-chrome](http://askubuntu.com/questions/548309/youtube-causing-black-screen-in-chrome)

---

### Post by eudemonis on 2014-12-31
same problem. this worked for me. [http://www.solveyourtech.com/turn-hardware-acceleration-google-chrome/](http://www.solveyourtech.com/turn-hardware-acceleration-google-chrome/)



> **jhay3 said:**
> I'm on Ubuntu 14.04 + Google Chrome ver 38 and every time I play a second YouTube video on a different tab, the entire screen goes black, the keyboard and mouse becomes unresponsive yet I can still hear the video playing.

Any help would be greatly appreciated.

---

### Post by eudemonis on 2014-12-31
try this. [http://www.solveyourtech.com/turn-hardware-acceleration-google-chrome/](http://www.solveyourtech.com/turn-hardware-acceleration-google-chrome/)

---

