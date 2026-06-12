---
title: "linux kernel-rt won't load xserver"
date: 2008-03-25
forum: General Help
---

### Post by guitarMan666 on 2008-03-25
I recently installed the ubuntustudio-desktop package.  It installed, among other things, a low latency kernel.

In my GRUB, the low latency kernel is the default.  However, when I try to boot into that option, the x server refuses to load.
I checked the detailed output and found the most useful information:

Error running install comand for Nvidia
Failed to Load Nvidia kernel module

When i get rid of the grey and blue screen, It leads to an inoperable console yielding still more error messages:
 
[timecode] Error microcode bcm43xx_microcode.fw not available or load failed

The time code changes each time.  The error seems related to my unused wireless card and doesn't appear when I load the generic kernel.
The above error repeats in what seems to be an infinite loop, forcing me to shut down, reboot and load the generic kernel (which works fine).

I've seen several people refer to running "sudo dpkg-reconfigure xserver-xorg" both with and without the -phigh option.  I want to know what this does (it seems to be hit or miss) before I try it because I don't want to screw over my good option.

Thank you all in advance for your help and your time.

---

### Post by pointone on 2008-03-25
"dpkg-reconfigure xserver-xorg" reconfigures the X.Org (GUI) configuration file, "/etc/X11/xorg.conf". This is not at all related to the problem you're having with kernel modules.

I'd suggest adding "blacklist bcm43xx" to the file "/etc/modprobe.d/blacklist" to prevent the "bcm43xx" kernel module from loading during boot.

---

### Post by guitarMan666 on 2008-03-25
Is there anything I can do about the kernel modules?

---

### Post by guitarMan666 on 2008-03-31
In more or less desperation, I ran Envy from the command line and I can now successfully boot one kernel or the other.

However, if I switch kernels, I have to run Envy again to install the proper kernel module for the kernel I want to boot (my options are generic and rt).

Is there a way to get around this and make it so both kernels boot interchangeably without running envy each time I want to use the other kernel?

---

### Post by jocko on 2008-03-31
> **guitarMan666 said:**
> In more or less desperation, I ran Envy from the command line and I can now successfully boot one kernel or the other.

However, if I switch kernels, I have to run Envy again to install the proper kernel module for the kernel I want to boot (my options are generic and rt).

Is there a way to get around this and make it so both kernels boot interchangeably without running envy each time I want to use the other kernel?

With envy, or any other manual install method, you will always have to rebuild the module for every different kernel version.
If you use the driver available through the repos you never need to rebuild anything, as the module will be loaded from the restricted modules. So as long as you have restricted modules for both kernels, everything should work.

---

### Post by guitarMan666 on 2008-03-31
That actually was what caused this problem to begin with.  I downloaded the nvidia-glx-legacy package which proceeded to cause a whole host of other problems that I successfully resolved.    

At some point a few weeks after that I downloaded the ubuntustudio-desktop package and when I tried to boot into the rt kernel I got the error that prompted my first post.

I'll try uninstalling (with envy) and then reinstalling thru the package manager and see if that changes anything, although I don't look forward to losing 3D at resolutions greater than 800 x 600.

---

### Post by guitarMan666 on 2008-04-01
I have no idea what happened but the problem seems to have resolved itself.  I uninstalled the driver in preperation to follow jocko's recommendation and had to reinstall it myself because my gui wouldn't load after reboot (obviously, no driver), reinstalled the driver with envy and when i accidentally booted into the rt kernel today (pressed wrong arrow key in GRUB) it works fine.
Thank you all for your advice and time

---

### Post by forrestcupp on 2008-04-01
> **guitarMan666 said:**
> I have no idea what happened but the problem seems to have resolved itself.  I uninstalled the driver in preperation to follow jocko's recommendation and had to reinstall it myself because my gui wouldn't load after reboot (obviously, no driver), reinstalled the driver with envy and when i accidentally booted into the rt kernel today (pressed wrong arrow key in GRUB) it works fine.
Thank you all for your advice and time

So did you use Envy from the rt kernel?  If so, it may not work with the generic one.  But if you got a newer version of Envy, I think he's been working with the Ubuntu devs to make it more Ubuntu compatible.

But what nvidia card are you using?  Your problem earlier may have been that you should have used nvidia-glx-new instead of the legacy one.  That's my suspicion because Envy doesn't support really old cards.

---

### Post by guitarMan666 on 2008-04-01
It is a fairly old card.   Windows reports it as an nVidia RIVA TNT/TNT2.  I used Envy 0.9.10.  

This latest time I ran envy under the generic kernel and that seems to be what led the card to work with both.

I just switched from the rt to the generic kernel and it works perfectly.  *shrugs* i'm not gonna complain about a good thing...but if you have any ideas that might help me duplicate this they would be welcome.

---

### Post by metrorat on 2008-04-03
Hi - I had exactly the same issue - had to run envy from recovery mode for each different kernel install.  The problem kept reappearing more or less at random.  Sorted it by running envy in the misbehaving kernel (i.e both) from recovery mode, rebooting, enabling the newly installed restricted driver from then gui then running ```
sudo dpkg-reconfigure -p high xserver-xorg
``` and manually reconfiguring the xserver using the assistant.  No problems after that (touch wood).

Seems envys auto-config of the xserver was somehow messing things up.  Until I did the above it was 50/50 whether the nvidia module (i think) would successfully load at boot in either kernel.

---

### Post by guitarMan666 on 2008-04-03
Thats interesting.  However the last time I tried to enable the restricted driver it didn't use the package that envy installed.  Instead, it attempted to download a driver package too new for my card and messed up everything again.  I guess I can try it this weekend and see if it works.

---

### Post by guitarMan666 on 2008-04-14
This has become a non-issue for me, I've swapped out my video card for an ATI Radeon 7500, which has brought with it it's own set of problems.  My thread regarding those troubles is located here: [http://ubuntuforums.org/showthread.php?t=754440](http://ubuntuforums.org/showthread.php?t=754440)

Thank you all for your valuable advice, before the upgrade I was able to get the nVidia card working in both kernels.

---

