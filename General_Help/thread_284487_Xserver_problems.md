---
title: "Xserver problems"
date: 2006-10-25
forum: General Help
---

### Post by lwr on 2006-10-25
When I boot, I get the following message:
> GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel
glx: pbuffer -accel xv:fbo -auth /ver/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restert GDM.
I've tried copying my xorg.conf nack-up files accross, and done dpkg-reconfigure xserver-xorg seveeral times, but I keep getting the same message. I think this started when trying to install nvidida drivers on edgy with Automatix2. Please help. Thanks

Luke

---

### Post by lwr on 2006-10-26
Please please help. I know someone must know what to do. I really don't want to have to do yet another reinstall before I can get into a working system. Thanks.

---

### Post by frodon on 2006-10-26
Weel it seems that automatix installed Xgl on your computer, i wonder why by the way since edgy have a AIGLX built-in support and Xgl is no more needed to run beryl/compiz.

Well, see if you have a gdm.conf-custom file (/etc/gdm/gdm.conf-custom)
You should have something like at the end of the file: ```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```if yes remove it and reboot.

---

### Post by lwr on 2006-10-26
Cheers frodon! That's brilliant, everything's working again. Thank-you so much. It might not have been Automatix that did that, as I've been playing about trying (unsuccessfully so far) to get any kind of 3D desktop working on Edgy. I don't want to be too hard on Automatix (especially after giving me Flash 9!), as it's usually my fault.
Thanks again frodon. You forum guys are superb; thanks for all the hard work you put in to make Ubuntu such a great distro and help fools like me.

---

### Post by frodon on 2006-10-26
If you want to get 3D desktop working on edgy, i suggest you to follow this guide which works for many users and don't require Xgl :
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
 
Enjoy ;)

---

### Post by lwr on 2006-10-26
Thanks again frodon. I'd come accross that guide, but things hadn't worked beforehand for some reason. It's all working beautifully now, though. Beryl's certainly very nice. Thanks again.

Luke

---

