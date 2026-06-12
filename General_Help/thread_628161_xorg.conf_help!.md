---
title: "xorg.conf help!"
date: 2007-11-30
forum: General Help
---

### Post by Hawk__0 on 2007-11-30
I think this is a problem with xorg.conf, but not positive.
I am on my brothers computer (fiesty 7.04) and I went to install the NEW nvidia drivers (nvidia-glx-new) to replace his current package of nvidia-glx
after that, x failed to start.

so i issued the command that is at the top of /etc/X11/xorg.conf, which is:
> sudo dpkg-reconfigure -phigh xserver-xorg
I then chose nvidia, and the problem persisted.

NOTE: before i did any of this i completely removed nvidia-glx and nvidia-glx-new

in the reconfiguration process i ended up having to use vesa.  it works. the video quality isn't great, but how do I get the old configuration back?  If I try installing the nvidia-glx drivers again I still get an X error.  In the log file it said something about the driver not matching the version of some other file... and at this point in time i cannot show the error because the log file was overwritten when i installed this vesa driver.

I REALLY NEED HELP!! PLEASE!!!

---

### Post by -grubby on 2007-11-30
I know this may seem kind of drastic but I think you should install NVIDIA-GLX-NEW and go to the etc/X11/ folder (gksudo nautilus) and delete xorg.conf. then reboot, and do the ```
sudo dpkg-reconfigure -phigh xserver-xorg 
``` and select the correct driver

---

### Post by PmDematagoda on 2007-11-30
Use the vesa driver to get to a GUI, get [Envy]("http://albertomilone.com/nvidia_scripts1.html") and then use it to install the Nvidia driver.

---

### Post by Hawk__0 on 2007-12-01
thx guys i tried both suggestions, however I get the same errors.  I redirected the error output to a text file, here is the error:

> 
kyle@kyle-desktop:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4493kB of archives.
After unpacking, 13.7MB of additional disk space will be used.
(Reading database ... 143113 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9631+2.6.20.6-16.30_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.6-16.30_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.6-16.30_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I also tried removing the deb package it has the error about, but the problem persists.

---

