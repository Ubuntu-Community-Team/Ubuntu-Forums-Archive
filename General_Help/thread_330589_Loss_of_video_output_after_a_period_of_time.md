---
title: "Loss of video output after a period of time"
date: 2007-01-03
forum: General Help
---

### Post by mapleshade on 2007-01-03
I have a computer running Edgy hooked up to my Samsung DLP TV via DVI.  I have the screensaver come on after 30 minutes, but don't have the computer set to go to sleep or turn off the monitor.  
After a period of time (several hours is as specific as I can be), usually after the TV has been off for a while, I'll turn on the TV and select the DVI input, but it can't get a signal.  I have shortcut keys (on my keyboard) programmed to launch terminal and firefox.  If I press one of these buttons, the HDD light on my case lights up and I can hear the HDs working, but no video is displayed.  All I can do is a hard reboot, which I don't like to do, and everything's fine once it reboots until I get home from work and there's no signal again.  
It seems to me that the video output from my card (ATI 9600) some how turns off after a period of time, but I can't figure out what setting would cause this, or how to fix it.  I installed the fglrx video driver as per the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).
Any ideas?
System details are in my signature.

---

### Post by mapleshade on 2007-01-06
So, it appears that whenever I turn off the TV and turn it back on, I'm unable to get a video signal from the computer.  Sometimes, if the TV's been on but on another input, I will come back to the screensaver and sometimes it says there's no signal, but if I hit a key on the keyboard the video will come back up.  Nothing I do after the TV's been turned off and back on will bring the video up.  Since I have a terminal shortcut on my keyboard, I realized that I can open it, and ```
 sudo shutdown now -r 
``` which I think is better than using the reset button.

Any ideas?

---

