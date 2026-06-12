---
title: "Screen Resolution (simple one)"
date: 2008-04-20
forum: General Help
---

### Post by StOoZ on 2008-04-20
hello ubuntuers.
First I would like to say I LOVE UBUNTU!!!! I totally switched from windows to ubuntu, im free of windows.
now to the issue, seems like ubuntu can save the resolution Im selecting from the nvidia driver, I run the "sudo nvidia-settings" select the resolution,save it in the xorg (<< why I use the sudo) , restart, the login screen comes in the right resolution,but not what comes after it ... (desktop etc...)
[IMG]http://img522.imageshack.us/img522/9506/screenshotck3.png[/IMG]

when I try to change the resolution from ubuntu settings (system>pref>resolutions), it just dont have the proper Hz for that resolution,so I dont use it.

---

### Post by kyphi on 2008-04-20
In a terminal type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
use your up/down arrow keys to scroll to the resolution that you want and press the spacebar to select it.
Save and exit and reboot.

---

### Post by chewearn on 2008-04-20
So, what is the question?

Using nvidia restricted driver, only nvidia-settings works properly.  The other (standard) ubuntu method to change the settings are not working due to a nvidia driver twinview hack.

---

### Post by StOoZ on 2008-04-20
> **kyphi said:**
> In a terminal type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
use your up/down arrow keys to scroll to the resolution that you want and press the spacebar to select it.
Save and exit and reboot.

@ AstalaVista  : But still, im sure there is a way to fix it.

about the xorg, I backed it up, and run what you said, it only created a new xorg file saying:
> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080420110144

---

### Post by chewearn on 2008-04-20
> **StOoZ said:**
> @ AstalaVista  : But still, im sure there is a way to fix it.


nvidia put in a hack to use the display frequency as the selector for dynamic twinview options.  This allow the nvidia driver to change the resolution (within some limits) without restarting Xorg.  The side effect is the display frequency reported is incorrect.

To fix this problem, you have to disable dynamic twinview, but you would not be able to change some parameters in nvidia-settings.

In this page:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-d.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-d.html)

Search for:
Option "DynamicTwinView" "boolean"

for the explanation.

---

### Post by StOoZ on 2008-04-20
first of all , thanks.
secondly, I tried adding to the device in the xorg.conf the following line :
> Option "DynamicTwinView" "false"

but I still couldnt see the correct refresh rates :(:confused:

---

### Post by chewearn on 2008-04-20
If it's not working, I don't know what's wrong.  Please recheck that you did not make a typo error, and the option is under Screen or Devices section.  You need to restart Xorg for it to take effect.

---

### Post by sailor2001 on 2008-04-20
nvidea is tricky..  boot into recovery mode and type in sudo dpkg-reconfigure -phigh xserver/xorg select your resolution....click ctrl/x to save and type reboot....

---

