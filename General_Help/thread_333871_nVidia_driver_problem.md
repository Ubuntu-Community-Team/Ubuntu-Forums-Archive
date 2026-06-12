---
title: "nVidia driver problem"
date: 2007-01-08
forum: General Help
---

### Post by J86 on 2007-01-08
I'm having trouble getting the drivers for my GeForce TI 4200 working. When I use the "nv" driver I can get into the X windows but openGL isn't working. glxgears gives me this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I can't get into the X windows at all with the nvidia driver. It says something about the "kernel module does not appear to be receiving interrupts". I've been messing with it forever and I can't find any solution. ](*,)   I'm about to give up. Please help, and also, I'm really new to this Linux thing so please bear with me

---

### Post by spin2cool on 2007-01-08
I'd try to reinstall the drivers.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

Also check out this thread:
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by J86 on 2007-01-08
I now have a different problem. Now it says there was an "error running install command for nvidia"

---

### Post by J86 on 2007-01-08
So I reinstalled the OS and the drivers, now I'm back to the first problem. ](*,)

---

### Post by J86 on 2007-01-08
Please help. Is there anything that can be done?

 :confused:

---

### Post by cmost on 2007-01-08
Please post the steps you're taking to install the nVidia driver.
Also, try using the 'Envy' script to help you automate the process.  (Do a google search to find the download site for this...also note that the 'Envy' author has a repository for ready-made debs of the latest nvidia driver.)

---

### Post by J86 on 2007-01-08
First of all, Envy does not work. It just gets to me this 'kernel interrupt error' again.

And to install:
1. Downloaded all packages the installer wanted such as gcc-3.4, xorg-dev, xserver-xorg-dev.
2. Downloaded nVidia drivers version 1.0-7184. This is the version I was told to use when I tried a newer one.
3. sudo /etc/init.d/gdm stop
4. sudo sh <installer location>
5. sudo pico /etc/X11/xorg.conf, change "nv" to "nvidia", remove "load "dri""

I'm going to try my ATI card soon because I don't think this is ever going to work...

---

### Post by cmost on 2007-01-09
Can I suggest you run a live CD that includes the proprietary nVidia drivers?  If you can, download and try the latest Sabayon Linux 3.26 (just released) mini Edition CD.  They offer a full DVD too, but it's much larger and will take a long time to download.  Burn the Sabayon image to a Cd and boot the computer from it.  It should automate the installation of the nvidia driver and enable full 3D acceleration at boot time.  You'll even have a chance to try both XGL and AIGLX to see which one your system supports.  If this distro works as expected, then the problem lies with your current Ubuntu setup (either the kernel is damaged, or the sources; resulting in a non functioning module.)  If you get a similar error, or cannot use the included nvidia driver then I would suspect the problem lies somewhere in your particular mix of hardware.  I know this seems like a lot of work to test a nvidia card, but, it will be well worth it.

---

### Post by J86 on 2007-01-10
I downloaded the mini edition and I have no idea what to do with it; how to find out if the drivers are working. It starts at the command line (is it supposed to?). So I'm downloading the full edition DVD now...

---

### Post by J86 on 2007-01-12
I downloaded the full edition and it does exactly the same thing. While loading is showed some error message about "../nvidia.ko cannot be found". When I went to the "Start Quake 4 demo" option it also went straight to the command line...

---

### Post by J86 on 2007-01-13
Well, I've given up and reinstalled Windows XP. After I installed an ATI card and it wouldn't work either I decided that I'd had enough. The driver for both these cards work with a couple clicks in Windows and besides that, they actually work at all.

---

