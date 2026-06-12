---
title: "nvidia-glx-new problem - tried everything posted (?)"
date: 2007-10-07
forum: General Help
---

### Post by farmfield on 2007-10-07
So I guess we're a lot of folks who got prob's with the nvidia-glx-new...

I personally knew about the problem so I didn't update to the new kernel and all that crap, but then I was tricked into it when installing nvidia-glx-new (which installed the kernel as a dependancy) - the words I think of now I cannot write without being banned from this forum!

In my case I can't activate the driver, everytime I try, after reboot/logoff it stalls & blinks a few times at *"Running local boot scripts (/etc/rc.local/)"* and then goes into failsafe/low graphics mode. From there the only way to get into the desktop is to click always run low graphics mode, everything else will kick me back to *"Running local boot scripts (/etc/rc.local/)"* and then the failsafe/low graphics mode... And the only thing I want is to be able to run my desktop in 1440x900 - no tv-out or anything is of interest...

I tried to remove/purge/uninstall the nvidia-glx & nvidia-glx-new in any way I can think of, from the terminal and from Synaptics - and nothing seem to work... As the driver never gets loaded it's no use manipulating xorg.conf either, something I became good at trying to solve the *tv-out-compiz-window decoration-issue*...

Anybody have any ideas? Only way I can get my desktop to 1440x900@60 is to run the NV driver which kinda feel like running a new Ferrari on wooden carriage wheels... =(

---

### Post by ZipoTe on 2007-10-07
Install nvidia official drivers by downloading them from the website. Seriously guys, if you want cool features as compiz, beryl or whatever, use official drivers and install them **YOURSELF** I know there is envy but.. well, i don't really like it, too many headaches.

---

### Post by farmfield on 2007-10-07
I tried that but the installer complained about the x-server running... And yes, I'm so stupid I haven't figured out how to end the gui to get to the pure command line interface as yet, hehe...

So how do I do this in the simplest way?

---

### Post by ZipoTe on 2007-10-07
> **farmfield said:**
> ... And yes, I'm so stupid I haven't figured out how to end the gui to get to the pure command line interface as yet, hehe... :lolflag: ok ok, just ask :-P

to stop the X server (i suppose you are running gnome):
/etc/init.d/gdm stop

and this to start

/etc/init.d/gdm start

---

### Post by DagMan on 2007-10-07
First uninstall the nvidia-glx stuff.  Select compete uninstall or whatever the option is in synaptic.  Then download the NVIDA linux driver for youre arch, 32 or 64 bit or whatever, it will be a file called NVIDIAsomethingsomething.run
Move that file to your home directory
back up your xorg.conf
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup**
now youre going to kiss your graphics goodbye which is the x thing it was complaining about. so write this down if you have a short memory like me.
Hit **ctrl-alt-f1** on the keyboard
type:
**sudo /etc/init.d/gdm stop**
**sudo sh NVIDIA*run**
follow the instructions and when it asks you about updating the xorg file select yes.
to get your gui back, 
**sudo /etc/init.d/gdm start**

Edit: Or you can just use the easier instuctions that Zipo te posted :p

---

### Post by farmfield on 2007-10-07
So that got me far, but not far enough...

The installer asks for a kernel which it proposes to download, fails and then proposes to kompile and then says the "Libc header files" are missing..?

---

### Post by farmfield on 2007-10-07
Here ya'go...

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Oct  7 15:40:23 2007

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by farmfield on 2007-10-07
Isn't there anyway I can try to enable the **nvidia-glx-new** from the terminal?

---

### Post by bodhi.zazen on 2007-10-07
What driver were you using before ?

You can try to re-configure X with:

```
sudo dpkg-reconfigure xserver-xorg
```

FYI the nvidia-glx-new module is a pain to remove, it is a known bug but it has not been resolved.

I can walk you through it if you like, thus my first question.

---

### Post by jocko on 2007-10-07
The easiest way of getting the nvidia driver installed and working is the restricted manager.
It will make sure you have everything you need and make the appropriate changes in /etc/X11/xorg.conf.

A manual install using nvidias installer (or using envy) should work fine as well, but you'll need to install a few things first (build-essential and linux-headers for your running kernel).
And if you install manually you will need to reinstall every time the kernel is updated.

---

### Post by bodhi.zazen on 2007-10-07
> **jocko said:**
> The easiest way of getting the nvidia driver installed and working is the restricted manager.
It will make sure you have everything you need and make the appropriate changes in /etc/X11/xorg.conf.

A manual install using nvidias installer (or using envy) should work fine as well, but you'll need to install a few things first (build-essential and linux-headers for your running kernel).
And if you install manually you will need to reinstall every time the kernel is updated.

Yes, but farmfield can not run the manager as X has failed.

And now with nvidia-glx-new installed it will not be so easy to install the nvidia driver with envy or directly from nvidia as there is a bug with nvidia-glx-new, so it is not going to be so simple ...

@farmfield: The other option is to choose the vesa driver when you re-configure with a low resolution. This will allow you to work in X if you prefer ....

---

### Post by ZipoTe on 2007-10-07
yeeeah, glx-new is a headache but i didn't know it was a bug... so what can he do with glx-new?

---

### Post by jocko on 2007-10-07
> **bodhi.zazen said:**
> Yes, but farmfield can not run the manager as X has failed.

And now with nvidia-glx-new installed it will not be so easy to install the nvidia driver with envy or directly from nvidia as there is a bug with nvidia-glx-new, so it is not going to be so simple ...

@farmfield: The other option is to choose the vesa driver when you re-configure with a low resolution. This will allow you to work in X if you prefer ....

I think the restricted manager will work even without x:
```
sudo restricted-manager --enable=nvidia_new
```Edit: I may have been wrong, maybe x is required for the restricted-manager.
I tried it myself and got complaints about gtk2 libraries followed by a segmentation fault...

But it's always possible to set xorg to use vesa or nv, so that you can start x and use the restricted-manager.
I seem to remember a bug with nvidia-glx or nvidia-glx-new that caused the wrong version of the module to be loaded.
The fix was a complete uninstall and reinstall of the restricted-modules.

---

### Post by bodhi.zazen on 2007-10-07
> **jocko said:**
> I think the restricted manager will work even without x:
```
sudo restricted-manager --enable=nvidia_new
```Edit: I may have been wrong, maybe x is required for the restricted-manager.
I tried it myself and got complaints about gtk2 libraries followed by a segmentation fault...

But it's always possible to set xorg to use vesa or nv, so that you can start x and use the restricted-manager.
I seem to remember a bug with nvidia-glx or nvidia-glx-new that caused the wrong version of the module to be loaded.
The fix was a complete uninstall and reinstall of the restricted-modules.

No, there is an easier way.

Purge nvidia-glx-new

```
sudo apt-get remove --purge nvidia-glx nvidia-glx-new
```

Then remove this file ```
sudo rm /lib/linux-restricted-modules/.nvidia-new-installed
```

Or sudo rm /lib/linux-restricted-modules/.nvidia.new.installed

Then, re-install the nvidia (propriarty) driver ...

---

### Post by farmfield on 2007-10-07
Well, my solution wasn't to purge the driver, I purged Gutsy and the driver with it, hehe...

This wasn't because of the graphics though, everything stopped working, graphices, sound, DVD-RW a.s.o...

It was really stupid of me to upgrade in the first place, I actually need to work on this box, hehe, and should have waited unleast until the official release or even a bit after...

Sorry to have caused you work w/o taking advantage of it myself but hopefully this will help others... =)

Best Rgds/Johnny-Boy

---

### Post by ZipoTe on 2007-10-07
:lolflag:

don't worry that's why forums exists :)

---

### Post by farmfield on 2007-10-07
> **bodhi.zazen said:**
> Yes, but farmfield can not run the manager as X has failed.

"Well, that isn't entirely true Mr. president..." (ID4)

I just changed driver to Vesa in xorg.conf so I could always access the gui... :)

...didn't do me much good though as everything was failing anyway - like in an episode of ER, me trying to resuscitate my failing computer... Sound, DVD-RW, everything was gone... :( ...beeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee "Call it! Time of death, 3.02pm"...

---

