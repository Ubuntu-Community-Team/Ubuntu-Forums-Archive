---
title: "Dell xps 13. core i7 skylake with intel hd graphics"
date: 2016-06-26
forum: General Help
---

### Post by oualid on 2016-06-26
Hello everyone !
I am running ubuntu 16.04 with kernel version 4.4.0. I would like to understand why at my native resolution (3200x1800) most of the UI is sluggish.
When I resize a window, it is considerably laggy for example. I made sure the intel drivers were installed. I tried disabling vsyn. And I managed to fix the screen tearing by adding a conf file.
When I set the resolution at 1920x1080. Everything is smooth, resizing windows is not a problem ( yes this is my benchmark aha ! ).
I find it even weirder that when I tried windows 10 while receiving the machine, everything is so damn smooth.... So I know this is not a hardware issue.

Basically, how do I get the same performance on linux ?
Thank you all !

---

### Post by oldfred on 2016-06-27
Dell is pretty good about offering updated drivers for its hardware in a Sputnik package. Back when 12.04 did not work, they had a sputnik, but by 14.04 all those changes were included in the standard distribution.
Not sure what Dell now has or what is included in current distributions.

 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Dell with Ubuntu 14.04 pre-installed & question on special drivers (Sputnik)
[http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops](http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)
Uses Intel Wi-Fi adaptors
[http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/](http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

