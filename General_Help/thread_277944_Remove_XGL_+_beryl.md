---
title: "Remove XGL + beryl?"
date: 2006-10-15
forum: General Help
---

### Post by Poka64 on 2006-10-15
I used this guide to install xgl + beryl:  [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

I don't like it, how do I remove it?

Searched through the forums and I found nothing that could help me out :(

The problem that I'm having is the poor support with VLC, it gets screwed up bad when I try to watch stuff, can't use Opengl driver either.

So, how do I remove this buggy xgl beta thing from my system?

---

### Post by skymt on 2006-10-15
* Remove beryl-start or beryl-manager (whichever you chose) from the Sessions control panel (System > Preferences > Sessions > Startup Programs)

* Edit /etc/gdm/gdm.conf-custom (gksudo gedit /etc/gdm/gdm.conf-custom) and remove these lines from the bottom:```
[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```* Log out and back in

* Run this command:```
sudo apt-get remove xserver-xgl compiz-gnome emerald emerald-themes beryl beryl-manager
```

Your system should now be Beryl- and XGL-free.

---

### Post by Poka64 on 2006-10-15
Thank you skymt :)

---

### Post by crazedgremlin on 2006-12-04
skymt you **ROCK!!!**
You saved me from doing a reinstall :):):)

I am in your debt forever lol

---

