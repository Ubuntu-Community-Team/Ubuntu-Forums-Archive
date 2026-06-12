---
title: "Broke my xserver trying to install xgl"
date: 2006-11-05
forum: General Help
---

### Post by chrisblue on 2006-11-05
OK first up I am pretty new to Ubuntu & Linux. I had edgy installed and working well, having upgraded from dapper. Wanted to try to install xgl and followed the howto here [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Troubleshooting_Guide](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Troubleshooting_Guide)  however upon rebooting I am getting an error with xserver as follows

"Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?" Y/N

"GDM: Xserver not found: /user/bin/Xgl :0 :0 -fullscreen -ac -accel
glx:pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten
tcp vt7
Error: Command could not be executed!
Please intall the X server or correct GDM configuration and restart GDM."

Tried to reconfigure the xserver with dpkg-reconfigure xserver-xorg which appeared to run though but make no difference.

edit: In fact it quits after selecting the color depth with a warning about overwriting possibly customised config file. I tried backing up the file but the reconfigure still quits at the same spot. /edit

Tried to reinstall the nvidia drivers following the steps here [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Now I need a little help :)

---

### Post by boobooq88 on 2006-11-06
I feel your pain... why cant it be as easy as suse?  jeepers.

---

### Post by Dr. Nick on 2006-11-06
Someone please correct me if I am wring, But I believe XGL is not needed with edgy, I removed my xgl and am using the built in aiglx.
 
What I would try is removing xgl from the command line using
 
**sudo apt-get remove xgl**
 
and then see if X boots back up.
 
 
Here is the guide I followed to set up beryl on edgy if thats what your after
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by chrisblue on 2006-11-07
OK case closed. Fixed the problem. The first howto I used (referenced above) instructed me to edit /etc/gdm/gdm.conf-custom and add the following lines

```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

I managed to find this file and re edit it from the command line to remove the reference to the Xgl server and rebooted and all is back to how it was. phew!

---

