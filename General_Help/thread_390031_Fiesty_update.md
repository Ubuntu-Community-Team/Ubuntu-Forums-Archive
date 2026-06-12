---
title: "Fiesty update"
date: 2007-03-21
forum: General Help
---

### Post by tyty12 on 2007-03-21
I just ran the update from dapper to fiesty and I am now getting this error:

Current Operating System: Linux Peak2006 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 28 February 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 21 11:56:49 2007
(==) Using config file: "/etc/X11/xorg.conf"

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but
this X module has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
root@Peak2006:~#

Any easy way to fix this so I get the gui gdm back?

Thanks

---

### Post by Ruthenium on 2007-03-21
Try sudo apt-get install --reinstall nvidia-glx nvidia-kernel-common

---

### Post by taurus on 2007-03-21
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by tyty12 on 2007-03-21
Not sure what you had me do, but it worked perfect!  Thanks for the easy fix!!!

---

### Post by mephcpp on 2007-03-26
HI,I just upgraded to feasty and I got a similar problem. I followed the instructions above but still it does not load nvidia module. When I modprobe nvidia and I got an error like: failed to run install on nvidia module.

---

### Post by taurus on 2007-03-26
> **mephcpp said:**
> HI,I just upgraded to feasty and I got a similar problem. I followed the instructions above but still it does not load nvidia module. When I modprobe nvidia and I got an error like: failed to run install on nvidia module.

Did you reinstall nVidia driver after you upgraded to feisty?

---

### Post by mephcpp on 2007-03-26
Yes, I did.. only I didn't installed the right version. Problem solved thank you.

---

### Post by clrobnsn on 2007-04-02
I had similar problems and did the dpkg fix mentioned above. I then typed startx and gdm and gnome then appeared - even though I was trying to run kde. I exited, was returned to the commmand prompt and then restarted the machine and everythig worked out - booted into kdm and kde.

So, you might be able to skip the 'startx' command and just reboot.

Thanks!

---

