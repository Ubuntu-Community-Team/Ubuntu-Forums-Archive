---
title: "[SOLVED] Problems with REinstalling nvidia driver"
date: 2008-01-18
forum: General Help
---

### Post by oscarsfriend on 2008-01-18
Hi,

I've had the nvidia driver 100.14.11 from nvidia's website working fine for some time now.  Today I had to reinstall the drivers after xorg was updated.  I had no problem.  I decided to uninstall the drivers and try the ones from the Feisty repos (nvidia-glx-new).  I couldn't get them to work, so I uninstalled the package, and reinstalled the one's from nvidia's website, however I cannot get X working at all with the drivers.  My xorg is OK, but I tried a new one, and that didn't work either.  I've tried rebooting.  I've tried uninstalling the drivers and reinstalling them, and nothing works.  Here is the error message I am getting from X:

```

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Running modprobe nvidia returns:
```

Not loading nvidia_new module; not used in /etc/X11/xorg.conf

```

Which suggests to me that it something in the nvidia-glx-new package has not uninstalled properly.  Can anyone shed any light on this?

---

### Post by oscarsfriend on 2008-01-18
OK, I got it working now.  I had tried removing the nvidia files from /lib/linux-restricted-modules/2.6.20-16-generic/, which did not work.  However there was also a file called /lib/linux-restricted-modules/.nvidia_new_installed, which I didn't see initially because of the dot, which hid it from ls.  Removing that file seems to have sorted things.

EDIT: It survived a reboot, and 3d is working fine, so I've marked the thread as solved.

---

