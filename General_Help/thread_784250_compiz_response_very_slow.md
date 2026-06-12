---
title: "compiz response very slow"
date: 2008-05-06
forum: General Help
---

### Post by kinzeron on 2008-05-06
Hi,

I have installed ubuntu Hardy 8.04 on my system, but the response I get is completely sluggish. I have tried xserver-xgl, the system response is fast and comparable to that of windows XP. However, once I try to enable desktop effect I get a blank screen with the mouse cursor hovering, nothing else.

I have an intel centrino 2.0G laptop with 2GiBytes RAM and nvidia 8400G with driver version 169.12 installed.

Does any have a remedy to this problem please? Am I missing something in the configurations?

Regards,

---

### Post by tommyhakinen on 2008-05-06
Please check if 3D Direct rendering is enabled.

> glxinfo | grep 'direct rendering'

If the answer is no, it might be something to do with Restricted Driver of your Graphics Card.

---

### Post by sdennie on 2008-05-07
This is a problem with something called PowerMizer in the nvidia drivers.  You'll have to run a script to force the video card to use max power at all times.  A simple script to do that would be:

```

#!/bin/bash

while true; do
    /usr/bin/nvidia-settings -q all > /dev/null
    sleep 25;
done

```

And, a more advanced method that works on some machines can be found towards the bottom of this thread: [http://ubuntuforums.org/showthread.php?t=747294](http://ubuntuforums.org/showthread.php?t=747294)

Edit:
Note: Neither of these are intended for xserver-xgl

---

### Post by kinzeron on 2008-05-07
For the glxinfo:
 direct rendering: Yes

As for the nvidia-settings tweak, I have tried it, but no much of improvement, xserver-xgl is still faster by many order of magnitude, so is there anyway to make compiz run with xgl? or at least is there anyway to make Xorg render things faster?

Regards,

---

### Post by sdennie on 2008-05-07
The only other thing I can think to try without xserver-xgl would be to install compiz settings:

```

sudo apt-get install compizconfig-settings-manager

```

And then navigate to System->Preferences->Advanced Desktop Effects Settings->General Options->Display Settings.  Once there, uncheck "Detect Refresh Rate" and manually move the Refresh Rate slider from 50 to 60.  You can also enable vertical sync from this screen if you get annoying amounts of tearing.

---

