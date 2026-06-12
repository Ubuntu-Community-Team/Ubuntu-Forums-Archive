---
title: "Login Loop (NVIDIA Drivers) [15.10]"
date: 2015-12-08
forum: General Help
---

### Post by SirMoo on 2015-12-08
I'm seeming to get stuck in a never ending login loop when I try to change the drivers to NVIDIA from the default.

I've tried multiple options and all result in the same method. The graphics card in question is a **NVIDIA GeForce GTX 960M** - I've tried multiple drivers and all seem to result in the login loop. I need some support on where to start trouble shooting this as everything I've tried (I've read a large amount of askubuntu/ubuntuforum posts that Google has suggested) and nothing has resulted in anything that's made a difference. 

For the sake of testing. Drivers currently installed at 355 based on this ppa: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 

Ubuntu is 15.10. 

Fresh install other than the graphics drivers.

---

### Post by QDR06VV9 on 2015-12-08
Lets see what we have installed if you would post back the results of
```
[COLOR=#111111][FONT=Consolas]dkms status[/FONT][/COLOR]
```

---

### Post by SirMoo on 2015-12-08
> **runrickus said:**
> Lets see what we have installed if you would post back the results of
```
[COLOR=#111111][FONT=Consolas]dkms status[/FONT][/COLOR]
```

```
bbswitch, 0.7, 4.2.0-19-generic, x86_64: installed
nvidia-355, 355.11, 4.2.0-19-generic, x86_64: installed
```

---

### Post by QDR06VV9 on 2015-12-08
Have you looked at this guide yet? I have had very good outcomes with method..
[http://rajat-osgyan.blogspot.com.au/2015/03/how-to-install-bumblebee-on-ubuntu.html](http://rajat-osgyan.blogspot.com.au/2015/03/how-to-install-bumblebee-on-ubuntu.html)

Post back if you need to.
Regards

---

### Post by SirMoo on 2015-12-08
> **runrickus said:**
> Have you looked at this guide yet? I have had very good outcomes with method..
[http://rajat-osgyan.blogspot.com.au/2015/03/how-to-install-bumblebee-on-ubuntu.html](http://rajat-osgyan.blogspot.com.au/2015/03/how-to-install-bumblebee-on-ubuntu.html)

Post back if you need to.
Regards

Progress! Woo! Ok, so the desktop is back. Under additional drivers it shows the correct drivers as being selected... However, under the system details it shows **Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits) **and not the actual graphics card. 

Running anything with the primus command gives me this error. 

```
E connect(5, AF=1 "/var/run/bumblebee.socket", 27): No such file or directory 
```

---

### Post by QDR06VV9 on 2015-12-09
What is the output of this now?
```
sudo cat /proc/acpi/bbswitch 
```
And forgot to mention that I noticed is If you switch from intel to nvidia, it works after a reboot

---

### Post by SirMoo on 2015-12-11
> **runrickus said:**
> what is the output of this now?
```
sudo cat /proc/acpi/bbswitch 
```
and forgot to mention that i noticed is if you switch from intel to nvidia, it works after a reboot

```
0000:02:00.0 on
```

---

### Post by SirMoo on 2015-12-14
So after doing all this, if I put the correct nvidia drivers in /bumblebee.conf I'm simply unable to login. It gets to the 5 white and orange dots and never progresses...

---

### Post by QDR06VV9 on 2015-12-14
Hi SirMoo
Well let us check on a couple of things,
What is the contents of this file?
```
gedit '/etc/modules' 
```

---

### Post by SirMoo on 2015-12-15
> **runrickus said:**
> Hi SirMoo
Well let us check on a couple of things,
What is the contents of this file?
```
gedit '/etc/modules' 
```

```
i915
bbswitch
```

---

### Post by QDR06VV9 on 2015-12-15
> **SirMoo said:**
> ```
i915
bbswitch
```

That looks good..

IMPORTANT TO NOTE THAT THERE IS A BUMBLEBEE BLACKLIST FILE BY DEFAULT IN THE FOLDER.
```
/etc/modprobe.d/

```
```
bumblebee.conf

```
Contents of this file are
> sudo cat /etc/modprobe.d/bumblebee.conf
# installed by bumblebee-nvidia
# to be used by kmod / module-init-tools, and installed in /etc/modprobe.d/
# or equivalent


# do not automatically load nouveau as it may prevent nvidia from loading
blacklist nouveau
# do not automatically load nvidia as it's unloaded anyway when bumblebeed
# starts and may fail bumblebeed to disable the card in a race condition.
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
# 304
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
# 310
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
# 313
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
# 319
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
# 325
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
# 331
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331
# 334
blacklist nvidia-334
blacklist nvidia-334-updates
blacklist nvidia-experimental-334
# 337
blacklist nvidia-337
blacklist nvidia-337-updates
blacklist nvidia-experimental-337
# 340
blacklist nvidia-340
blacklist nvidia-340-updates
blacklist nvidia-experimental-340
#343
blacklist nvidia-343
blacklist nvidia-343-updates
blacklist nvidia-experimental-343
> This is a problem specific to Ubuntu and its derivatives only.(Sorry for this earlier I posted that one needs to uncomment the Driver in above file which is not true.)
So if you see the contents of this file reveal that no matter what you do you can't get succes in getting bumbleebee work with any of the nvidia drivers unless you Ensure that your Driver is listed above and blacklisted. 
This will ensure that the driver Is not loaded automatically. If it loads automatically, **you will have a BLACK SCREEN at boot**.
Now you can edid the bumblebee.conf as below.


```
Sudo gedit /etc/bumblebee/bumblebee.conf

```
1. line 22:
Driver=nvidia


2. line 55:
KernelDriver=nvidia-331**(Your Driver Version)**


3. line 58:
LibraryPath=/usr/lib/nvidia-331:/usr/lib32/nvidia-331 **(Your Driver Version)**


4. line 61:
XorgModulePath=/usr/lib/nvidia-331/xorg,/usr/lib/xorg/modules **(Your Driver Version)**


5. Reinstall bbswitch-dkms:
```
sudo apt-get install --reinstall bbswitch-dkms

```
[B]Reboot
[/B]NOTE :- You neeed to make sure that you place the nvidia-355.11 with whatever driver version you have installed in previous steps and the one you uncommented from the bbswitch.conf file under /etc/modprobe.d/bumblebee.conf


Here is an Example  of what bumblebee.conf looks like.
> # Configuration file for Bumblebee. Values should **not** be put between quotes


## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d


## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false




# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
# bbswitch - new in BB 3, recommended if available
# switcheroo - vga_switcheroo method, use at your own risk
# none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)


## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-340
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-340:/usr/lib32/nvidia-340
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-340/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau


So please make changes to your files accordingly..
Now the final Reboot.
After the reboot you can now test
Run the command
```
primusrun glxinfo | grep OpenGL

```

---

### Post by SirMoo on 2015-12-16
> **runrickus said:**
> That looks good..

[..snip..]

Yes, I've done all that. 

The problem is that when it comes to editing the **bumblebee.conf  **and changing that driver to nvidia, once I modify the file... The system will no longer boot properly and thus result in a black screen with dots... It will even lock me out of using ttyl. It seems to freeze.

---

### Post by QDR06VV9 on 2015-12-16
If you are still seeing this <[B]Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits) >

[/B]You might need some extra DKMS packages "LTS Enablement Stack"
```
 sudo apt-get install --install-recommends linux-generic-lts-wily 

```
And be sure you add yourself to the bumblebee group:
As Root
```
# addgroup <your_username_here> bumblebee

```
Try with the above^^^first.
Now if all that fails
[COLOR=#ff0000]**WARNING YOU ARE ON YOUR OWN HERE**[/COLOR]
And some have reported that with systemd they had to set a delay in the grub-line
As root, open /etc/default/grub, find 

**GRUB_CMDLINE_LINUX_DEFAULT**, and append "**rcutree.rcu_idle_gp_delay=1**" to it. Regenerate the boot image:
```
sudo update-grub
```

---

### Post by SirMoo on 2015-12-29
> **runrickus said:**
> If you are still seeing this <[B]Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits) >

[/B]You might need some extra DKMS packages "LTS Enablement Stack"
```
 sudo apt-get install --install-recommends linux-generic-lts-wily 

```
And be sure you add yourself to the bumblebee group:
As Root
```
# addgroup <your_username_here> bumblebee

```
Try with the above^^^first.
Now if all that fails
[COLOR=#ff0000]**WARNING YOU ARE ON YOUR OWN HERE**[/COLOR]
And some have reported that with systemd they had to set a delay in the grub-line
As root, open /etc/default/grub, find 

**GRUB_CMDLINE_LINUX_DEFAULT**, and append "**rcutree.rcu_idle_gp_delay=1**" to it. Regenerate the boot image:
```
sudo update-grub
```

Once again, same result of it loads, but doesn't get past the ubutnu logo with the dots... when bumblebee.conf has is set to nvidia I can't seem to get things to work. :/

---

