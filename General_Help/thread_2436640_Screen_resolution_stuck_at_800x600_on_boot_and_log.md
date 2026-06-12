---
title: "Screen resolution stuck at 800x600 on boot and login screen."
date: 2020-02-10
forum: General Help
---

### Post by tasnimtamim on 2020-02-10
SOLVED. CHECK LAST POST
Hi,
I am running KDE Neon, which I suppose is the closest to Kubuntu so hopefully people here don't mind, and I also had same issue on Ubuntu 18.04.
Now, my PC has problems with almost every Linux OS I tried (Ubuntu, Manjaro, Puppy, Mint, etc.) where the screen resolution won't go above 800x600 when running in VGA. In order to get 1920x1080 resolution I have to use xrandr and then everything is OK. Now I got to make xrandr apply it's setting **when I login only**, not while booting nor in login screen which bugs me alot as I can't see/reach many things. It's quite annoying and I can't find any solution for this.

So my question is, how can I get my correct screen resolution before/during my OS boots so that I can see the login screen properly? Any helps would be appreciated, Thanks!

Spec:
Ryzen 3 2200G APU
Vega 8 iGPU
GIGABYTE A320M-S2h
KDE Neon 5.17 (Same issue for Ubuntu 18.04 too)

---

### Post by mastablasta on 2020-02-10
does it have same issues on 19.10? what about latest kernel? same issue? if yes, then it's not the drivers that are the issue.

Have you tried installing amdgpu-pro drivers? though i am not sure they would help with screen resolution.

problem is likely that VGA monitor is not passing the EDID or that EDID is not being read correctly.

---

### Post by tasnimtamim on 2020-02-10
Haven't tried 19.10. Kernel is 5.3.0-28-generic and that's what I think is latest (could be wrong).

Tried installing amdgpu-pro and now I'm having more problems than before. Resolution is not fixed nor auto detects unless I xrandr it. Now PC won't suspend properly, Ethernet keeps disconnecting while trying to connect, always has Power LED on, sudden graphics glitch and some theme is broken.

I avoided installing amdgpu-pro because it didn't had Vega 8 or any Ryzen iGPU on supported list. Other than said problems and main problem not fixing, it didn't caused other problems than having this message at the end of installation "warning: amdgpu dkms failed for running kernel"

---

### Post by CatKiller on 2020-02-10
You'll need to specify the information that would otherwise be provided by EDID. HorizSync and VertRefresh are generally sufficient for resolution calculations; you can normally get them from the monitor's manual or specifications page.

---

### Post by tasnimtamim on 2020-02-10
I am fairly newbie on Linux side, so I didn't got what you mean.

---

### Post by Autodave on 2020-02-10
How is the monitor connected to the PC: what cables / adapters are you using?

---

### Post by tasnimtamim on 2020-02-10
Through VGA cable of my motherboard. Linux detects it as DisplayPort-0.
The monitor is a 19" no name brand. Windows 10 auto detects the monitor as 1400x900_75hz. Though I can manually add and get 1920x1080_73hz both on Linux and Windows.

---

### Post by CatKiller on 2020-02-10
> **tasnimtamim said:**
> I am fairly newbie on Linux side, so I didn't got what you mean.

There are lots of posts already describing how to put that information in xorg.conf. You can search for them.

---

### Post by tasnimtamim on 2020-02-10
Finally got it working!! Thanks to CatKiler's suggestion.

What I did:
1. Created /etc/X11/xorg.conf.d/ directory
2. Made a 10-monitor.conf file with these info:
> 
Section "Monitor"
    Identifier "DisplayPort-0"
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Option "PreferredMode" "1920x1080_60.00"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "DisplayPort-0"
    DefaultDepth 24
    SubSection "Display"
        Modes "1920x1080_60.00"
    EndSubSection
EndSection

Section "Device"
    Identifier "Device0"
    Driver "amdgpu"
EndSection

3. Reboot and done!

Except boot animation, I get 1920x1080 output now on Login Screen! Don't care about boot part. Anyway thanks a lot to everyone on this thread :D

---

### Post by Autodave on 2020-02-10
You may want to try another VGA cable.  The monitor's information is sent to the PC through one wire.  If that wire is broken or a pain connection weak, the PC cannot determine the monitor's abilities.  Also, some very cheap VGA cables don't even have that wire in them.

---

### Post by mastablasta on 2020-02-11
in any case this doesn't look like the OS issue, but a hardware issue.

---

