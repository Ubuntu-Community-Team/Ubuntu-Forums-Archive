---
title: "Wireless Help....PLEASE"
date: 2007-08-02
forum: General Help
---

### Post by skoalman88 on 2007-08-02
I recently bought an Edimax 7318USG from newegg. When I tried to install the RT73 drivers in Feisty, the device was visible with iwconfig, but any attempt to connect to the internet (FireFox, Gaim, apt-get, synaptic) caused the system to freeze.  For the time being, I have had to revert to Edgy and the device is working fine. However, I would prefer to be running Feisty. Can anyone offer some assistance on this issue?

Thanks

I followed the RT73 Guide (serial monkey drivers) and the p_larbigs's drivers tutorial.

---

### Post by upthelum on 2007-08-02
I lean towards staying away from wireless, sorry it's not any help though.

---

### Post by jet2230 on 2007-08-02
have u tried wicd?  

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

apparently it does work with your wireless card [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=146](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=146)

---

### Post by skoalman88 on 2007-08-02
I installed the newest WICD and that also freezes when I attempt to connect to my listed network.

---

### Post by jet2230 on 2007-08-03
u can try fixing ur problem thru trail & error.  run this command in terminal: sudo tail -f /var/log/syslog


then try connecting to ur wireless network and keep an eye out on the output in the terminal it should tell you where you are going wrong.

---

### Post by MadSavage on 2007-08-04
I know you've probably already got your card working, but I thought I'd add some information from my experience. I'm very new to Linux, and I started out with a Wireless problem; what's worse, it's my only connection to my router (which is too far for CAT-5, at that distance I would lose continuity.) Anyway, I also use the rt73 driver, and I actually found the information on how to fix this in the Ubuntu Wikki, using ndiswrapper and it worked great. 
 
   I use a Belkin Wireless 54g adapter, but it's still the same ralink driver we both need, (I think...) as long as you have the original drivers (for Windows) somewhere (or a place online to get them.) On the CD for the drivers, you should have three files, but only two are needed: rt73.inf, and rt73.sys. (I used the XP/2K drivers.) No matter which way you try to get your device working, I was just curious...did you blacklist the built-in rt73 drivers first?

---

