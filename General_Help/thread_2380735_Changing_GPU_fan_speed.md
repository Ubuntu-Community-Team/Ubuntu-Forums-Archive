---
title: "Changing GPU fan speed"
date: 2017-12-21
forum: General Help
---

### Post by resiak1 on 2017-12-21
I've been trying for several hours to change the fan speed on my GPU's and can't seem to find anything that works. I've tried NVClock, editing xorg.conf (or creating it rather), and editing fan speed settings in NVIDIA X Server Settings. 

I'm unable to locate the NVClock package, if I create xorg.conf ubuntu black screens on boot, and there's no option to edit fan speed settings in Thermal Settings in NVIDIA X Server Settings. 

Can someone please help? I'm getting a bit fed up. 

Thank you!

P.S I'm using 16.04

Solution:

```
cd /etc/X11
sudo nvidia-xconfig --enable-all-gpus
nvidia-xconfig --cool-bits=4
reboot
```

---

### Post by Autodave on 2017-12-21
May we ask why you are trying to change the fan speed? Are you having a particular problem?

---

### Post by Frogs Hair on 2017-12-21
> [COLOR=#000000]I'm unable to locate the NVClock package,[/COLOR] I can find no release candidate for 16.04 and NVClock only allows a 10 %  speed adjustment up or down. Also, your card like mine may have no fan speed setting option. What card and driver  are you using ?

---

### Post by again? on 2017-12-21
In 17.04 using nvidia drivers with Xorg I run these 2 commands and reboot.
(Used the same procedure in 16.04)
```
cd /etc/X11
sudo nvidia-xconfig --cool-bits=4
```

On restart, nvidia-settings has a fan control slider.
The fan control only lasts for the session and resets when you logout.
[http://www.gpugrid.net/forum_thread.php?id=3525](http://www.gpugrid.net/forum_thread.php?id=3525)

---

### Post by resiak1 on 2017-12-21
> **Autodave said:**
> May we ask why you are trying to change the fan speed? Are you having a particular problem?

My GPUs are hitting temp over 90° and the fans are only on 50-60%.  I want to run them at 100% 

> **Frogs Hair said:**
> I can find no release candidate for 16.04 and NVClock only allows a 10 %  speed adjustment up or down. Also, your card like mine may have no fan speed setting option. What card and driver  are you using ?

I'm running 3 gtx 1080 FE and 1 gtx 1080ti FE. The driver is 387 I believe. I'll double check when I get home.

> **guber2 said:**
> In 17.04 using nvidia drivers with Xorg I run these 2 commands and reboot.
(Used the same procedure in 16.04)
```
cd /etc/X11
sudo nvidia-xconfig --cool-bits=4
```

On restart, nvidia-settings has a fan control slider.
The fan control only lasts for the session and resets when you logout.
[http://www.gpugrid.net/forum_thread.php?id=3525](http://www.gpugrid.net/forum_thread.php?id=3525)

Hmm, maybe I'll update Ubuntu.

---

### Post by again? on 2017-12-21
> **resiak1 said:**
> My GPUs are hitting temp over 90° and the fans are only on 50-60%.  I want to run them at 100% 



I'm running 3 gtx 1080 FE and 1 gtx 1080ti FE. The driver is 387 I believe. I'll double check when I get home.



Hmm, maybe I'll update Ubuntu.
Works in my 16.04 install as well.
If you have 3 gfx devices you probably need to write a config with a  "Coolbits"  option for each device ID.
[https://www.gpugrid.net/forum_thread.php?id=2925](https://www.gpugrid.net/forum_thread.php?id=2925)

---

### Post by resiak1 on 2017-12-21
Wait, does that create the xorg.conf file? I believe I tried this and couldn't boot until I deleted the xorg.conf file.

Edit: Actually I think I did 

sudo nvidia-xconfig --cool-bits=28

---

### Post by again? on 2017-12-21
> **resiak1 said:**
> Wait, does that create the xorg.conf file? I believe I tried this and couldn't boot until I deleted the xorg.conf file.

Edit: Actually I think I did 

sudo nvidia-xconfig --cool-bits=**28**

What's the **28** value?

---

### Post by resiak1 on 2017-12-21
> **guber2 said:**
> What's the **28** value?

Honestly, I have no idea. I was following the instructions someone posted in response to someone with a similar problem.

So I just got home and tried,

```
sudo nvidia-xconfig --cool-bits=4
```

and I get this message,

> WARNING: Unable to locate/open X configuration file.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
New X configuration file written to '/etc/X11/xorg.conf'




Edit: I just ran it again and got this,

> /etc/X11$ sudo nvidia-xconfig --cool-bits=4

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'




Lets see if I'm able to reboot without getting a black screen.

Success!!! Woohoo! Thank you!


Edit: Ok so  now how do I apply it to all 4 GPU's? I just realized it only enabled it for 1 GPU,

---

### Post by resiak1 on 2017-12-22
I figured it out,

```
cd /etc/X11
sudo nvidia-xconfig --enable-all-gpus
nvidia-xconfig --cool-bits=4




```

---

