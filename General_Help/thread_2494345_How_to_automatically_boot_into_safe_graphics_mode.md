---
title: "How to automatically boot into safe graphics mode?"
date: 2024-01-13
forum: General Help
---

### Post by cbraxton on 2024-01-13
I'm resurrecting an ancient Acer laptop using Lubuntu, something I've done successfully with other old hardware in the past. However this laptop is equipped with an Nvidia GeForce 7000m video card which it seems is not supported either by the nouveau open-source driver or the proprietary Nvidia driver.

The Lubuntu 22.04 live image boot menu has a selection for safe graphics mode and that works fine, it will even play youtube videos in SD. However once Lubuntu is installed there is no such selection on the boot menu and the screen is distorted and unusable.

I've done some searching and not found anything yet that works. It must be possible since the option exists running the live image. What mystical incantations are needed to have the installed Lubuntu boot automatically into safe graphics mode?

---

### Post by MAFoElffen on 2024-01-13
You have two options.

First option: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 
 - Add this ppa and install nvidia-driver-304. That is the legacy driver that covers your GPU.

OR...

In the /etc/default/grub file, add "nomodeset" to the GRUB_CMDLINE_DEFAULT_LINUX line, right after the words "quitet splash", but withi the quotation marks... Save and exit. Then do
```

sudo update-grub

```
From then on it will be in Safe-mode, and use the opensource Nouveau driver.

---

### Post by cbraxton on 2024-01-13
Thanks for those suggestions! I added the "nomodeset" setting, ran update-grub, and rebooted. However after Plymouth is done displaying the startup/logo screen the system doesn't switch into graphics mode, it drops into text mode showing a few lines of logging the last of which is "[ OK ] Set console scheme".  Then it just sits there with no graphics and no prompt. (A positive change is previously there was no logo displayed while loading.) It is possible to get to the text consoles using the Alt-Fn keys.

Unfortunately it looks like the nvidia-driver-304 package is not available for jammy. The last Ubuntu LTS release that version is listed as available for is bionic which is years out of support now.

The safe mode video would be fine and it does work from the live image so I must still be missing something to get it working on the installed system.

---

### Post by guiverc on 2024-01-13
You mention Lubuntu 22.04, but not which ISO you actually installed with.

Lubuntu 22.04 being a LTS has kernel stack options; with the install media setting your default.  Post install & after updates you can thus end up booting into a newer kernel IF you used install media that defaults to a HWE kernel stack.

- Lubuntu 22.04 LTS & 22.04.1 media defaults to the GA kernel stack.
- Lubuntu 22.04.2 LTS & later media defaults to the HWE kernel stack.

Which did you use?

If interested you can learn more reading [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) where Lubuntu being a *flavor* of Ubuntu, still operate as Ubuntu 18.04 LTS media did (*ie. what I describe above*).

FYI:  I'd expect the `nomodeset` paramater to achieve what *safe graphics* did on your install media; however I wonder if you used a HWE kernel stack install media, and are thus booting into a different linux kernel to what existed on your install media; thus the different results.   I've also found using the older (GA) kernel stack is better for older hardware (especially graphics hardware).

---

### Post by cbraxton on 2024-01-13
I used the latest installer, Lubuntu 22.04.3, that may well be the problem.

---

### Post by BicyclerBoy on 2024-01-14
I believe that safe mode would be blacklisting the nouveau driver as it is the far less reliable than the builtin modeset or fbdev or vesa or efifb etc.

I have doubts about the modeset driver.
Vesa is said to be slow & does not work with EFI booting.
Your old 7000 is never going to EFI boot in any case. 

For many reasons I chose to use an older nvidia videocard & fbdev framebuffer driver.
This results LLVMpipe & swrast for openGL (CPU).
With a powerful CPU this works really well & it does not corrupt the screen & crash/lock up the PC (like nouveau).
And openGL & directX works in Wine32 bit (does not with nvidia drivers from ubuntu).

A curious observation is that nouveau is always reliable in the live USB sessions (debian 11 or 12 mate & unity 23.10) just never in the install.

---

### Post by guiverc on 2024-01-14
> **cbraxton said:**
> I used the latest installer, Lubuntu 22.04.3, that may well be the problem.


Lubuntu 23.04.3 used the 6.2 linux kernel originally from the more recent Ubuntu 23.04 release (*this is how HWE kernels update*) but on upgrades it'll get the current 6.5 kernel from 23.10 meaning if you installed upgrades during install OR anytime after that, you'll be booting into a newer kernel than the 22.04.3 media used.

At boot, I'd expect you to have an option to boot into the 6.2 kernel; is is there as a selection of options at grub (look in ***Advanced Options***).  This may get you a GUI using your installed system, though as 6.2 is no longer a patched kernel for security fixes, its not a long term solution if security matters to you.

To add the GA kernel stack on your install, you can follow what you'll find in [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) by searching for

> To downgrade from HWE/OEM to GA kernel:

A pure Lubuntu install will allow both GA + HWE kernels to be installed, however do note some closed-source proprietary drivers (eg. some Nvidia) can prevent this. You'll note the doc tells you to test it, before suggesting

> 
 "If everything is good, you may remove the other kernel flavours"


ie. removing the older kernel stack is optional, thus if you don't do it, you can select which you'll use at boot time (via grub selection).  You can also edit grub to make a specific stack the default too if wanted.

The change from 6.2 to 6.5 linux kernel is very recent; as we're approaching 22.04.4 with the kernel upgrade a large part of that upgrade; but your system will report itself as 22.04.3 UNTIL all upgrades are installed on your system (*some upgrades are still only available [last I checked] in proposed*). There is almost always a small percentage of hardware platforms where problems are encountered with such changes (as the kernel upgrade means newer kernel modules; kernel modules commonly being called '*drivers*').  If bug reports are filed by those users (*on the hardware where a regression occurs*) the developers can start to investigate and create fixes for the issues, which has the benefit that upgrades will occur that will fix the issue for many hardware platforms (*on which the bug reports were filed*). This means you may find in a week (or two), even in a few days an upgrade will come through and you'll find the 6.5 kernel will work, alas 5.15 or GA is often a easier solution (*especially for older hardware*). FYI:  Server ISOs default to GA as its seen as the most stable stack.

---

### Post by cbraxton on 2024-01-14
Thanks. As detailed in the wiki I installed the linux-generic kernel. This installed the 5.15.0-91-generic kernel. Then rebooted, selected the 5.15 kernel, and the GUI came up. So, then I removed the other kernels, rebooted but no more GUI, not even the Plymouth splash screen. A case of one step forward and two steps back. Will have to play around with it some more.

---

### Post by guiverc on 2024-01-14
> **cbraxton said:**
> Thanks. As detailed in the wiki I installed the linux-generic kernel. This installed the 5.15.0-91-generic kernel. Then rebooted, selected the 5.15 kernel, and the GUI came up. So, then I removed the other kernels, rebooted but no more GUI, not even the Plymouth splash screen. A case of one step forward and two steps back. Will have to play around with it some more.

For us to provide specific help, its helpful if you're specific as to what commands you actually used, plus what output you obtained. The wiki page I provided was last updated for Ubuntu 20.04 LTS because the defaults for Ubuntu Desktop changed (20.04 & later), but *flavors *(like Lubuntu) aren't really mentioned in that page (*still following the standard of 18.04 Desktop & earlier anyway*) & Server didn't change (*still using GA or the most stable option as default** for all media*).

Your alternative is to view the logs of what you did, eg. if I use the command 
```

view /var/log/apt/history.log

```

and search for the keyword 'remove' (I typed "/remove"; if you're familiar with POSIX, `vim` or most unix tools, its been the same >40 years), I can come up with 
```

Start-Date: 2024-01-05  16:39:25
Commandline: apt autoremove
Requested-By: guiverc (1000)
Remove: linux-headers-6.5.0-9:amd64 (6.5.0-9.9), linux-modules-6.5.0-9-generic:amd64 (6.5.0-9.9), linux-modules-extra-6.5.0-9-generic:amd64 (6.5.0-9.9), linux-headers-6.5.0-9-generic:amd64 (6.5.0-9.9), linux-image-6.5.0-9-generic:amd64 (6.5.0-9.9)
End-Date: 2024-01-05  16:39:36

```

which tells me date/time of a command I executed; and the list of packages (*old kernels*) that were removed. You could provide such detail for us to maybe help why, and give a precise *fix* that changes the least possible.

Alternatively; simple moves like `sudo apt install --reinstall lubuntu-desktop` may help, but I'd always explore WHY something happened, so you can see what was overlooked and why something happened, as unusual results are usually a symptom of something differing to what you expected (*unrecognized problems may exist which are easier to fix early*). I don't know what has happened, but I don't know what exact command(s) you've entered into your box (*recently, or anytime since install*).

---

### Post by cbraxton on 2024-01-14
I saw those instructions were for 20.04 and tried not to remove anything that was needed but obviously clobbered something that should have been left alone.

Here are the apt log entries for the installation of linux-generic and the removals. (At one point I installed synaptic to easily search for hwe components which shows that the GUI was working.)

```

Start-Date: 2024-01-14  11:03:16
Commandline: apt install --install-recommends linux-generic
Requested-By: owner (1000)
Install: linux-modules-extra-5.15.0-91-generic:amd64 (5.15.0-91.101, automatic), linux-headers-generic:amd64 (5.15.0.91.88, automatic), linux-image-5.15.0-91-generic:amd64 (5.15.0-91.101, automatic), linux-generic:amd64 (5.15.0.91.88), linux-image-generic:amd64 (5.15.0.91.88, automatic), linux-headers-5.15.0-91-generic:amd64 (5.15.0-91.101, automatic), linux-modules-5.15.0-91-generic:amd64 (5.15.0-91.101, automatic), linux-headers-5.15.0-91:amd64 (5.15.0-91.101, automatic)
End-Date: 2024-01-14  11:05:33

Start-Date: 2024-01-14  15:06:55
Commandline: /usr/bin/unattended-upgrade
Remove: linux-image-6.2.0-26-generic:amd64 (6.2.0-26.26~22.04.1)
End-Date: 2024-01-14  15:07:01

Start-Date: 2024-01-14  15:07:19
Commandline: /usr/bin/unattended-upgrade
Remove: linux-hwe-6.2-headers-6.2.0-26:amd64 (6.2.0-26.26~22.04.1), linux-headers-6.2.0-26-generic:amd64 (6.2.0-26.26~22.04.1)
End-Date: 2024-01-14  15:07:23

Start-Date: 2024-01-14  15:07:41
Commandline: /usr/bin/unattended-upgrade
Remove: linux-modules-extra-6.2.0-26-generic:amd64 (6.2.0-26.26~22.04.1), linux-modules-6.2.0-26-generic:amd64 (6.2.0-26.26~22.04.1)
End-Date: 2024-01-14  15:07:47

Start-Date: 2024-01-14  15:08:06
Commandline: /usr/bin/unattended-upgrade
Upgrade: locales:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.6)
Error: Sub-process /usr/bin/dpkg exited unexpectedly
End-Date: 2024-01-14  15:08:53

Start-Date: 2024-01-14  15:09:21
Commandline: apt install synaptic
Requested-By: owner (1000)
Install: libgtk3-perl:amd64 (0.038-1, automatic), synaptic:amd64 (0.90.2build1), libextutils-depends-perl:amd64 (0.8001-1, automatic), libvte-2.91-common:amd64 (0.68.0-1, automatic), libept1.6.0:amd64 (1.2.1, automatic), libcairo-gobject-perl:amd64 (1.005-3build1, automatic), libvte-2.91-0:amd64 (0.68.0-1, automatic), libglib-object-introspection-perl:amd64 (0.049-1+build2, automatic), libglib-perl:amd64 (3:1.329.3-2build1, automatic), libcairo-perl:amd64 (1.109-2build1, automatic)
End-Date: 2024-01-14  15:13:23

Start-Date: 2024-01-14  15:18:49
Commandline: synaptic
Requested-By: owner (1000)
Remove: linux-image-generic-hwe-22.04:amd64 (6.5.0.14.14~22.04.7), linux-headers-generic-hwe-22.04:amd64 (6.5.0.14.14~22.04.7), linux-generic-hwe-22.04:amd64 (6.5.0.14.14~22.04.7), linux-headers-6.5.0-14-generic:amd64 (6.5.0-14.14~22.04.1)
Purge: linux-hwe-6.5-headers-6.5.0-14:amd64 (6.5.0-14.14~22.04.1), linux-image-6.5.0-14-generic:amd64 (6.5.0-14.14~22.04.1)
End-Date: 2024-01-14  15:19:01

Start-Date: 2024-01-14  15:20:19
Commandline: synaptic
Requested-By: owner (1000)
Remove: linux-modules-extra-6.5.0-14-generic:amd64 (6.5.0-14.14~22.04.1)
Purge: linux-modules-6.5.0-14-generic:amd64 (6.5.0-14.14~22.04.1)
End-Date: 2024-01-14  15:20:26

Start-Date: 2024-01-14  15:23:00
Commandline: synaptic
Requested-By: owner (1000)
Install: linux-modules-6.2.0-39-generic:amd64 (6.2.0-39.40~22.04.1, automatic), linux-image-6.2.0-39-generic:amd64 (6.2.0-39.40~22.04.1)
End-Date: 2024-01-14  15:23:38

Start-Date: 2024-01-14  15:26:28
Commandline: apt install net-tools
Requested-By: owner (1000)
Install: net-tools:amd64 (1.60+git20181103.0eebece-1ubuntu5)
End-Date: 2024-01-14  15:26:29

Start-Date: 2024-01-14  15:35:36
Commandline: apt remove --purge linux-image-6.2.0-39-generic
Requested-By: owner (1000)
Purge: linux-image-6.2.0-39-generic:amd64 (6.2.0-39.40~22.04.1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2024-01-14  15:35:46

Start-Date: 2024-01-14  15:39:51
Commandline: apt-get remove --purge linux-image-6.2.0-39-generic
Requested-By: owner (1000)
Purge: linux-image-6.2.0-39-generic:amd64 (6.2.0-39.40~22.04.1)
End-Date: 2024-01-14  15:39:58

Start-Date: 2024-01-14  16:54:02
Commandline: apt autoremove
Requested-By: owner (1000)
Remove: linux-modules-6.2.0-39-generic:amd64 (6.2.0-39.40~22.04.1)
End-Date: 2024-01-14  16:54:03

Start-Date: 2024-01-14  16:57:55
Commandline: apt remove --purge systemd-hwe-hwdb
Requested-By: owner (1000)
Purge: systemd-hwe-hwdb:amd64 (249.11.3)
End-Date: 2024-01-14  16:58:00

```

---

### Post by cbraxton on 2024-01-22
To bring some closure to this, I was not able to figure out why my Ubuntu installation only booted to GUI one time then failed, though no doubt it was something I did. So I did some experimenting with other distributions. After trying several I found that Devuan Linux works well after adding "nomodeset" to the kernel command line. That should be fine for the way this thing will be used, just for general internet browsing.

---

