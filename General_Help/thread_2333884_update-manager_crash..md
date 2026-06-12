---
title: "update-manager crash."
date: 2016-08-14
forum: General Help
---

### Post by IbraM on 2016-08-14
Hi all. Today when I tried to run update-manager: I saw the next window:
[IMG]https://pp.vk.me/c626225/v626225279/22f4e/fMUga-KjuSQ.jpg[/IMG]

When I click on 'Install...' it starts something download ('Details' button doesn't active) and the get crashed.
[IMG]https://pp.vk.me/c626225/v626225279/22f55/qoyZQOPqTXI.jpg[/IMG]

Trying from console...

> ***@**pc:~$ sudo apt-get install -f
[sudo] password for ***:
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 18 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.

> hwe-support-status --verbose

WARNING: Security updates for your current Hardware Enablement
Stack ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)

There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash.

Xubuntu 14.04.5, 3.16.0-77-generic
About a week ago update-manager was working well. Yesterday I changed up in settings open drivers for my ATI Radeon videocard to proprietary one.
Does anybody know what's the problem?
It could be reproduced every time I do it all. Should I post the bugreport for update-manager and where can I do that?

---

### Post by banceu_sergiu_ione on 2016-08-14
As it say here, [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL) and you said run on a 3.16... kernel. 
> Starting Aug 4, 2016, systems using an interim HWE Stack older than the  Xenial HWE Stack will no longer receive software updates for the kernel  and, if you're running it, the graphics stack.  We encourage all Ubuntu  14.04 HWE Stack users to update to the final Ubuntu 16.04 Xenial HWE  Stack or fully upgrade to the Ubuntu 16.04 LTS release.

On the same site you can see what are the options you have.

At this point you will no longer get support for kernel and graphics.

If you try to upgrade from 14.04 to 16.04 make sure you do not run on proprietary drivers. Also I suggest you go for a check and see first how your pc run it via a liveOS version.

---

### Post by brian-murray on 2016-08-26
> **IbraM said:**
> Hi all. Today when I tried to run update-manager: I saw the next window:

About a week ago update-manager was working well. Yesterday I changed up in settings open drivers for my ATI Radeon videocard to proprietary one.
Does anybody know what's the problem?
It could be reproduced every time I do it all. Should I post the bugreport for update-manager and where can I do that?

Please report a bug using the 'ubuntu-bug update-manager'.  It'd also be helpful if you were to include the output of "hwe-support-status --show-all-unsupported" and "hwe-support-status --show-replacements".  Thanks in advance!

---

### Post by IbraM on 2016-08-26
> **brian-murray said:**
> Please report a bug using the 'ubuntu-bug update-manager'.
Where can I report the Xubuntu related bugs?

> **brian-murray said:**
>  It'd also be helpful if you were to include the output  of "hwe-support-status --show-all-unsupported"
**hwe-support-status --show-all-unsupported**
> hwe-support-status --show-all-unsupported
xserver-xorg-input-synaptics-lts-utopic 
xserver-xorg-input-wacom-lts-utopic libxatracker2-lts-utopic 
xserver-xorg-input-evdev-lts-utopic linux-image-generic-lts-utopic 
xserver-xorg-video-savage-lts-utopic libegl1-mesa-lts-utopic 
xserver-xorg-core-lts-utopic linux-image-3.16.0-74-generic 
xserver-xorg-video-siliconmotion-lts-utopic 
xserver-xorg-video-cirrus-lts-utopic linux-generic-lts-utopic 
xserver-xorg-input-all-lts-utopic linux-image-3.16.0-77-generic 
libgl1-mesa-dri-lts-utopic xserver-xorg-video-vesa-lts-utopic 
xserver-xorg-video-sisusb-lts-utopic 
xserver-xorg-video-fbdev-lts-utopic libgl1-mesa-dri-lts-utopic:i386 
xserver-xorg-video-all-lts-utopic 
xserver-xorg-input-vmmouse-lts-utopic 
xserver-xorg-video-ati-lts-utopic 
xserver-xorg-video-vmware-lts-utopic 
xserver-xorg-video-trident-lts-utopic 
linux-image-extra-3.16.0-74-generic 
xserver-xorg-video-modesetting-lts-utopic 
xserver-xorg-video-mach64-lts-utopic 
xserver-xorg-video-openchrome-lts-utopic 
linux-image-extra-3.16.0-77-generic 
linux-signed-image-generic-lts-utopic libglapi-mesa-lts-utopic 
linux-signed-generic-lts-utopic libgl1-mesa-glx-lts-utopic 
libglapi-mesa-lts-utopic:i386 libegl1-mesa-drivers-lts-utopic 
libwayland-egl1-mesa-lts-utopic libgl1-mesa-glx-lts-utopic:i386 
xserver-xorg-video-r128-lts-utopic xserver-xorg-video-tdfx-lts-utopic 
xserver-xorg-input-mouse-lts-utopic 
xserver-xorg-video-neomagic-lts-utopic libgles2-mesa-lts-utopic 
xserver-xorg-video-nouveau-lts-utopic 
xserver-xorg-video-mga-lts-utopic libgbm1-lts-utopic 
xserver-xorg-lts-utopic libopenvg1-mesa-lts-utopic 
linux-headers-generic-lts-utopic xserver-xorg-video-intel-lts-utopic 
libgles1-mesa-lts-utopic xserver-xorg-video-radeon-lts-utopic

> **brian-murray said:**
> and "hwe-support-status  --show-replacements".

**hwe-support-status  --show-replacements**
> linux-signed-image-generic-lts-xenial linux-signed-generic-lts-xenial linux-image-generic-lts-xenial linux-generic-lts-xenial xserver-xorg-lts-xenial libgl1-mesa-glx-lts-xenial:i386 libgl1-mesa-glx-lts-xenial

---

### Post by brian-murray on 2016-08-26
Xubuntu uses the same update-manager as Ubuntu, and the ubuntu-bug command will work on Xubuntu.

---

### Post by IbraM on 2016-08-26
Bug was reported, thanks.

---

