---
title: "Garbled Login Screen"
date: 2020-12-31
forum: General Help
---

### Post by robert99999 on 2020-12-31
Yesterday, I installed 20.04.1 LTS, onto an older PC laptop, from a bootable USB stick. The installation went well except for one detail. When I boot from the computer's hard drive, the login screen is garbled. The splash screen that appears on power up, and the desktop screen are both fine, but the login screen that appears between the two is garbled. It appears as a diagonal smear of white pixels on a purple background. (It's not a problem when booting from the USB stick, because it skips the login screen.) Knowing that I'm on the login screen, I'm still able to login blindly by hitting Enter a couple of times, then typing my password, and hitting Enter again.

 Obviously, GRUB is setting the resolution to something that's incompatible with the video hardware (ATS Radeon X1600 video processor).

I've pored over posts on this and other forums to find a cure, but nothing has worked. The suggested fix has been to edit the /etc/default/grub file and uncomment the commented out line: #GRUB_GFXMODE=640x480 with a compatible resolution. The first one I tried was 640x480, because I assumed that 640x480 would work on any hardware. After editing and saving the file I did the required sudo update-grub. But nothing changed. The login display was exactly the same. I tried many different resolution settings, with no effect. I've also seen suggestions to add the line GRUB_GFXPAYLOAD_LINUX= with various arguments. I also tried this with no effect.

I began to wonder if GRUB was even reading the configuration file, so I uncommented the system beep line at the end of the file. On the next boot, I did get the startup beep, so the file is being saved correctly, and GRUB is being updated, but still no change to the garbled login screen.

I would really appreciate it if someone could point me to a solution. I don't really care what resolution the login screen is, as long as it's readable.
BTW, my Linux experience is virtually nil, so it may take a lot of explaining.

Edited (2021-01-01) to add the following video hardware info:

[B]           *-display
                description: VGA compatible controller
                product: RV530/M56-P [Mobility Radeon X1600]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:29 memory:e0000000-efffffff ioport:4000(size=256) memory:f4600000-f460ffff memory:c0000-dffff
[/B]
The computer is a 2007 model HP-Compaq nc8430 notebook computer. Centrino Core Duo (64 bit) processor.

---

### Post by robert99999 on 2021-01-08
I'm getting closer to the solution to the problem. On another website I discovered that grub is switching from the bios video driver (which works) to one of the Linux drivers (which doesn't work, or isn't properly configured) before it loads the login screen.

Editing the /etc/default/grub file and adding the "nomodeset" option to this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
so that it's now:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
fixes the garbled login screen. The login screen is now readable, but this creates another problem. When the desktop starts up, the resolution remains the same as the login screen which doesn't have quite the correct aspect ratio. It's slightly stretched horizontally. When I go into Setup, it says "Unknown Display", and the only resolution option is 1400x1050. The normal resolution should be 1680x1050, but there's no way to change it. Before I added the nomodeset option to the grub config file, the display was recognized as "Built-In display", and quite a few resolution options were available.

So, now I need to figure out how to get Ubuntu to load the video drivers, but not until after the login is finished.

Any help would be much appreciated.

---

### Post by QIII on 2021-01-09
Would you please post the results of 

```
lsmod | grep radeon
```

to see if the "driver" kernel module is loaded.  If you can see anything at all, then it is.

---

### Post by robert99999 on 2021-01-09
This is what I get:
```
radeon               1466368  4
i2c_algo_bit           16384  1 radeon
ttm                   102400  1 radeon
drm_kms_helper        217088  1 radeon
drm                   552960  7 drm_kms_helper,radeon,ttm
```

---

### Post by QIII on 2021-01-09
OK.  That means that the module is loaded.  In other words, your driver is working.

During installation, the kernel detects whether an AMD GPU is present.  Then, depending on whether is it supported by radeon or amdgpu, the correct module is loaded.  There is nothing further to do.

The problem here is that your GPU is so old that it is still ATI branded.  That's pretty old.  AMD started to eliminate the ATI branding soon after it bought ATI, which was completed in 2008.  They kicked most ATI hardware to the curb pretty quickly.  Not that it mattered much.  ATI never cared about Linux anyway.

You are going to have to manually change some config files to allow the resolution you want.  It's been a while since I made any posts indicating how to do that, so I might have to dig.  

Unfortunately, I have a life outside of the forums and life seems to be happening pretty much in my face right now, so I may not be able to get back to this right away.

---

### Post by robert99999 on 2021-01-09
Sorry, I was in the process of editing my last post when you replied. Because of the reply, I cancelled the edit, and will elaborate here.
I had meant to say that WITHOUT the **nomodeset** option, I got the results that I posted above. However, WITH the **nomodeset** option,  the "lsmod | grep radeon" command doesn't return anything.

---

### Post by robert99999 on 2021-01-09
After comparing operation with and without the nomodeset option, I see that I was inaccurate in my comments in my second post about the boot sequence of events. I had believed that if the nomodeset option is NOT used, then the bios video driver is still used throughout the boot process, and that the linux drivers take over immediately before the login screen. 

After observing the boot sequence several times, with and without nomodeset, I've found the following:
Without the nomodeset option, the linux drivers are loaded and used immediately during the boot sequence. On the other hand, if the nomodeset option is used, then the linux drivers are never loaded, even after the boot sequence is complete. This seems contrary to what has been stated in various online resources, which say that if the nomodeset option is used, then GRUB won't load the drivers, but then the kernal or X will load them when they start up. However, this is clearly not happening.

I've also concluded that the linux drivers do work with my hardware (mostly), because when they are in operation, the splash screen and the desktop are displayed correctly. The only exception is when the login screen is displayed. Now I have to ask: Is login actually part of the boot process? It seems to me that at the point where the login screen is displayed, then the kernal must already be up and running, but perhaps X has not started up yet. If that is the case, then maybe the GRUB configuration is not the source of the problem. Is another process doing the login, and is it responsible for the wrong video setting?

---

### Post by tea for one on 2021-01-10
In Ubuntu 20.04, the login screen is using **gdm3**
There are other display managers in the repositories such as [COLOR="#0000FF"]lightdm[/COLOR] and [COLOR="#0000FF"]sddm[/COLOR].
However, in my experience, changing the display manager could lead to other problems such as not being able to log in at all, therefore tread carefully.

Having logged in, you could activate [COLOR="#0000FF"]autologin[/COLOR] to avoid the troublesome screen completely.
Settings > Users > Automatic Login
Again, there a a few threads on this forum where autologin has created other difficulties.

Ubuntu 20.04 may be too heavy for your 2007 HP Compaq so possibly a lighter flavour such as Xubuntu or Lubuntu may be better and they do not use **gdm3**.

---

### Post by robert99999 on 2021-01-10
Thanks. I may just leave things as they are. The login screen is just a minor irritation more than anything else, but being new to linux, I was more curious than anything else about how things work.

I chose 20.04 because it had been recommended as the easiest installation (from a bootable USB stick), even though it's probably not the best version for this old computer. I must say however that it works surprisingly well, so I'll continue to use it for the time being. I've been streaming movies in full screen mode with no hiccups. I just make sure not to have more than 2 or 3 applications running at a time. Speed problems seem to be mostly due to slow disk access. Since RAM is cheap, I'll probably bump it up to the 4GB maximum. I'll get an SSD too, as they're not expensive. I'm not ruling out Lubuntu or Xubuntu. I'll try them at some point, once I get a bit more comfortable with things.

---

