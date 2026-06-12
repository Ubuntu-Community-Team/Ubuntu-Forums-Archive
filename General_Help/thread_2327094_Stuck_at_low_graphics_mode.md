---
title: "Stuck at low graphics mode"
date: 2016-06-07
forum: General Help
---

### Post by Kevin_Lopez on 2016-06-07
Hi, I am running ubuntu 16.04 and I have an amd cazzaro. I accidentally uninstalled ubuntu-desktop and lightdm, so I tried rebooting and of course I and into an issue. I sshed into my machine and reinstalled the two packages and I got a blank screen. I removed the fglrx drivers completely and still nothing. I followed this guide: [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)
and I got nothing out of it. What can I do? I havent installed the drivers from the website.

---

### Post by RobGoss on 2016-06-07
Hello and welcome, This post might have the fix for the Low graphic more message I believe this is a driver problem.
 [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

---

### Post by grahammechanical on 2016-06-07
There are no AMD proprietary video drivers in Ubuntu 16.04. Only radeon & amdgpu depending on the hardware. This is mentioned in the 16.04 release notes.

> The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 


More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)


[URL="https://wiki.ubuntu.com/XenialXerus/ReleaseNotes"]https://wiki.ubuntu.com/XenialXerus/ReleaseNotes
[/URL]
Regards

---

### Post by RobGoss on 2016-06-07
> **grahammechanical said:**
> There are no AMD proprietary video drivers in Ubuntu 16.04. Only radeon & amdgpu depending on the hardware. This is mentioned in the 16.04 release notes.




[URL="https://wiki.ubuntu.com/XenialXerus/ReleaseNotes"]https://wiki.ubuntu.com/XenialXerus/ReleaseNotes
[/URL]
Regards

> [COLOR=#000000]*When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). *[/COLOR]

[COLOR=#000000]* *[/COLOR]
[COLOR=#000000]So this would mean if you're trying to upgrade let's say from 14.04 to 16.04 and have [/COLOR]AMD proprietary drivers you may be faced with low graphic mode message correct?

---

### Post by QIII on 2016-06-07
Which driver did you remove and what were the results?  As stated, fglrx does not come with 16.04.  Don't try to install it from AMD's website.

16.04 installs with either the Radeon or AMDGPU open source drivers.  Since the Carrizo is considered a Volcanic Islands series and is GCN 1.3, I think AMDGPU would have been installed.

---

