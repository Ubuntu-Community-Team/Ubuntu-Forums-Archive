---
title: "Cupsys error crippling apt"
date: 2007-12-03
forum: General Help
---

### Post by bpazolli on 2007-12-03
Doing an automatic upgrade from my 64bit gutsy system I got an error message as such
Code:

E: Sub-process /usr/bin/dpkg returned an error code (1)

The process spits this message up every time I try to install anything using apt until I type in "sudo apt-get remove cupsys" which removes cupsys and thus the problem. By running "sudo apt-get install cupsys" I recieved the following dump
Code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  cupsys-bsd cupsys-driver-gutenprint cupsys-driver-gimpprint
  foomatic-filters-ppds xpdf-korean xpdf-japanese xpdf-chinese-traditional
  xpdf-chinese-simplified cups-pdf hplip
The following NEW packages will be installed:
  cupsys
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2033kB of archives.
After unpacking 11.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package cupsys.
(Reading database ... 94640 files and directories currently installed.)
Unpacking cupsys (from .../cupsys_1.3.2-1ubuntu7.1_amd64.deb) ...
Setting up cupsys (1.3.2-1ubuntu7.1) ..
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have done "sudo apt-get clean" to remove the download files in case of a corrupted download, no help and I have gone through manually and tried to confirm each dependency, all of which seem fine, and done "apt-get update" after install as well.

Further note that when typing cupsys into terminal I get a command not found message, I don't know if this normal or not. I am starting to think this is an actual bug. I am this close to reinstalling linux, which is something I thought only had to be done in windows. I would like to know how I can download the pre-update download I have already tried the version here [http://packages.ubuntu.com/gutsy/net/cupsys](http://packages.ubuntu.com/gutsy/net/cupsys) to no luck, i.e. seems to be 
the same.

I had a hp laserjet 1200 working before and I am running 64bit version of ubuntu.

---

### Post by snakattak on 2007-12-14
I am currently having the same problem. Trying to install Kubuntu in a chroot environment and it is stuck on cupsys. I cannot even remove it to re-install it. The problem is with cupsys 1.3.2-1ubuntu7.1. This is affecting everything else I do as I cannot continue with the install. Every method of install or remove cupsys produces the output below, and I cannot complete the install.
```
Setting up cupsys (1.3.2-1ubuntu7.1) ...
invode-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure)
  subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
  cupsys
E:  Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by CanadianGuitarist on 2007-12-15
Ya im having this problem also. any help would be awesome

---

### Post by WaddleDee on 2007-12-28
Forgive me for bumping, but I too am also experiencing this problem, and I too also remove cupsys to fix, but I would like to print. :(

Please help us.

---

### Post by nikkkko on 2008-01-07
I have the same issue. 

It started as a problem seeing a printer attached to another computer - it consistently refused to see the sharing machine's new IP address, showing a printer attached to the old and now non-existant IP.  I decided to re-install cups, only to find that it still saw the old IP! Then I re-installed everything cups related and that's when I hit the problem.

Anyone got a suggestion?

---

### Post by arjayes on 2008-02-29
Same here this is what i get when i do " sudo apt-get install -f "
> 
08:49 PM:$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libfaad2-0 libxvidcore4 libsoundtouch1c2 libjack0 libmp4v2-0 libopenspc0 libx264-54 libcdaudio1 libsidplay1 libmpeg2-4 libmms0 libfaac0
  liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cupsys (1.3.2-1ubuntu7.5) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.7); however:
  Package hplip is not configured yet.
 hpijs depends on hplip (>= 2.7.12-0ubuntu2~gutsy1); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 hpijs
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by FastZ on 2008-03-17
Anyone find a fix for this problem?  I'm having it too on my laptop running 32-bit version of Gutsy.  I don't have this issue on any of my other machines, just my laptop.  Here is a pastebin of the output of a sudo apt-get upgrade on my machine.

I don't print and never will have a need to print anything from my laptop so how could I remove cupsys, hplip, and hpijs without having to get rid of ubuntu-desktop?  Is it possible to just remove those three packages and keep everything else?

[http://paste.ubuntu-nl.org/59951/](http://paste.ubuntu-nl.org/59951/)

---

