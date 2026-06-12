---
title: "Shared Memory"
date: 2008-03-17
forum: General Help
---

### Post by Silvernail on 2008-03-17
I want to run 'syndaemon' to disable my touchpad while typing.

I get the error "SHMonfig disabled"

How/where do I go to enable it?

---

### Post by penguinpi.com on 2008-03-18
/etc/X11/xorg.conf

SHMConfig “off" (change to on) 

MAKE SURE YOU BACKUP THE XORG.CONF FILE FIRST!!!!!!!!!!!!!

---

### Post by Silvernail on 2008-03-18
> **penguinpi.com said:**
> /etc/X11/xorg.conf

SHMConfig “off" (change to on) 

MAKE SURE YOU BACKUP THE XORG.CONF FILE FIRST!!!!!!!!!!!!!

Thank you for the reply. For some reason I do not have the feature in Xorg.conf. I did find a touchpad input device which I may try turning off.

Again THANKS
Dave

---

### Post by Silvernail on 2008-03-22
What happens if I comment out the following in '/etc/X11/org.config?



```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```

---

### Post by Silvernail on 2008-04-19
> **penguinpi.com said:**
> /etc/X11/xorg.conf

SHMConfig “off" (change to on) 

MAKE SURE YOU BACKUP THE XORG.CONF FILE FIRST!!!!!!!!!!!!!

I don''t know why this did not work. T hat is to be investicated later.

I use 'sudo gedit' to change 'true' to 'false' and all is I  want it.

Thanks for the time and help.
Dave

---

