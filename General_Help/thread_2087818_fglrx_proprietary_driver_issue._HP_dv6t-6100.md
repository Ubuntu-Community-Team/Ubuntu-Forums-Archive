---
title: "fglrx proprietary driver issue. HP dv6t-6100"
date: 2012-11-24
forum: General Help
---

### Post by Dans564 on 2012-11-24
So there is a ton of conflicting info on the web about the state of the fglrx in ubuntu 12.10.  On a clean install the OSS drivers work* but not very well; performance is less then stellar, and it runs very hot, so I need the proprietary driver. 

 I have tried installing both fglrx and fglrx-updates using the additional drivers tool, as well as the current version on amd's website and the beta driver from the website.  in all cases, computer boots fine, login screen works fine, yet only the wallpaper and mouse shows when logged in.  

I have already installed the linux headers for my kernel which I know is something causing a lot of problems for people.

Anyone have any insight on my problems?

D

---

### Post by Dans564 on 2012-11-24
Seems that problem is about xserver-xorg-intel package.

A workaround was proposed (By Nick Andrick) in this thread at launchpad bug

I've tested and worked for me with an HD 6770M hybrid with Intel HD 3000

Access [THIS]("https://launchpad.net/~andrikos/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal") ppa link , click on xserver-xorg-video-intel - 2:2.20.0-0~andrik1 to expand and download xserver-xorg-video-intel deb file for your architecture (amd64 or x86), you must download the 2 following files:

xserver-xorg-video-intel-dbg_2.20.0-0~andrik1_XXX.deb
and
xserver-xorg-video-intel_2.20.0-0~andrik1_XXX.deb
where XXX must me your architecture identifier (x86 or amd64)

Then open terminal and go to directory where files were downloaded, then type:
Code:

```
sudo dpkg -i xserver-xorg-video-intel*.deb
```after package installation, execute following command:
Code:

```
sudo dpkg-reconfigure Xorg
```reboot your machine and install amd fglrx driver

TIP: I've installed 12.11 beta and first time I execute 'sudo amdconfig --initial -f' command it returns me that my graphic card is not supported. But I've rebooted, then I logged in Ubuntu (also without Unity bars)

But don't worry, wait about 1 minute until finish loading your OS, then press CTRL + ALT + T (to open terminal) and execute following commands:

Code:

```
sudo amdconfig --initial -f
sudo reboot
```Now everything works like a charm after rebooting...

---

