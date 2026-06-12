---
title: "Touchpad Synaptics configuration: where are in Ubuntu 17.04?"
date: 2017-05-14
forum: General Help
---

### Post by lorenzo-n on 2017-05-14
Hello,

I have installed Ubuntu 17.04 on a HP Spectre X360 15bl001na.
Thanks to synclient I have customized my touchpad behaviour but only very few options survive to reboot (i.e. new value for AccelFactor is in place after every reboot).
I have then checked /etc/X11/xorg.conf.d/ but xorg.conf.d didn't exist.
First question: maybe my touchpad is not a synaptic (or does not use synaptic drivers)? How to determine it?

As described here:
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Synclient](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Synclient)
I created ithe directory and created also a 70-synaptics.conf inside:
/etc/X11/xorg.conf.d/70-synaptics.conf
Then I filled the conf file with my configurations:
Section "InputClass"
    Identifier "touchpad"
    Driver "synaptics"
    MatchIsTouchpad "on"
        Option "LeftEdge" "1629"
        Option "RightEdge" "5313"
        Option "TopEdge" "1395"
        Option "BottomEdge" "4459"
        Option "FingerLow" "25"
        ...
        Option "MiddleButtonAreaTop" "0"
        Option "MiddleButtonAreaBottom" "0"
EndSection

BUT every reboot seems to ignore this file.

Any solution (different that put syclient commands in the bashrc file)?

Thank you,
Lorenzo

---

### Post by kevinkane on 2018-01-31
If you read the man page for synclient, it should tell you the location of the config file. On Ubtuntu 16.04, this is 
/etc/X11/xorg.conf

---

### Post by cruzer001 on 2018-01-31
You have one other problem.  17.04 has reached end of life.

[https://ubuntuforums.org/showthread.php?t=2382832](https://ubuntuforums.org/showthread.php?t=2382832)

---

### Post by oldos2er on 2018-01-31
Old thread closed.

---

