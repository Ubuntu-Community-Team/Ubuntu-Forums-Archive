---
title: "X Server Failed to Start"
date: 2007-05-24
forum: General Help
---

### Post by Plantmiester on 2007-05-24
I just finished installing 7.04, and had just Nvidia accelerated drivers:

```
#sudo apt-get install nvidia-glx-nvidia kernel common
#sudo nvidia-glx-config enable
```

Now I can't load X server at all.  I get the following message:

```
Failed to start the X server (Your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?
```

Upon viewing that I see

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux <user>-desktop 2.6.20-15-generic #2
SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
     Before reporting problems, check http://wiki.x.org
     to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
               (++) from command line, (!!) notice, (II) informational,
               (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 24 20:20:35 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found
```

After that I'm asked if I want to view the detailed X server output.  That gives me much the same header, but the body is more indepth, but I can't figure out any more vital information.

I'm running a Samsung SyncMaster 940BW with a NVidia GeForce 4Ti 4200.  I'm not going to lie, I'm not that great with Linux as of yet.  I'm pretty familiar with using X, and working from there, but I have no idea how to solve issues outside of X.

Any explanation and solution would be greatly appreciated.

---

### Post by gustavoberman on 2007-05-24
try to reconfigure your xserver. at the console type:

sudo dpkg-reconfigure xserver-xorg

and follow instructions

---

### Post by Plantmiester on 2007-05-24
Okay, I'm in the confg, but I'm not 100% sure which steps I need to really work with.  Several steps are a bit above my ability (determining P/S2 type etc).  Any hints in regards to that?

---

### Post by ryanVickers on 2007-05-24
The drivers change this file to activate the GPU.  They can also someetimes corrupt the file.  Just replace it with your backup.  You did make one right? :)

Actually, if you didn't, sorry, that's not funny.  Try to find a auto-created thing, probably is hidden and has a ~ before/after the name.  Best of luck!

---

### Post by Plantmiester on 2007-05-24
Gustavoberman, thank you.  I'm not sure what, out of all my value entering, actually solved the problem, but somewhere in that config, something went right.  Again, thank you.

---

### Post by gustavoberman on 2007-05-24
you are welcome my friend!
at the xserver reconfigure most options defaults work great

---

### Post by Plantmiester on 2007-05-24
Okay, new issue.

I'm running on Restricted Drivers, and I would really like to boost my resolution to closer to my usual 1440x960.  Does anyone know how to get the official NVidia drivers to work?

I attempted to install them already, and apparently my GeForce 4 isn't an NVidia GPU.

Okay, so I just installed a different set of drivers outside X, and it will no longer start.

Here are the errors:

```
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
dlopen: /usr/lib/xorg/modules/drivers//nvidia_drv.so: invalid ELF header
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found
```

I ran X reconfig, and that did nothing.  The install DID make a backup, but I have no clue where that would be.

---

### Post by kolanos on 2007-05-25
Sometimes a motherboards AGP modules can get in the way (via_agp, asus_agp, etc.).

You could always try the following, open your /etc/X11/xorg.conf config file (might be wise to back it up first), and under

Section "Device"

add the following:

Option "NvAGP" "3"

just make sure you add it before the "EndSection" part.

Then save your xorg.conf and restart gdm ("sudo /etc/init.d/gdm start").

If that works then it means agpgart and your motherboards agp module are causing the problem. You can Google "agpgart" for information on how to blacklist these modules.

Hope that helps.

---

### Post by Plantmiester on 2007-05-25
That solution didn't seem to solve anything, but I do have a new error in the X report.

```
Parse error on line 86 of section Device in file /etc/X11/xorg.config
         "NvAGP" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
```

---

### Post by ryanVickers on 2007-05-25
It may not be detecting the card because it's using the legacy driver.  Maybe.

My resolution would also not go above 1024x768 when it's capable of 1280x1024.  I went into my xorg.conf file and added sections onto all the resolutions with my number in them, like this:

> "1280x1024@75" "1024x768@55" "800x600@59" "640x480@63"

But when I installed the drivers, it added a bunch more and that further mixed the problem, but see if this helps (oh, I actually had to reboot for this to take effect! :))

---

### Post by Plantmiester on 2007-05-25
Okay, on preliminary check, that didn't do anything.  On the other hand, I didn't have a list of refresh rates at specific resolutions, I was only given "depths" and the resolution available at any given depth.

I'm not sure about the depth thing so that could probably do with some explanation.  On top of that if adding refreshrates to that line, or to another line is the best solution.

---

### Post by Plantmiester on 2007-05-26
Still stuck, but I'm wondering if anyone knows what the default "restricted" drivers are that I should enter in the driver section, or how I'm to find the backup files that have been made by Nvidia install, and myself (I'm unclear as to how to view the contents of a folder in Terminal).

---

### Post by hegex on 2007-05-28
I had the same problem in my laptop and i noticed, i made install from desktop-cd with boot parament acpi=off. Now my kernels always try to open with that parament. i read nvidias document *(the README.txt if you are installed the driver from the nvidias pages. Else in README.txt.gz file)* and i found solution from the "common problems" section.  So as you maybe got my point, the problem was the "acpi=off". Remove it and try again. if that wont help you try "noapic" option at boot. That helped me out.

Good luck! :)

---

