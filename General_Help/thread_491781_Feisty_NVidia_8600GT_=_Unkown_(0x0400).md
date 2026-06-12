---
title: "Feisty: NVidia 8600GT = Unkown (0x0400)"
date: 2007-07-04
forum: General Help
---

### Post by rscott5 on 2007-07-04
Hi everyone,

I just got a new Dell XPS 410 and am installing Ubuntu 7.04. I have a PCI-E nVidia 8600GT video card that came pre-installed in the machine. Unlike on my original Ubuntu machine where I just go to Restricted Drivers Manager and it installs them for me, when I do it on this new machine it says "Your hardware does not need any restricted drivers." even though it clearly does since I cannot run at full resolution. Also, when I go to Device Manager, the video card shows up as the following:
```
Vendor: nVidia Corporation
Device: Unknown (0x0400)
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabilities: Unknown
```

I just want the drivers installed so I can run at 1680x1050 on my new widescreen monitor :-) . What should I do to install the correct driver so that I don't have to try the millions of different methods that are listed all over the place? Thanks for your help.

---

### Post by rscott5 on 2007-07-04
Apparently the nvidia-glx-new driver in the Ubuntu Repo doesn't yet support the 8600GT so I had to download the newest driver (100.14.11) from the NVidia website. Then I followed the instructions here to install it:
[HTML]http://www.nvnews.net/vbulletin/showthread.php?t=94072[/HTML]

---

### Post by hikaricore on 2007-07-04
Aye I believe the GT series has just become supported, so it may be awhile before the restricted driver in Feisty is updated.  >.<

The 100 series driver has only been out of beta for a little over a week.

---

### Post by rscott5 on 2007-07-04
Ok so the steps I followed in the link above worked fine until I rebooted. Now it gives me a big error on the bootup saying:
```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```

When I say Yes, it brings me to a big long error page. The following is what I think is relevant:
```
Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to intialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Any ideas what to do here? Does anyone have a good tutorial that works for installing the newest drivers? Thanks.

---

### Post by jefffq on 2007-07-20
**BUMP**

I have the same card and the same error. I am also running Feisty. I do not know what to do.

I followed this guide:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I have this kernel:
2.6.20-16-generic

I did install the source, although the directions on the tutorial did not work exactly as specified. The command "sudo apt-get install linux-source-`uname -r`" did not find a package. I used synaptic and installed one, the difference in the string was lacking the "-16-generic". This affected the following to commands (from the guide) as well.

When I installed the driver it told me no precompiled kernel interface was found. This is the relevant output from the log file:
> -> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.

This is the only other error I could find:
> ERROR: Kernel configuration is invalid.
include/linux/autoconf.h or include/config/auto.conf are missing.
Run 'make oldconfig && make prepare' on kernel src to fix it.

The entire log file can be found [here]("http://jefff.ca/host/nvidia-installer.txt").

Any help would be much appreciated!

---

### Post by rscott5 on 2007-07-20
jefffq: I'm gonna be really honest with you, I started this post and for about 12 hours that day I thought I was simply out of luck, I did about a million things, followed every guide I could find, nothing worked. So I went to sleep. When I woke up 5 hours later, I turned on my machine and everything worked, I'm running at 1680x1050. I wish I knew what in the world I did to make it work. I am so afraid of making it not work again that I haven't played with the res or even breathed too hard near it. I wish I could help you. The one thing I would recommend trying if you haven't is get the driver directly from the nVidia website and install that, it may do the trick. I can't wait until Gutsy comes out and our card is included in the nVidia Restricted Drivers.

---

### Post by jefffq on 2007-07-20
Thanks for the sympathy! :)

I actually started my own post on it, just to exclude your original issue in case it threw anybody off.

[http://ubuntuforums.org/showthread.php?t=505569](http://ubuntuforums.org/showthread.php?t=505569)

There's been one reply, with a guide mentioning some explicit module stuff (in spanish, of course). Perhaps it will shed some light on what you did so you can breathe comfortably. I'm going to try it later.

---

### Post by fragos on 2007-07-20
> **rscott5 said:**
> jefffq: I'm gonna be really honest with you, I started this post and for about 12 hours that day I thought I was simply out of luck, I did about a million things, followed every guide I could find, nothing worked. So I went to sleep. When I woke up 5 hours later, I turned on my machine and everything worked, I'm running at 1680x1050. I wish I knew what in the world I did to make it work. I am so afraid of making it not work again that I haven't played with the res or even breathed too hard near it. I wish I could help you. The one thing I would recommend trying if you haven't is get the driver directly from the nVidia website and install that, it may do the trick. I can't wait until Gutsy comes out and our card is included in the nVidia Restricted Drivers.
When you compile a new driver that replaces an older one, a restart is probably required.

---

### Post by rscott5 on 2007-07-22
Ah yes, that must of been it.

---

### Post by Sockerdrickan on 2007-07-22
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

---

### Post by Linux_Punk on 2007-07-24
Tux0r will this work with the 2.6.20.16 kernel or would you recommend sticking with the 2.6.20.15 kernel?

---

### Post by xl_cheese on 2007-07-24
Install it with envy using the 15 kernel and let envy update your xorg.confg.

When you restart if the xserver is broken install the driver manually from the command line, but do not let it overwrite your xorg config.  

That combo worked for me two seperate instances.

---

### Post by Linux_Punk on 2007-07-24
ok after instalilng Ubuntu for the 'x'th time, i have the card (eVGA 8600 gt) fully configured. With kernel 2.6.20.15, Update manager is waiting for me to install linux-headers-generic and linux-image-generic both for 2.6.20.16. Should i go ahead and do this or just stick with 2.6.20.15? Sorry am new to linux :)

---

### Post by Linux_Punk on 2007-07-24
and what is envy xl_cheese?

---

### Post by Linux_Punk on 2007-07-24
ok heres what i did if anyone would like to answer my next upcoming question;
i had Synaptics 'lock' the two updates about 2.6.20.16 so Update manager would stop bugging me about it (Pet Peeve? I think so :p) If i went ahead and deleted the two configurations about 2.6.20.16 in my MENU.LST file would that affect my system at all pertaining to 2.6.20.15?? Meaning would i still be able to boot into .15 I just dont like .16 being in the GRUB menu because i just want to let the system to go into .15 (Winblows boots fine btw) Thanks!

---

### Post by fragos on 2007-07-24
You can have multiple kernels installed for the same version of Ubuntu.  You select the one you want to use in the GRUB menu at boot up.

---

### Post by Linux_Punk on 2007-07-24
but if i get rid of the 2.6.20.16 in menu.lst that only deletes it from the OS selection in Grub correct? i just want .15 kernel and winblows thats all when starting up grub. My video card doesnt do too well in .16 kernel

---

### Post by Linux_Punk on 2007-07-24
edited it with no problems, thanks!
SOLVED

---

### Post by xl_cheese on 2007-07-24
you can use the 16 kernel once the driver is working ok.

Envy is a peice of software that installs nvidia drivers.  Search for it and you'll find where to get it from.

---

### Post by Linux_Punk on 2007-07-25
thank you very much, will try!

---

