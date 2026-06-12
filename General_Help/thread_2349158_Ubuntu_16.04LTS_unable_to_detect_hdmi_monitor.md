---
title: "Ubuntu 16.04LTS unable to detect hdmi monitor"
date: 2017-01-11
forum: General Help
---

### Post by alkarinv on 2017-01-11
I have already tried posting on AskUbuntu [here]("http://askubuntu.com/questions/870762/ubuntu-16-04-unable-to-detect-hdmi-monitor").

Essentially; as of today my laptop is not recognizing any display inputs from my HDMI port. I booted into windows and it is working correctly.

As mentioned in my AskUbuntu question I have attempted to reinstalled the Nvidia drivers to no avail. A friendly user went into chat with me and upon some further troubleshooting, NVIDIA Server X Settings does not come up with any information.


[IMG]http://i.imgur.com/tw0SO80.png[/IMG]


[IMG]http://i.imgur.com/b7sD01L.png[/IMG]

However in Additional Drivers, it specifically states that I am ```
using NVIDIA binary driver -version 375.26 from nvidia 375 (open source)
```


When I run
```
xrandr --listmonitors
```
It returns 
```
Monitors: 1 [COLOR=#111111][FONT=Consolas]0: +*eDP1 1920/345x1080/194+0+0  eDP1[/FONT][/COLOR] 
```

The laptop I am using is an ASUS Q551LB with an nvidia geforce 940m graphics chip

Any help is greatly appreciated thank you!

---

### Post by efflandt on 2017-01-14
Was it working before with different nvidia driver? Did you try booting with the external display on, with that HDMI input selected (if an HDTV with multiple inputs)?

Read "man apt-get". Note that "sudo apt-get upgrade" only upgrades existing packages, any may not do updates if related packages or dependencies change, so it may hold some things back. After doing "sudo apt-get update" it would be preferable to do "sudo apt-get dist-upgrade". That does a smarter upgrade to keep everything coordinated (it does not change your Ubuntu version).

Does NVIDIA X Server Settings look like that when running without external display? Normally with hybrid graphics there should be a panel to select Intel or Nvidia graphics (although you might need to logout and back in or reboot when switching). Maybe something did not get removed or updated properly.

I would try doing:```
sudo apt-get purge nvidia*
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install nvidia-375
```Or if still strange, purge nvidia* and try nvidia-370.

Unfortunately, my gaming laptop with Intel/Nvidia hybrid graphics will not even power up to BIOS splash (gradually powers down in 7 sec w/blank screen), so I cannot test it with recent Ubuntu and nvidia driver versions

---

### Post by ik-0 on 2017-01-14
Your Nvidia driver isn't set as the main driver so it's defaulting to the onCPU video chip, which is probably Intel with module i915.  Do lsmod and grep for DRM to see what video driver is loaded.  If i915 is the default, you can switch to the Nvidia and logout or try to fix the i915.

---

