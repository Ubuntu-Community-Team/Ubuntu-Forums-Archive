---
title: "how to update intel graphics drivers in ubuntu 14.04 final beta?"
date: 2014-04-12
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-12
i saw this link: [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux)

should i go ahead and install it these are for 13.10....will they work with 14.04 as well? 
thanks for the help in advance:P

---

### Post by Mark Phelps on 2014-04-12
You generally do not need to hunt down and install Intel video drivers are they are bundled with the kernel and loaded during initial setup.

What leads you to believe you have to install new drivers? If you're seeing a desktop, the Intel drivers are already installed.

---

### Post by AbhimanyuAryan on 2014-04-12
reason why i am updating the drivers: [http://ubuntuforums.org/showthread.php?t=2216420](http://ubuntuforums.org/showthread.php?t=2216420)

---

### Post by grahammechanical on 2014-04-12
That link that you provided also linked to this site. And of all the suggestions only one person said to install a proprietary (closed source) video driver but the person added that it was only necessary to do this if we were using 12.04.1 as later versions of Ubuntu had drivers that fixed the problem.

[http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)

If you want you can open Additional Drivers and see if it offers a proprietary driver. Ubuntu 14.04 will have updated open source video drivers and proprietary video drivers as well as later Linux kernels than those that come with Ubuntu 13.10.

As for the Intel Graphic Installer, the only way to find out if it works in 14.04 is to install it and see. Or to ask on this section of the forum if anyone has installed it and what the results were.

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

Regards

---

### Post by s-p-constantine on 2014-04-19
> **grahammechanical said:**
> That link that you provided also linked to this site. And of all the suggestions only one person said to install a proprietary (closed source) video driver but the person added that it was only necessary to do this if we were using 12.04.1 as later versions of Ubuntu had drivers that fixed the problem.

[http://askubuntu.com/questions/128463/how-to-control-brightness](http://askubuntu.com/questions/128463/how-to-control-brightness)

If you want you can open Additional Drivers and see if it offers a proprietary driver. Ubuntu 14.04 will have updated open source video drivers and proprietary video drivers as well as later Linux kernels than those that come with Ubuntu 13.10.

As for the Intel Graphic Installer, the only way to find out if it works in 14.04 is to install it and see. Or to ask on this section of the forum if anyone has installed it and what the results were.

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

Regards

I've spent a wasted 4 hours trying to get this to work, progressively installing missing libraries etc. I have given up!

---

### Post by strange on 2014-04-21
im looking for a way to update my driver as well because my gpu seems to lock

> 
strange@norad:~$ xbmc
intel_do_flush_locked failed: Input/output error
intel_do_flush_locked failed: Input/output error

it seems to do that after doing some fullscreen/windowed switching

---

