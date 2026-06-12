---
title: "How to debug: Firefox &quot;Failed to open VDPAU backend libvdpau_nouveau.so&quot;"
date: 2013-12-03
forum: General Help
---

### Post by Jim_Granite on 2013-12-03
$ uname -m
x86_64

$ lsb_release -c
Codename:       saucy

Firefox crashes
The xterminal it was opened in says:
```

 Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: 
 No such file or directory
 NOTE: child process received `Goodbye', closing down
 [1]+  Done  firefox
```

$ dmesg
REPORTS:
```

[33739.540311] nouveau E[  PGRAPH][0000:01:00.0] DATA_ERROR INVALID_VALUE
[33739.540320] nouveau E[  PGRAPH][0000:01:00.0]  DATA_ERROR
[33739.540326] nouveau E[  PGRAPH][0000:01:00.0] ch 6 [0x003f7d8000 totem[5847]] subc 3 class 0x8597 mthd 0x0e04 data 0xfda20000

```

Any debugging ideas?

EDIT: Googling for "VDPAU", it's apparently **Video Decode and Presentation API for Unix**, which is an open-source library (*libvdpau*) and API for Nvidia for its [GeForce 8 series]("http://en.wikipedia.org/wiki/GeForce_8_series") (which I have in my IBM W510) which lets Nvidia cards play video with hardware acceleration.

---

### Post by mc4man on 2013-12-03
> Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: 
No such file or directory
that's a normal message from flashplayer when using nouveau in Ubuntu as vdpau in nouveau isn't enabled as far as  I know.
(so no libvdpau_nouveau.so is installed

I see it here if running FF from terminal on my nouveau machine & playing a flash video, it's harmless
(more info on nouveau & vdpau here inc. notes on extracting firmware to enable though not sure how much advantage there would be for nvidia 8000 series
[http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)

Likely some other reason FF is crashing, what are the circumstances & is there a crash file for FF in /var/crash?

Edit : or are you using the nvidia driver, not nouveau

---

### Post by Jim_Granite on 2013-12-04
> **mc4man said:**
> is there a crash file for FF in /var/crash?
There are a few files in /var/crash that I've no idea what they are:
```

$ ls -l
total 129488
-rw-r----- 1 root     whoopsie  1209939 Nov 26 17:51 susres.2013-11-26_16:33:17.391255.crash
-rw-r--r-- 1 root     whoopsie        0 Nov 26 17:51 susres.2013-11-26_16:33:17.391255.upload
-rw------- 1 whoopsie whoopsie        0 Nov 26 19:34 susres.2013-11-26_16:33:17.391255.uploaded
-rw-r----- 1 root     whoopsie 13015527 Nov 30 08:48 _usr_bin_Xorg.0.crash
-rw-r--r-- 1 root     whoopsie        0 Nov 30 08:48 _usr_bin_Xorg.0.upload
-rw------- 1 whoopsie whoopsie        0 Nov 30 09:28 _usr_bin_Xorg.0.uploaded
-rw-r----- 1 usr1     whoopsie 28754516 Dec  3 21:44 _usr_lib_firefox_plugin-container.1000.crash
-rw-r--r-- 1 usr1     whoopsie        0 Dec  3 21:44 _usr_lib_firefox_plugin-container.1000.upload
-rw------- 1 whoopsie whoopsie        0 Dec  3 21:55 _usr_lib_firefox_plugin-container.1000.uploaded
-rw-r----- 1 usr1     whoopsie   303046 Dec  2 08:43 _usr_lib_gvfs_gvfsd-mtp.1000.crash
-rw-r--r-- 1 usr1     whoopsie        0 Dec  2 08:43 _usr_lib_gvfs_gvfsd-mtp.1000.upload
-rw------- 1 whoopsie whoopsie        0 Dec  2 10:06 _usr_lib_gvfs_gvfsd-mtp.1000.uploaded
-rw-r----- 1 usr1     whoopsie 89303144 Dec  2 14:47 _usr_lib_thunderbird_thunderbird.1000.crash
-rw-r--r-- 1 usr1     whoopsie        0 Dec  2 14:47 _usr_lib_thunderbird_thunderbird.1000.upload
-rw------- 1 whoopsie whoopsie        0 Dec  2 16:13 _usr_lib_thunderbird_thunderbird.1000.uploaded

```

> **mc4man said:**
> or are you using the nvidia driver, not nouveau

I *do* have an Nvidia gforce card, so, I *should* probably be using the Nvidia driver but I'm not sure *what* driver I'm using.
Googling, I see I should look in /etc/X11/xorg.conf but I don't even have that file:
```

$ sudo updatedb
$ locate xorg.conf
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/(where a bunch of files are found in this directory)
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/man/man5/xorg.conf.d.5.gz
```

I'll google some more to find out how to figure out what drivers I'm using on the Lenovo W510 laptop.

EDIT: OK. So it's ungodly complicated, unnecessarily complex, and, Ubuntu is exceedingly offbeat when it comes to init levels (can you tell I'm frustrated?).

EDIT: The Lenovo website doesn't supply *any* drivers for Linux for the W510 laptop:
[http://support.lenovo.com/en_US/research/hints-or-tips/detail.page?&DocID=HT063291](http://support.lenovo.com/en_US/research/hints-or-tips/detail.page?&DocID=HT063291)

EDIT: Googling for how to find what graphics card I have, [I find this command]("http://http://www.cyberciti.biz/faq/linux-tell-which-graphics-vga-card-installed/"):
```

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GT216GLM [Quadro FX 880M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
```

OK. So I have the Quadro FX 880M Nvidia graphics card in my Lenovo W510 laptop.
Nvidia [says here to never use nouveau drivers]("http://us.download.nvidia.com/XFree86/Linux-x86_64/331.20/README/commonproblems.html#nouveau")!
> 
** What is Nouveau, and why do I need to disable it?**
    
Nouveau is a display driver for NVIDIA GPUs, developed as an open-source project through reverse-engineering of the NVIDIA driver. It ships with many current Linux distributions as the default display driver for NVIDIA hardware. It is not developed or supported by NVIDIA, and is not related to the NVIDIA driver, other than the fact that both Nouveau and the NVIDIA driver are capable of driving NVIDIA GPUs. Only one driver can control a GPU at a time, so if a GPU is being driven by the Nouveau driver, Nouveau must be disabled before installing the NVIDIA driver.

Nouveau performs modesets in the kernel. This can make disabling Nouveau difficult, as the kernel modeset is used to display a framebuffer console, which means that Nouveau will be in use even if X is not running. As long as Nouveau is in use, its kernel module cannot be unloaded, which will prevent the NVIDIA kernel module from loading. It is therefore important to make sure that Nouveau's kernel modesetting is disabled before installing the NVIDIA driver.
    
** How do I prevent Nouveau from loading and performing a kernel modeset?**
    
A simple way to prevent Nouveau from loading and performing a kernel modeset is to add configuration directives for the module loader to a file in one of the system's module loader configuration directories: for example, /etc/modprobe.d/ or /usr/local/modprobe.d. These configuration directives can technically be added to any file in these directories, but many of the existing files in these directories are provided and maintained by your distributor, which may from time to time provide updated configuration files which could conflict with your changes. Therefore, it is recommended to create a new file, for example, /etc/modprobe.d/disable-nouveau.conf, rather than editing one of the existing files, such as the popular /etc/modprobe.d/blacklist.conf. Note that some module loaders will only look for configuration directives in files whose names end with .conf, so if you are creating a new file, make sure its name ends with .conf.

Whether you choose to create a new file or edit an existing one, the following two lines will need to be added:

blacklist nouveau
options nouveau modeset=0

The first line will prevent Nouveau's kernel module from loading automatically at boot. It will not prevent manual loading of the module, and it will not prevent the X server from loading the kernel module; see "How do I prevent the X server from loading Nouveau?" below. The second line will prevent Nouveau from doing a kernel modeset. Without the kernel modeset, it is possible to unload Nouveau's kernel module, in the event that it is accidentally or intentionally loaded.

You will need to reboot your system after adding these configuration directives in order for them to take effect.

If nvidia-installer detects Nouveau is in use by the system, it will offer to create such a modprobe configuration file to disable Nouveau.


EDIT: It's ungodly complicated, but, maybe I now have enough information to download the proper Nvidia drivers:
 [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Product Type = **Quadro**
Product Series = **Quadro FX Series (Notebooks)**
Product = **Quadro FX 880M**
Operating System = **Linux 64-bit**
Download Type = **Linux Long Lived Driver**
Language = **English (US)**

That enabled me to download a driver for:
                                     **Linux x64 (AMD64/EM64T) Display Driver**
Version = 331.20
Release Date - 2013.11.6
Operating System = Linux 64-bit
Language = English (US)
File Size = 60 MB
                                 
                                                                                                               [TABLE]
[TR]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[/TR]
[TR]
[TD][/TD]
[TD="colspan: 2"][/TD]
[/TR]
[TR]
[TD][/TD]
[TD="colspan: 2"][/TD]
[/TR]
[TR]
[TD="colspan: 2"][/TD]
[/TR]
[/TABLE]
EDIT: The file downloaded from Nvidia was:
```
$ ls -l 
usr1 60012677 Dec  4 02:58 NVIDIA-Linux-x86_64-331.20.run
```

But, it wouldn't run because X was running:
```

$ sudo sh NVIDIA-Linux-x86_64-331.20.run
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID
   '1041' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before
       installing.  For further details, please see the section INSTALLING
       THE NVIDIA DRIVER in the README available on the Linux driver
       download page at www.nvidia.com.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.

```

Now it gets unnecessarily complicated on the Ubuntu side.

The Nvidia help on booting to a command-line only interface is basically useless because it discusses all Linuxes other than Ubuntu (simply because Ubuntu is apparently different than all Linuxes in this regard):
Booting to a different runlevel on most Linux distributions (not Ubuntu!)
 ```
runlevel 0 (system halt)
 runlevel 1 (debugging/recovery mode)
 runlevel 2 (user defined)
 runlevel 3 (command line with networking) <=== normally you'd use this
 runlevel 4 (user defined)
 runlevel 5 (starts the X window system)
 runlevel 6 (system reboot)
```

If this were any other Linux other than Ubuntu, life would be easy as I would just execute:
```

sudo init 3

```

However, I soon find out, [after reading this]("http://ubuntuforums.org/showthread.php?t=843646"),  that Ubuntu makes it difficult to get into the normal runlevel 3 (which  isn't runlevel 3 in Ubuntu, it's runlevel 5 in Ubuntu).
** This is, apparently, what Ubuntu uses for run levels:**
 ```
runlevel 0 (system halt)
 runlevel 1 (debuging/recovery mode)
 runlevel 2 (for full graphical mode, i.e., as runlevel 5)
 runlevel 3 (Ubuntu uses as runlevel 5)
 runlevel 4 (Ubuntu uses as runlevel 5)
 runlevel 5 (Ubuntu uses as runlevel 5)
 runlevel 6 (system reboot)
```

So, in order to install the right drivers, I have to now figure out how to boot to the command line, which doesn't exist, by default on Ubuntu (apparently). Sigh.
This is, IMHO, way too complicated for just a simple driver installation; but I guess it is what it is.
WIP WIP WIP work in progress ...

---

### Post by mc4man on 2013-12-04
I no longer use nividia drivers here on my current laptop (lenovo with 660m/optimus) as the intel side works quite well
(and I can enable hwacell thru vdpau for some players &  FF > flash

In any event your Quadro FX 880M isn't optimus so the nvidia drivers should be ok. 
There are many threads about how to manually install nvidia drivers, a quick google site search should supply instructions  (not that complicated to do.

Did you ck Software & Updates > Additional Drivers tab to see what's avail. in 13.10 for you ?
Or in synaptic, seach nvidia

(I know the 331 package is up in 14.04 dev, not sure if 13.10 has it or  if 319 is the latest in 13.10. No idea if 319 is good for your card..

Ultimately if you stick with Ubuntu you'll want 14.04 when released as 13.10 & 13.04 are short term 'point in time' releases with issues that may or may not get fixed


Edit
The _usr_lib_firefox_plugin-container.1000.crash is likely relevant. Just before and after release crashers are sent to a db rather than open Launchpad reports
If you were right click on the file > open with 'report a problem', not click on "Continue"  but instead on "Show Details" you may get something of interest..

---

### Post by Jim_Granite on 2013-12-04
> **mc4man said:**
> install nvidia drivers... not that complicated Heh heh ... :) I guess if you already know **how to get to init 3** in Ubuntu, then that knocks out a major complication. Also, if you alreday know **how to set up apt-get to install the driver**, that knocks out another complication. And, of course, if you already knew how to tell what **hardware and drivers you have** on your system, that too would knock out some of the research effort. Lastly, if you could trust that **a howto would cover your system**, that would help immensly (all the ones I tried failed miserably,[ including the Nvidia installation instructions]("http://us.download.nvidia.com/XFree86/Linux-x86_64/331.20/README/faq.html"), which clearly were never tested on Ubuntu, and even the [multiple]("http://askubuntu.com/questions/228402/boot-to-runlevel-3") [Ubuntu instructions]("http://ubuntuforums.org/showthread.php?t=843646"), which just as clearly can't work on 13.10).

  [ATTACH=CONFIG]248346[/ATTACH][ATTACH=CONFIG]248349[/ATTACH] 

So, in summary, if you already know how to do it, sure, it's not all that complicated. :) Or, if you find a tutorial that actually matches what's on 3.10, then I'm sure it's not all that complicated.  However I havn't found a single howto that works yet for my 13.10 Ubuntu OS, and, certainly I have to research a lot just to run the installer provided by Nvidia.  (That's not necessarily a bad thing - but - installing a driver nowadays shouldn't have to take days of effort.) 

 > **mc4man said:**
> Did you ck Software & Updates > Additional Drivers tab to see what's avail. in 13.10 for you ? 

Here is what that application is telling me is current. 
[ATTACH=CONFIG]248348[/ATTACH] 
```

Ubuntu Software & Updates->Additional Drivers->NVIDIA Corporation->GT26GLM [Quadro FX 880M]
Using X.Org X server Nouveau display driver
 (o) from xserver-xorg-video-nouveau (open source) <== changed this
Using NVIDIA binary Xorg driver, kernel module, & VDPAU library
 ( ) from nvidia-319 (proprietary, tested)
 (o) from nvidia-319-updates (proprietary) <== to this
 ( ) from nvidia-304-updates (proprietary)
 ( ) from nvidia-304 (proprietary)

```

This is taking a very long time (30 minutes and counting); so I'll update to let you know if this older version of the driver worked to solve the problem.
[ATTACH=CONFIG]248351[/ATTACH]

---

### Post by Jim_Granite on 2013-12-05
Thanks for all the help. It will take a couple of days to be sure, but, I *think* installing the penultimate Nvidia driver fixed the problem.

---

### Post by Jim_Granite on 2013-12-08
To report back, the problem does not seem to have returned, so, I will mark this as solved.
All the details of everything I tried I already put in the thread, so, others may use this as a reference for similar problems in the future.

Thanks everyone for all your kind help, which I much appreciate!

---

