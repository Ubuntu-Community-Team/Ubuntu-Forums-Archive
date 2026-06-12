---
title: "Graphics Problems after replacing GPU"
date: 2016-02-23
forum: General Help
---

### Post by bizhat on 2016-02-23
Hi,

After changing NVIDIA GPU, rsolution is too low, i already had a differnt NVIDIA GPU model, it worked with open source driver.

I tried running 

```

dpkg-reconfigure xserver-xorg-video-nouveau

```

But it did not work. What is the proper way to get GPU detected ?

lshw -C Video shows 

```

  *-display UNCLAIMED
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff

```

I got it fixed by installing NVIDIA driver (nvidia-352).

Now desktop graphics work properly.

```

  *-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:76 memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff

```

I have no xorg.conf in /etc/X11 folder. It is not really needed ? What is the purpose of it, if it is working properly with out it ?

```

root@hon-pc-01:/etc/X11# ls -lah
total 109M
drwxr-xr-x  11 root root 4.0K Feb 23 21:51 .
drwxr-xr-x 151 root root  12K Feb 23 21:47 ..
drwxr-xr-x   2 root root 4.0K Apr 17  2014 app-defaults
-rw-------   1 root root 110M Feb 20 22:03 core
drwxr-xr-x   2 root root 4.0K Apr 17  2014 cursors
-rw-r--r--   1 root root   18 Apr 17  2014 default-display-manager
drwxr-xr-x   4 root root 4.0K Apr 17  2014 fonts
-rw-r--r--   1 root root  17K Dec  3  2009 rgb.txt
lrwxrwxrwx   1 root root   13 May 13  2014 X -> /usr/bin/Xorg
drwxr-xr-x   2 root root 4.0K Nov 27 08:21 xinit
drwxr-xr-x   2 root root 4.0K Jan 15  2014 xkb
-rwxr-xr-x   1 root root  709 Apr  1  2010 Xreset
drwxr-xr-x   2 root root 4.0K Feb 18  2015 Xreset.d
drwxr-xr-x   2 root root 4.0K Feb 18  2015 Xresources
-rwxr-xr-x   1 root root 3.7K Jan 29  2014 Xsession
drwxr-xr-x   2 root root 4.0K Nov 27 08:21 Xsession.d
-rw-r--r--   1 root root  265 Jul  1  2008 Xsession.options
drwxr-xr-x   2 root root 4.0K Apr 17  2014 xsm
-rw-r--r--   1 root root  601 Apr 17  2014 Xwrapper.config
root@hon-pc-01:/etc/X11# 

```

The 110M file, core, its needed file or some core dump ?

When i go to console (CTRL+ALT+F1), i get very low screen resolution. How i fix resolution of console windows ?

Thanks,

Boby

---

### Post by Bashing-om on 2016-02-23
bizhat; Hello;

A lot of questions here , let me see what I can do to address these questions:

the 1st question I have for you is what release are you running ? as It makes a difference as to the driver that is available in the software repository . For the 750ti GPU Nvidia recommends the 361 version driver:
[http://www.nvidia.com/download/driverResults.aspx/98373/en-us](http://www.nvidia.com/download/driverResults.aspx/98373/en-us)
so, to answer questions:
> 
I have no xorg.conf in /etc/X11 folder. It is not really needed ? 

correct, in that the file is depreciated and is generally no longer required. However if it is present it will be used. Recent kernels incorporate DKMS - Dynamic Kernel Module Support - where the kernel does all the heavy lifting in detecting and integrating the hardware.

> 
The 110M file, core, its needed file or some core dump ?

Do not know yet... what returns:
```

file /etc/X11/core

``` see what we can find out about that file.

> 
When i go to console (CTRL+ALT+F1), i get very low screen resolution. How i fix resolution of console windows ?


Maybe we can effect the terminal resolution from the ' /etc/default/grub '
 control file ?
in particular the line :
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```

Hope this helps
[INDENT][INDENT][INDENT]where do we go from here 
[/INDENT][/INDENT][/INDENT]

---

### Post by buzzingrobot on 2016-02-23
If you get things sorted out with the Nvidia driver, stay with it. The 750ti -- I have one -- isn't (able to be) supported well by Nouveau, for a number of reasons.

---

### Post by bizhat on 2016-02-23
Thanks all for the reply. I created xorg.conf file in nvidia-settings. 

"file /etc/X11/core" shows

```

root@hon-pc-01:~# file /etc/X11/core
/etc/X11/core: ELF 64-bit LSB  core file x86-64, version 1 (SYSV), too many program header sections (221)
root@hon-pc-01:~# 

```

> **Bashing-om said:**
> 
Maybe we can effect the terminal resolution from the ' /etc/default/grub '
 control file ?
in particular the line :
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```


Thanks, i modified the file, added (found at [https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks](https://wiki.archlinux.org/index.php/GRUB/Tips_and_tricks))

```

GRUB_GFXMODE=1024x768x32

```

I will do reboot and see how it goes.

> **buzzingrobot said:**
> If you get things sorted out with the Nvidia driver, stay with it. The 750ti -- I have one -- isn't (able to be) supported well by Nouveau, for a number of reasons.

Thanks, i will stay with current version of NVIDIA driver.

---

### Post by Bashing-om on 2016-02-23
bizhat; Hey,

You do good work.

If this natter is concluded to your satisfaction, then
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and we look
[INDENT][INDENT]for something 
[INDENT][INDENT][INDENT][INDENT]different to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bizhat on 2016-02-24
Thanks, i will mark it as solved.

---

