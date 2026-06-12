---
title: "Cannot install nvidia-glx-new in hardy x86_64"
date: 2008-06-22
forum: General Help
---

### Post by bogdanbiv on 2008-06-22
My system is Kubuntu 8.04, vers x86_64
uname -a results: "Linux bog-desktop 2.6.24-19-generic #1 SMP i686 [..]"
Graphics card: I have Nvidia 8500gt
current graphics driver: xserver-xorg-video-nv

Instaling nvidia-glx-new (169.12 + 2.6.24.13-) renders my xserver unusable. The system starts the xserver in failsafe mode and then launches displayconfig-gtk. 
After I select the VGA+monitor model in displayconfig-gtk, I reboot and everything is normal (but without hardware acceleration)

When I run "kdesu /usr/bin/jockey-kde" and enable the binary driver it also downloads nvidia-glx-new, but the effect seems to be the same: upon reboot, xserver fails, enters failsafe mode and starts displayconfig-gtk. After I select Nvidia "Geforce 8" and Samsung model numbers I save and upon reboot I am back at xserver-xorg-video-nv


Excerpt from system log:
06/22/2008 03:16:09 PM	bog-desktop	kdm[5106]	Failed to start X server. Starting failsafe X server.

06/22/2008 03:16:09 PM	bog-desktop	kdm[5106]	X server died during startup

06/22/2008 03:16:09 PM	bog-desktop	kdm[5106]	X server terminated: [1, 0, 1]

I guess th xserver log was cleared upon reboot, as it is empty. Why was it cleared? how do I save it?
(by the way: I had to manually install displayconfig-gtk, it was not installed by default)

What am I missing?

---

### Post by Zorael on 2008-06-22
X's own log file is at **/var/log/Xorg.0.log**. It gets overwritten if you pick another driver in the failsafey window that pops up, so might be better to refer to **Xorg.0.log.old** in the same directory.

These commands take care of most Nvidia driver issues, but certainly not all.
```
$ sudo aptitude purge ~nnvidia-glx
$ sudo aptitude install nvidia-glx-new
```

---

### Post by bogdanbiv on 2008-06-22
**From /var/log/Xorg.0.log.old:**
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

**sudo aptitude purge ~nnvidia-glx**

The following packages will be REMOVED:
  nvidia-glx{p} nvidia-glx-new{p} nvidia-glx-new-envy{p}
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 15.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 191448 files and directories currently installed.)
Removing nvidia-glx ...
Purging configuration files for nvidia-glx ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Removing nvidia-glx-new ...
Purging configuration files for nvidia-glx-new ...
Removing nvidia-glx-new-envy ...
Purging configuration files for nvidia-glx-new-envy ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by Zorael on 2008-06-22
Sounds about right. Enter those commands and see if things improve.

---

### Post by bogdanbiv on 2008-06-22
Unfortunately, 3d acceleration still does not work.
/usr/bin/jockey-kde reports that I am not using nvidia restricted drivers.

3d games start, hang around showing the waiting cursor, but then close silently.

Here's the output from openarena started from konsole:
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 8: 1280 1024
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
[...]
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (8)
Initializing OpenGL display
...setting mode 3: 640 480
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: ...
[...]
                               ...find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by ddales on 2008-06-22
System > Administration > Hardware Drivers
Check the NVidia drivers and let it do it's thing.  The drivers will be installed and you have to reboot.

I like to install the NVidia Setting package as well which makes things really easy to adjust.

sudo apt-get install nvidia-settings
sudo nvidia-settings

Note:  If you try to use nvidia-settings from the System > Administration > NVidia X Server Settings as a regular user, it won't work unless you give your users write access to the /etc/X11 directory.

---

### Post by Zorael on 2008-06-22
I'm sorry, did you enter the second command? You seem to have properly uninstalled it but your code tag didn't show you installing it again.

---

### Post by bogdanbiv on 2008-06-22
Solved it.
It seems that I was missing the right kernel modules.
I installed the NVIDIA-Linux-x86-173.14.09.pkg1.run driver from nVidia's site.
It did download and build the right modules.

This is where I started to try to configure my drivers:
System > Administration > Hardware Drivers
(it's the same as /usr/bin/jockey-kde)

After installing:
$ sudo aptitude install nvidia-glx-new
it kept complaining that it lacks the right modules (I presume kernel modules).
I had installed nvidia kernel modules earlier, I guess those weren't the right ones..

---

