---
title: "Nouveau vs NVIDIA"
date: 2014-01-19
forum: General Help
---

### Post by Spirrwell on 2014-01-19
Alright, this is really simple. I recently switched from Linux Mint over to the latest Ubuntu 13.10. I've always found the traditional NVIDIA drivers to be a pain in the ass to deal with, especially if you want the latest from NVIDIA having to go get the .run file and blablabla. Point is, I have a GTX 660 Ti, and I decided to go with the NVIDIA driver right from the software center.

I've never really used the Nouveau driver, so I have no idea how well it works. I either want to update to the latest from NVIDIA using the .run file or go with Nouveau. I've heard that the Nouveau driver is really good considering, but I'd like to know what other people think. Any help\information is appreciated.

---

### Post by Bashing-om on 2014-01-19
Spirrwell; Hi !

The news is real good for open source support for graphics drivers in 13.10:
These links, though directed at switchable graphics, demonstrate how far the developers have come and provide links to additional information. 
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
[http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144](http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

The consensus I have observed, is try the open source drivers, the result might be very pleasing.

[INDENT][INDENT]just keeps getting better
[/INDENT][/INDENT]

---

### Post by buzzingrobot on 2014-01-19
For games and a lot of full-screen video, you probably still want the Nvidia.  Otherwise, nouveau is fine.  Try both and see for yourself.

There are PPA's that package new Nvidia releases, letting you avoid the .run route. Additional Drivers offers, at best, what was tested at the time of that Ubuntu release.

---

### Post by oldfred on 2014-01-19
This site does reviews of drivers.

 Nouveau vs. NVIDIA Linux vs. NVIDIA Windows 8.1

[http://www.phoronix.com/scan.php?page=article&item=nouveau_nvidia_win81&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_nvidia_win81&num=1)

[http://www.phoronix.com/scan.php?page=article&item=nvidia_linux_2013&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_linux_2013&num=1)
       NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

[http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1](http://www.phoronix.com/scan.php?page=article&item=nouveau_april_2013&num=1)

---

### Post by sgage on 2014-01-19
For some nvidia GPU's (e.g. my GeForce 8500 GT), the nouveau drivers in Ubuntu will not allow resume from suspend. Oddly, I have no problem with the nouveau drivers in other distros. Anyway, in Ubuntu I always install the newest nvidia drivers available in the repos, and all works well. 

I never notice that nvidia performed all that much faster than nouveau, but then, I'm not a gamer or anything. The nouveau drivers used to run a few degrees hotter than nvidia, but that seems to have been fixed within the past year.

---

