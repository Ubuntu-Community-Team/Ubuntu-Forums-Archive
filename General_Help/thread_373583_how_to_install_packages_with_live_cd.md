---
title: "how to install packages with live cd?"
date: 2007-03-01
forum: General Help
---

### Post by comodor64 on 2007-03-01
hi again
i tried to follow the very complicated (4 me) instructions to try
and install the nvidia latest driver -and i removed some restricted packages with
synaptic-now i cant boot noramlly coz it says my x-config is a mess
how do i use live cd to re install the old nvidia packeges?
i rather quit the option of seeing movies in my t.v. 
who has the time to burn on this coplicated manuals?

thanks

---

### Post by anaconda on 2007-03-01
Just mount your hd from the liveCD and edit your /etc/X11/xorg.conf file from the mounted disk..
search this place (the identifier may be different)

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
```

and change the driver from "nvidia" to "nv", which is the open driver that comes with ubuntu.. (so no 3d acceleration) and boot the machine and reinstall nvidia drivers..

Oh.. and if you have a backup of your xorg.conf file (I think nvidia installer makes one automatically? should be something like /etc/X11/xorg.conf.backup) just copy it to be xorg.conf and reboot..  might be easier..

---

### Post by bodhi.zazen on 2007-03-01
For the nvidia driver try the envy script :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

