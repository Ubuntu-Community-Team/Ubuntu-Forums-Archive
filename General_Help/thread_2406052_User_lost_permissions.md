---
title: "User lost permissions"
date: 2018-11-15
forum: General Help
---

### Post by colonelkorn2 on 2018-11-15
I am not really sure what happened here, but I seem to not be able to do a lot of stuff I previously was able to do on Ubuntu. 

First let give some information, I am not really sure what to give aside from the basics since I have no clue what the issue is:
I have Ubuntu 16.04.5, installed just 3 weeks ago and using i3. 
I have kernel version 4.15.0-39-generic
I am using a Lenovo Y-50 laptop

Previously, I was able to do things such as connect to a network, listen to audio, and use the command poweroff without the need for sudo. However, after restarting my machine I see that it no longer automatically connects to my wifi and I cannot just use nmtui or nm-applet to connect anymore, they both say I do not have permission to change networking  I must connect to a network using sudo (I use sudo nmtui and this works fine). I cannot listen to audio as apparently audio drivers are not visible to me anymore. The command aplay -l yields:

```
aplay: device_list:268: no soundcards found...
```

However, doing sudo aplay -l yields:

```

**** List of PLAYBACK Hardware Devices ****Home directory not accessible: Permission denied
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3239 Analog [ALC3239 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC3239 Digital [ALC3239 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Further, I cannot poweroff my machine without using sudo, it gives the following error: 

```

Failed to set wall message, ignoring: Interactive authentication required.
Failed to power off system via logind: Interactive authentication required.
Failed to start poweroff.target: Interactive authentication required.
See system logs and 'systemctl status poweroff.target' for details.
Failed to open /dev/initctl: Permission denied
Failed to talk to init daemon.

```

There may be more features affected, but I have not been able to find them yet. I thought this may be an issue with my groups being deleted for some reason, but I still belong to the standard groups 

```
adm cdrom sudo dip plugdev lpadmin sambashare
```

I have also tried restarting my machine several times to no avail. 

Aside from just coding, the most "dangerous" thing I have done before this issue appeared is attempting to use module-assistant to install openafs-modules, which apparently no longer builds on Ubuntu due to a bug ([https://bugs.launchpad.net/ubuntu/+source/openafs/+bug/1748465](https://bugs.launchpad.net/ubuntu/+source/openafs/+bug/1748465)). Several hours after this failed, my laptop ran out of battery and died. When I restarted after charging this issue appeared. I have tried looking up solutions to specific problems I am having (such as the networking issue), but the solution to those seems to be to just add the user to a group. I think my issue does not fall into this category. I am thinking perhaps module assistant messed something up.

---

### Post by colonelkorn2 on 2018-11-15
I think I have found my issue. I will leave this post up as well as my solution in case anyone has this issue in the future.

What I was trying to do was set up AFS on my laptop. To do this, I followed a tutorial which told me to modify /etc/pam.d/common-auth and /etc/pam.d/common-session. These modifications, however, resulted in the behavior I mentioned above. At the time, I was naive enough to not know what the significance of PAM was, I thought it was just a package that the tutorial asked me to install, I had no clue it would affect my system to such a degree. Since the install failed, I decided to undo my steps after posting my original message so I uninstalled libpam-krb5. Upon doing this, it asked me if I wanted to overwrite the user modified config files with the system provided configs, to which I again naively said yes. This for some reason seems to have changed my password so I could no longer use sudo or even log in. I had to enter recovery mode and delete and reset my password (simply changing it would not work as I got an Authentication token manipulation error). 

With the system provided configs in place and my password reset, my system has returned to normal and I have wasted half a day. At least now I know what PAM is.

---

