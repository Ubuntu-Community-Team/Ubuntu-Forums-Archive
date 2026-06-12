---
title: "Wine X Server Crash"
date: 2007-01-29
forum: General Help
---

### Post by Clodaus on 2007-01-29
Whenever I attempt to run something with wine, even winecfg, it crashes the X server. I've done a clean install (removed with apt using the --purge option and reinstalled), and I still have the same problem. Any suggestions?

---

### Post by Preserved Killick on 2007-02-01
I'm seeing a similar problem-- Picasa2 uses wine, too.  Whenever I start this app, the screen goes black and then the gui comes back up with a login screen.  The same thing happens when I try to use a full-screen game (bzflag).  Are you by any chance using an nvidia graphics card?  I suspect the problem is related to the driver and the most recent system update.  I don't have a solution and I'm hoping someone here knows what's going on.

-- Killick

---

### Post by grcoles on 2007-02-05
Same issues here. Running both Dapper and Edgy clean installs, with both custom and stock kernels, along with the NVidia 9746 drivers, on an AMD Athlon XP 2600+ with 1GB RAM and a GeForce FX 5600 in dual-head mode (with TwinView enabled). 

On Dapper, I could not run any OpenGL applications, including screen savers, glxgears, googleearth, etc, without an X-server crash. I never noticed issues with Wine, however, until I performed a clean install to Edgy. Now, I can run glxgears without a crash, but googleearth will cause X to crash, and running winecfg causes the X server to crash. Checking /var/log/Xorg.0.log.old, I can see that the server crashed with SIGSEG (11):

```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting
```


Definitely an issue here. 

Note that I am using the NVidia 9746 drivers at work on a PIV 2.6GHz with 1GB RAM and a dual-head NVidia X300 card without issues with Wine or OpenGL (My work PC is either Breezy or Dapper, can't remember right now).

One thing I notice when I installed the NVidia driver is that there is some conflicts caused because Edgy appeared to ship with the NVidia kernel module built in, as part of one of the linux-restricted-modules packages, or something like that. I had to remove the conflicting package and reinstall the NVidia driver. 

Similar problems for you?

---

### Post by grcoles on 2007-02-06
Interesting:

[http://www.linuxquestions.org/questions/showthread.php?t=517918](http://www.linuxquestions.org/questions/showthread.php?t=517918)

I notice I am getting errors about OpenGL burried deep in the Xorg log. It appears to be loading parts of the nvidia driver but not others (opengl). The user in the above post suggests building one of the later kernels, I may try this (I actually enjoy kernel building, but I don't have a ton of time to do this right now), either way I'll let you know what I figure out.

---

### Post by grcoles on 2007-02-06
How peculiar. I booted into single mode, again, and ran the nvidia installer, again, this time as an "expert" (use the `-e' switch when running the installer). It found conflicting files, related to openGl, backed them up, and reinstalled itself. Sure enough, after running startx, I could run glxgears (it had also stopped working), googleearth, etc, without issue. Also, my winecfg works again. 

The only thing that I can surmise is that I had inadvertently allowed adept to upgrade a package that replaced the opengl driver files for Xorg, thus, the nvidia 2-d driver was loading, but the GL portion was not.

I have found that libgl1-mesa-glx is installed on the system by Kubuntu, and it apparently is in conflict with NVidia's drivers. Unfortunately, if I try to remove this package, **everything** I have installed for the graphical OS is marked for removal (such as `kubuntu-desktop', LoL). For now I will just avoid upgrading anything to do with the mesa drivers. :)

---

### Post by Preserved Killick on 2007-02-06
I reinstalled my nvidia driver for Ubuntu 6.06 using this driver script:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and my problem went away.

-- Killick

---

### Post by Enverex on 2007-02-11
I'm getting this now with the 97xx drivers. If I try and do anything that uses OpenGL (Wine, or even just running glxinfo) X crashes and then reloads dropping me at a login prompt. I've tried installing new drivers and it didn't help :(

---

