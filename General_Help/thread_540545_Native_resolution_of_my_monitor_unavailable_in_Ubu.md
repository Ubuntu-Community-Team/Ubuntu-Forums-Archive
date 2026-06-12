---
title: "Native resolution of my monitor unavailable in Ubuntu?"
date: 2007-09-01
forum: General Help
---

### Post by daldous on 2007-09-01
I have a 22" LCD Flatscreen monitor and I can't get its native resolution (1680x1050) in Ubuntu. The highest I can get with dpkg-reconfigure xserver-xorg is 1280x1024 -- even though I've selected other, higher resolutions. The native option just isn't available to me when I go to System->Preferences->Screen Resolution. 1280x1024 at 61Hz is the best I can see. 

My graphics card is NVIDIA GeForce 6800GS and the monitor is L226W from LG. The monitor's native resolution is 1680x1050 and refresh rates are this: 

HORIZONTAL SCANNING FREQUENCIES 	
Analog: 30 ~ 83 kHz
Digital: 30 ~ 83 kHz
 
VERTICAL SCANNING FREQUENCIES 	
Analog: 56 ~ 75 Hz
Digital: 56 ~ 75 Hz

I am using the vesa drivers for this machine. Please help.

---

### Post by taurus on 2007-09-01
You need to install nVidia driver to get to a higher resolution.  Use synaptic and search for nvidia driver then.

---

### Post by daldous on 2007-09-01
Right on, I've searched for nVidia in Synaptic but I don't know what to install for my GeForce 6800GS. Any advice? 

These are the search results: 
[http://xs219.xs.to/xs219/07356/scrnsht1.png](http://xs219.xs.to/xs219/07356/scrnsht1.png)
[http://xs219.xs.to/xs219/07356/scrnsht2.png](http://xs219.xs.to/xs219/07356/scrnsht2.png)

---

### Post by taurus on 2007-09-01
Which release are you running?  Otherwise, go with nvidia-glx (or nvidia-glx-new), nvidia-settings, & nvidia-xconfig.

---

### Post by daldous on 2007-09-01
Not quite sure how to find that out :)
I know for sure I'm running Ubuntu 7.0. I had to do a bunch of package updates when I first loaded. Will it make a difference?

---

### Post by daldous on 2007-09-01
I ran into a problem installing those three: 

E: /var/cache/apt/archives/nvidia-settings_1.0+20060516-3ubuntu1_i386.deb: trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-glx-new

E: /var/cache/apt/archives/nvidia-xconfig_1.0+20051122-2_i386.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-glx-new

I'll try nvidia-glx (without the new) and I"ll take it from there.

---

### Post by taurus on 2007-09-01
If it's 7.04, then it's Feisty.  Click those three packages (and it will also install other dependencies for them).  Then, you can use nvidia-xconfig to reconfigure your X to use nvidia driver instead of the generic driver, vesa.  And of course, you can use nvidia-settings to do all kind of settings for your nVidia graphic card.

---

### Post by daldous on 2007-09-01
> **taurus said:**
> If it's 7.04, then it's Feisty.  Click those three packages (and it will also install other dependencies for them).  Then, you can use nvidia-xconfig to reconfigure your X to use nvidia driver instead of the generic driver, vesa.  And of course, you can use nvidia-settings to do all kind of settings for your nVidia graphic card.


Well I got an error with those other two packages so I just tried doing nvidia-xconfig and I got this: 
zho@humzel:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

zho@humzel:~$ 

Any ideas?

---

### Post by taurus on 2007-09-01
You need to run that as root since you need to write to /etc/X11 directory.

```
**sudo** nvidia-xconfig
```

---

### Post by daldous on 2007-09-01
> **taurus said:**
> You need to run that as root since you need to write to /etc/X11 directory.

```
**sudo** nvidia-xconfig
```

Thanks for your advice and patience taurus. Ubuntu looks sweet at 1680x1050 @ 56Hz. :)

Now I gotta figure out how to make my headset work. I smell another thread in the coming :D

---

