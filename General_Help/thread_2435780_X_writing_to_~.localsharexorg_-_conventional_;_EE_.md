---
title: "X writing to ~/.local/share/xorg - conventional? ; EE error opening /dev/fb0"
date: 2020-01-25
forum: General Help
---

### Post by crackers_altitude on 2020-01-25
Is it conventional for X to write to ~/.local/share/xorg? I thought it always writes to /var/log/Xorg.0.log.
UPDATE:
ANSWER : YES - REASON :
an ask Ubuntu webpage claims that rootless X default since v1.16 is to write to ~/.local/share/xorg. To read about what that means : 
[https://wiki.ubuntu.com/X/Rootless](https://wiki.ubuntu.com/X/Rootless)

... still I persist:

My X session has an error - permission to open /dev/fb0 is denied. I am now working to understand this.

>>I was not aware this is default behavior<<NOW I DO - SEE ABOVE. 

I am concerned I have misconfigured X or something like libinput, or synaptics.

As a consequence, I have been on a long adventure - installing or removing packages using only apt. I solved one login problem already, but now I am trying to get a touchpad working with multitouch gestures - this led me to find ~/.local/share/Xorg.0.log.

details:

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 GNU/Linux
X.Org X Server 1.19.6
Release Date: 2017-12-20
some environment variables : 
XDG_MENU_PREFIX=gnome-
XDG_VTNR=2
XDG_SESSION_ID=2
TEXTDOMAINDIR=/usr/share/locale/
TEXTDOMAIN=im-config
XDG_SESSION_TYPE=x11
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
XDG_SESSION_DESKTOP=ubuntu
XMODIFIERS=@im=ibus
XDG_CURRENT_DESKTOP=ubuntu:GNOME
XDG_SEAT=seat0
XDG_RUNTIME_DIR=/run/user/1000
XAUTHORITY=/run/user/1000/gdm/Xauthority
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg


... prior to this, a number of packages such as anaconda2 and anaconda3 were installed - I think this is related my problem.

---

