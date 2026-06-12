---
title: "Where is my X configuration? (Ubuntu 12.10)"
date: 2013-02-15
forum: General Help
---

### Post by ArlieS on 2013-02-15
I'm having wall-to-wall problems with X on ubuntu 12.10, starting from when I got some kind of pop-up or menu suggesting I install nvidia drivers. (I've since removed them.) 

In attempting to investigate this, I wanted to look at the X configuration on my system. I expected to find this in /etc/X11/xorg.conf.  All found there was /etc/X11/xorg.conf.failsafe.  Another 12.10 installation didn't even have that. But a 12.04 installation has /etc/X11/xorg.conf and no /etc/X11/xorg.conf.failsafe.

If it weren't for the second (believed to be functional) 12.10 installation, I'd assume that my problems were caused by the missing configuration, combined with unsuitable defaults. As it is, I'm just plain baffled. 

Can anyone at least point me to whatever configuration X uses on 12.10. Pointers to changelists, bug reports, emails etc. explaining the change would be nice too.

---

### Post by deadflowr on 2013-02-15
When you say you remove them, what do you mean?
Did you install the nvidia drivers?
If you installed the nvidia drivers then you need to generate the xorg.conf file.

```
sudo nvidia-xconfig
```

As far as I know, if there isn't an xorg.conf file the system uses whats in /usr/share/X11/xorg.conf.d.

---

### Post by ArlieS on 2013-02-15
> **deadflowr said:**
> When you say you remove them, what do you mean?
Did you install the nvidia drivers?
If you installed the nvidia drivers then you need to generate the xorg.conf file.

```
sudo nvidia-xconfig
```As far as I know, if there isn't an xorg.conf file the system uses whats in /usr/share/X11/xorg.conf.d.

What I did with the nvidia drivers was:

sudo apt-get purge nvidia-current
sudo apt-get purge nvidia-settings

This is after some menu I can't now find suggested that I enable them, and once I rebooted, graphics login gave me a useless screen - no way to launch any applications, AND the usual tricks didn't get me a command prompt or a non-graphics login screen. 

Now the only way I can get graphics is to undock and redock; and every time the screen lock kicks in I have to do it again.  I'm trying to figure out whether this mess is caused by hardware, software, or both. (Windows 7 likes to blue screen when I try to use an external monitor :-)  But ubuntu 12.04 worked fine, and ubuntu 12.10 was merely a bit slow before the nvidia driver experiment.

---

