---
title: "IDL package needs libxp"
date: 2016-05-22
forum: General Help
---

### Post by kaurie on 2016-05-22
I have been stalled for many years with an old version of 12:04 on an old machine and just recently bought a new laptop on which I have installed Ubuntu 16.04 (64 bit version). It appears to be running satisfactory but recently I was trying to install LAMP from ILL. Apparently this runs a version of IDL which needs "ibXp.so.6" I believe that this was on older versions of UBUNTU but is not installed in 16:04.

Googling I found that [http://www.harrisgeospatial.com/Support/HelpArticles/TabId/185/ArtMID/800/ArticleID/13759/IDL-fails-to-install-on-Linux-What-to-do.aspx](http://www.harrisgeospatial.com/Support/HelpArticles/TabId/185/ArtMID/800/ArticleID/13759/IDL-fails-to-install-on-Linux-What-to-do.aspx)
The article was titled “IDL fails to install on Linux: What to do” and  stated that “On some recent*Ubuntu versions (such as version 15.10) the libXP package needs to be downloaded*from the web first. The best place to look for these downloads is the Debian website and *here is a link to download libxp6 from there [https://packages.debian.org/stable/libs/libxp6.”](https://packages.debian.org/stable/libs/libxp6.”)

This link suggests "If you are running Debian, it is strongly suggested to use a package manager like aptitude or synaptic to download and install packages, instead of doing so manually via this website. You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this: deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) jessie main " Is this good advise?

I have tried it and it seems to work with all sorts of dire warnings. 

> sudo apt-get install libxp6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-base lammps-daily-doc libcdaudio1 libdirectfb-1.2-9
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libmpcdec6 libslv2-9
  linux-image-4.2.0-35-generic linux-image-extra-4.2.0-35-generic
  linux-signed-image-4.2.0-35-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libxp6
0 to upgrade, 1 to newly install, 0 to remove and 69 not to upgrade.
Need to get 22.2 kB of archives.
After this operation, 77.8 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libxp6
Install these packages without verification? [y/N] y
Get:1 [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) jessie/main amd64 libxp6 amd64 1:1.0.2-2 [22.2 kB]
Fetched 22.2 kB in 1s (17.5 kB/s)                
Selecting previously unselected package libxp6:amd64.
(Reading database ... 230293 files and directories currently installed.)
Preparing to unpack .../libxp6_1%3a1.0.2-2_amd64.deb ...
Unpacking libxp6:amd64 (1:1.0.2-2) ...
Setting up libxp6:amd64 (1:1.0.2-2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...

LAMP seems to run> However  Any comments to a relative newbie in this area would be very welcome.

---

### Post by mörgæs on 2016-05-23
The best way to install LAMP is ```
sudo apt-get install lamp-server^
``` (notice the caret at the end). It has worked for all Buntu releases where I have tried.

---

### Post by napapon on 2016-08-20
I have similar problem but got this instead

sudo apt-get install libxp6
[sudo] password for napapon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxp6

Any help is highly appreciated.

more info: libXp.so.6 library is missing when install IDL 8.5.1 on Ubuntu 16.04 guest on Oracle VMWar.

thanks in advance.

---

