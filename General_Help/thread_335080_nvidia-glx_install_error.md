---
title: "nvidia-glx install error"
date: 2007-01-09
forum: General Help
---

### Post by paridoth on 2007-01-09
im getting this error when i try to install nvidia-glx

The following packages have unmet dependencies:
nvidia-glx: Depends: nvidia-kernel-1.0.9746
E: Broken packages

i have all the required repos, others are having this trouble too, check the end of this post

[http://ubuntuforums.org/showthread.php?t=263851&page=140](http://ubuntuforums.org/showthread.php?t=263851&page=140)

---

### Post by Azakus on 2007-01-09
The new updates to the restricted modules breaks the nvidia-glx repo. Try using the envy program.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by firezip on 2007-01-10
> **Azakus said:**
> The new updates to the restricted modules breaks the nvidia-glx repo. Try using the envy program.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Whenever I use that script it goes to a black screen and I have the reboot. Hmm, should I just do a fresh install, install nvidia drivers, and then upgrade ubuntu? BTW I just set up ubuntu so I have no important files to backup. Thanks for the help :)

---

### Post by renzokuken on 2007-01-10
upgrading ubuntu will give you a new kernel, and since the nvidia drivers are tied into the kernel, you would have to reinstall them anyway.

---

### Post by firezip on 2007-01-10
Well envy is still not working for me, does it have to do something with my xorg.conf? Check this section out

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	55-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"


```

I have a nvidia 7600gt btw

---

### Post by bodhi.zazen on 2007-01-10
YOu need to change 

Driver "vesa"

to

Driver "nvidia"

---

### Post by PriceChild on 2007-01-10
I'm just getting in contact with lupine about the latest issues.

---

### Post by PriceChild on 2007-01-10
lupine is now aware of the issue and we're sorting out updated packages.

---

### Post by lupine_nickt on 2007-01-10
Yeah. Updated drivers will come.... tomorrow. I have an exam so need to get some stuff done for it.

In the meantime, you can regrade to the standard Ubuntu l-r-m (no beryl) and nvidia-glx, or you can downgrade your kernel to the older version and use the current l-r-m and nvidia-glx (beryl). 

Can't say you weren't warned - see [http://nvidia.limitless.lupine.me.uk/](http://nvidia.limitless.lupine.me.uk/) ;)

xF,

...Nick

---

### Post by Azakus on 2007-01-10
You're not trying envy from a terminal are you? You have to logout from Ubuntu and press Control Alt F1 to go to a blank screen, login, then run the envy script. Running it from an active X.org will kill the script and reboot your computer. More detailed directions are on the site below the packages.

---

### Post by lupine_nickt on 2007-01-11
ok, fixed. Hit me with your update stix

2,000+ people all trying to update at the same time... should be fun ;)

xF,

...Nick

---

### Post by jamesford on 2007-01-11
i still get
The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9746
E: Broken packages

amd64

---

### Post by paridoth on 2007-01-11
ya same here, did apt-get update, then apt-get upgrade, and it got held back, so i did apt-get install nvidia-glx, and got the same dependency error

---

### Post by jamesford on 2007-01-11
i found a fix that works for me
1: disable any non-official repos, leaving just the ubuntu ones
2: install nvidia-glx, configure xorg etc
3: re-enable beryl repos and isntall the usual way

it works! this must mean that beryl works with the nvidia drivers in ubuntus official repos

i got an uninstallable update in my update manager tho, nvidia-glx from 1.0.8776+2.6.17.7-10.1  > 1.0.9746+2.6.17.6-2~release.lupine1
isnt there something wrong with the lupine kernel version there?

---

### Post by paridoth on 2007-01-11
ya i already did that so i could get hardware acceleration to play games with and such, but i thought beryl needed the beta drivers?

---

### Post by jamesford on 2007-01-11
thought so too, but it works

---

### Post by sherl0k on 2007-01-12
The latest kernel upgrade forced me to uninstall nvidia-glx, which in turn made X fail on boot for me. I had to edit /etc/X11/xorg.conf and change 'nv' back to 'nvidia' but then GNOME failed to load, most likely because I have beryl set to load automatically and beryl doesn't like the nvidia driver. Luckily I have fluxbox installed so I'm running from that right now until I can get my nv driver back.

---

### Post by PriceChild on 2007-01-13
> **sherl0k said:**
> Luckily I have fluxbox installed so I'm running from that right now until I can get my nv driver back.I'm confused... fluxbox runs on the same xserver as all the others and so uses the same driver... if fluxbox works then so will the others...

---

### Post by bkeithly on 2007-01-20
THANKS Envy works great!!!!

---

