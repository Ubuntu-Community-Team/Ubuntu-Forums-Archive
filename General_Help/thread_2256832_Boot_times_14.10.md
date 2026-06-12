---
title: "Boot times 14.10"
date: 2014-12-15
forum: General Help
---

### Post by mJayk on 2014-12-15
Hi All,

Recently upgraded from 14.04 to 14.10 and my boot time is now really bad ( > 1 min) wasnt amazing before hand but was not this bad. I don't really know how to diagnose this problem or what to do next so any help would be appreciated. I've attached a bootchart image for anyone who understands it :)

Cheers

Matt
[http://imgur.com/WSZLb84](http://imgur.com/WSZLb84)



[ATTACH=CONFIG]258594[/ATTACH]

---

### Post by ajgreeny on 2014-12-15
Sorry but your attached image is far too small to be of any use, and your linked image takes a long time to study properly on screen as it is so large.

It may be more useful to attach dmesg or syslog from /var/log which should show where any delays occur.

---

### Post by mJayk on 2014-12-15
sys log 
[http://paste.ubuntu.com/9530585/](http://paste.ubuntu.com/9530585/)

I pasted the image as that is what most people seam to ask for regarding these sorts of problems, hope that is more clear.

---

### Post by oldfred on 2014-12-15
Which log file did you post?
The demesg is the start up log and large times between timestamps are potential issues.

In the log you posted it looks like the dual video is having issues.
Often with the very new nVidia or dual video you need not only the newest nVidia driver, but support software and sometimes the newer kernel. I would think 14.10 would give you a lot of that over 14.04 but default.
But many use a ppa to load newer nVidia drivers than Ubuntu has in its repository.

If you do change to load from ppa or even directly from nVidia (not really recommended as various other issues) then be sure to purge all nVidia drivers first. 
Often Ultrabooks boot with Intel driver for low power, but even the Intel driver may need boot parameters to work well.
[http://ubuntuforums.org/showthread.php?t=2184839&page=2&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&page=2&p=12871710#post12871710)

There seem to be several ppa available with the newer nVidia drivers, not sure if one is better or not.
 PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

