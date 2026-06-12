---
title: "Latest update breaks Nvidia drivers"
date: 2005-04-01
forum: General Help
---

### Post by HungSquirrel on 2005-04-01
At least, it did for me.  Mind you, I haven't done a dist-upgrade in a week, so this could have happened anytime between then and now, but something has broken my Nvidia drivers.

> $ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "xtt" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.


---

### Post by kleeman on 2005-04-01
Same thing happened here but a reboot solved things.

---

### Post by HungSquirrel on 2005-04-01
It didn't happen to me *until* I rebooted.

---

### Post by kleeman on 2005-04-01
Did you check that your /etc/X11/xorg.conf file wasn't overwritten? This happened to me after an upgrade about 4 days ago.

---

### Post by dermotti on 2005-04-01
The nvidia driver broke on my machine. X wouldnt start. I rebooted and it fixed it self somehow. The new drivers appear to be running great under ut2k4

---

### Post by Whiffle on 2005-04-01
If its fixed by a reboot that is because the update updated the kernel module and the glx-module.  It won't work until the kernel module has been reloaded, which is what the reboot does.

Squirrel, does synaptic show the same driver versions for the 2 nvidia drivers? and what does "sudo modprobe nvidia" give you?

---

### Post by HungSquirrel on 2005-04-01
The nvidia module is already loaded.

No, the driver versions are not the same.  The error dialog said so.

Synaptic shows no updates.

What kernel version is the latest K7?  I guess my GRUB entries got screwed up.

---

### Post by HungSquirrel on 2005-04-01
There was an update to the kernel headers just now.  Still didn't fix it.

---

### Post by negatory on 2005-04-01
I had this problems and a reboot solved them!But UT2004 is incredibly slow....I haven't been able to get past the initial screen...can't seem to understand why?

**EDIT:** I seem to have solved the UT2004 slowness by rm -rfing the .ut2004 dir in my home dir

---

### Post by HungSquirrel on 2005-04-01
I fixed the problem by getting the latest official drivers straight from Nvidia.


Edit: and after a reboot, it of course does not work.

NVIDIA = THE NEW ATI

---

### Post by slatkin on 2005-04-01
I just compiled te 2.6.11 with the latest nvidia-kernel-source and nvidia-glx files from the Ubuntu repository. I had to grab the latest nvidia-kernel-common from the unstable repository at [http://packages.debian.org](http://packages.debian.org) though because while nvidia-kernel-source and nvidia-glx are updated to the latest version, the common files in the Ubuntu repository are still the old version (why would that also not be updated? I can't install the nvidia module image without it).

Everything is working great. If you're working with precompiled binaries you might want to try compiling your own ([http://ubuntuforums.org/showthread.php?t=21111)](http://ubuntuforums.org/showthread.php?t=21111)).

---

### Post by Firetech on 2005-04-02
[QUOTE=HungSquirrel]I fixed the problem by getting the latest official drivers straight from Nvidia.


Edit: and after a reboot, it of course does not work.

NVIDIA = THE NEW ATI[/QUOTE]
If you use drivers straight from nVidia, you should "apt-get remove nvidia-glx".
Else the nvidia-glx package will kill your drivers after each upgrade. Do you get any info if you run "dmesg | grep -i nvidia"? Do you have the agpgart and/or your chipset agp driver blacklisted (NvAGP doesn't support all chipsets, and the nvidia installer may run "modprobe agpgart".)

---

### Post by elwis on 2005-04-02
True! i don't care about 3D accel, but a desktop with only 1024x768 is not usable, and ubuntu doesn't care at all whatever i write in my xorg.conf

Funs over, i loved the warty but i haven't had troubles with nvidia or X for 3 years, so Hoary's a giant leap back.  Better get back to SuSe's, though i definietly will miss apt-get.
(and yes, not to nag. Hoary are not a stable release - of course things like this might happen. unfortunately I need my computer 12 hours a day should have stayed Warty- I'll definietly try Ubuntu again though)

---

### Post by HungSquirrel on 2005-04-02
[QUOTE=Firetech]If you use drivers straight from nVidia, you should "apt-get remove nvidia-glx".
Else the nvidia-glx package will kill your drivers after each upgrade. Do you get any info if you run "dmesg | grep -i nvidia"? Do you have the agpgart and/or your chipset agp driver blacklisted (NvAGP doesn't support all chipsets, and the nvidia installer may run "modprobe agpgart".[/QUOTE]
 Removing nvidia-glx made it impossible to install the official drivers.  Yes, it boggles my mind, too.

I once tried blacklisting agpgart and using nvagp, but it doesn't work with SiS AGP controllers apparently, so I reverted.

---

### Post by Firetech on 2005-04-02
[QUOTE=HungSquirrel]Removing nvidia-glx made it impossible to install the official drivers.  Yes, it boggles my mind, too.

I once tried blacklisting agpgart and using nvagp, but it doesn't work with SiS AGP controllers apparently, so I reverted.[/QUOTE]
Do you have the headers so you can compile the official drivers? Are you sure you ran on the official before removing nvidia-glx?
I'm running the latest official driver right now (1.0-7174) and they are working better than both 6629 and 7167... But I'm running on a custom kernel, too, so I have the required headers. Try installing "linux-headers-[your-kernel-version]". (Replace [your-kernel-version] with the output from "uname -r", which you probably already have figured out...) I'm not sure if that helps but it's worth a try. It may be that you have to compile the kernel first... Or maybe just create a symbolic link called /usr/src/linux, directing to /usr/src/linux-headers-[your-kernel-version].

---

### Post by Biffy on 2005-04-03
I have the same problem, but a reboot wont help here. 

```
API mismatch: the NVIDIA kernel module is version 7.1.0, but this X module version is 1.0.7167. Please be sure that your kernel module and all NVIDIA driver files have the same driver version
```

Will this be fixed automaticaly via apt or do i have to do stuff manually? Cause i can wait a few days.

---

