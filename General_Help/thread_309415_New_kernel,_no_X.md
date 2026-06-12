---
title: "New kernel, no X"
date: 2006-11-29
forum: General Help
---

### Post by spork222 on 2006-11-29
I am currently running ubuntu 6.10.  Recently, I installed the server version of the kernel in order to support both of my processors.  However, after I installed and rebooted to the new kernel, X did not start.  I know that this is usually caused by Nvidia drivers (or, at least, it has in the past) so I removed nvidia-glx and then installed it again, both via apt-get.  The list of packages to remove and install was rather large, but I let it do its thing figuring it's smarter than I am.  Among those packages were ubuntu-desktop.  However, now it still will not start, and crashes after one try instead of the usual 3.  I don't know where to find the X logfile either (the onscreen dialogs never work correctly for me) so I don't know exactly what's wrong.

Anyone able to offer any help? ](*,) :confused: 

Note: Almost forgot- I also downloaded the NVidia drivers from NVidia's website, and they installed correctly with a proper xorg.conf, but still no help.

---

### Post by taurus on 2006-11-29
Change the "Driver" from "nvidia" to "nv" in /etc/X11/xorg.conf...

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by chrisccoulson on 2006-11-29
What is the error stated in /var/log/Xorg.0.log?

With the driver set to nvidia in xorg.conf, and nvidia-glx installed, make sure have installed the restricted modules package for the running kernel.

And, I thought the default kernel had SMP enabled to enable the use of dual processors?

---

### Post by spork222 on 2006-11-29
I figured out my own problem in the end.  It turns out that ubuntu-desktop was removed, but never re-installed, and therefore neither was my X server.  Simply re-installing it followed by the nvidia drivers from Nvidia's website fixed the problem.

And top only reports one cpu with the 386 kernel; with the server kernel it shows both.

---

