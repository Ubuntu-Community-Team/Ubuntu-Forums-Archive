---
title: "Back and forth on video cards, need help with getting nvidia-glx"
date: 2007-03-04
forum: General Help
---

### Post by Jphenow on 2007-03-04
So at the beginning this computer had a geforce 4 64mb, and i hated it horribly, so i chucked that for an ATI, that was a mistake, better potential...if you can get drivers and if you do you're still screwed on the glx side of things, well now i have a gefore fx 5200, finally got back into my desktop and i see this output after i do 

```
sudo apt-get install nvidia-glx
```

[I]The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
(Reading database ... 217004 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code [/I]

So after this someone pointed out to uninstall everything with mesa in it, should i do so and then see what happens? or does mesa have more to do with video than just ATI stuff? orrr what else any other ideas, and yes i have tried all adept, synaptic and of course apt to do this process.

thanks in advance!!

---

### Post by fragos on 2007-03-04
I also have an FX5200 and Synaptic finds a number of package that reference mesa.  My system works well.  nvidia-glx is the way to go but I recommend you use Synaptic instead of apt-get.

---

