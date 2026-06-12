---
title: "WPA and static ip; help please"
date: 2007-01-13
forum: General Help
---

### Post by sarikan on 2007-01-13
I have set up wi-fi radar; since gnome network applet lets me use only dhcp with my wireless adsl modem, but wi-fi radar simply can't connect
I have wpa supplicant setup, and gnome network applet has no problem in connecting to modem; it just does not allow me to use static ip. However, there are other users in the house and I need to get a specific ip for security related setup. 
Wi-fi radar does not show ipw as default wpa driver so I type it in the config dialog. but it just can not connect. Even if it says it is connected, and ifconfig shows that I have the ip,  I can't access anywhere. 

So, for static ip and wireless with wpa WHAT should I do? This his been a real problem since dapper, and I could not find any stable solution yet. 

Best Regards

---

### Post by sefs on 2007-01-13
Try to see if this thread helps you.  I finally got wpa to work by using this thread with a static IP.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by yopnono on 2007-01-13
This will probably fix you  problems. Connection Manager
[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

---

### Post by sarikan on 2007-01-14
Yopnono: thanks a lot, works like a charm (well, almost, just a problem with a file, but I think I got it working)

---

