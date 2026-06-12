---
title: "Flickering Graphics"
date: 2018-02-04
forum: General Help
---

### Post by jjkrause on 2018-02-04
Was this issue ever resolved? I have the same problem with the same laptop (HP Compaq nx9420) with flickering screen... First time running lubuntu trying to revive this laptop as Windows is too slow, but its unusable with this flickering... Help!

Edit:  I tried changing the resolution to 800x600 and the flickering stopped, but now all I see is the background image and no icons or buttons.  It's strange though, its as if there are things in the background that I cannot see because my mouse cursor changes when I move it around on the screen (changes to window resize cursor and other cursors).

---

### Post by cruzer001 on 2018-02-04
@jjkrause

Please post your system specifications.  Open a terminal (Ctrl + Alt + t) and enter:

```
inxi -bG
```

Also better to start your own thread.  This one is old and using 17.04, a version thats reached end of life and no longer supported.

---

### Post by jjkrause on 2018-02-04
Thanks for your post Cruzer001.  I just tried Lubuntu 16.04.3 LTS and the video is fine, so its an issue with version 17.10.1 and the Radeon x1600 graphics card.  I'll stick with version 16.04.3 for now. 

Thanks!
Jason

---

### Post by cruzer001 on 2018-02-04
Thats a good choice.  16.04 has long term support (two years) and you can upgrade to the next LTS in April. 17.10 is short term release and only supported for 9 months.

You can mark this thread solved...if it was your thread to mark :p

---

### Post by jjkrause on 2018-02-04
Not my thread... I just hijacked it.  :)

---

### Post by QIII on 2018-02-04
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2366368").

Hijacking another user's thread is counter to generally accepted forum netiquette.  Don't do it, please.

---

### Post by jjkrause on 2018-02-05
Sorry QIII, lesson learned, I thought it was ok since the original thread wasn't closed.  My initial problem with my flickering screen has returned after a few updates.  The laptop is a HP Compaq nx9420 and I'm attaching all relevant info below:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
```

```
uname -a
Linux LubuntuPC 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:25 UTC 2018 i686 i686 i686 GNU/Linux
```

```
env | grep DESK
DESKTOP_SESSION=Lubuntu
XDG_SESSION_DESKTOP=Lubuntu
XDG_CURRENT_DESKTOP=LXDE
```

```
inxi -bG
System:    Host: LubuntuPC Kernel: 4.13.0-32-generic i686 (32 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP Compaq nx9420 (RB549UT#ABA) v: F.1C
           Mobo: Hewlett-Packard model: 309F v: KBC Version 54.3C
           Bios: Hewlett-Packard v: 68YAF Ver. F.1C date: 03/05/2008
CPU:       Dual core Intel Core2 T7200 (-MCP-) speed/max: 1333/2000 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV530/M56-P [Mobility Radeon X1600]
           Display Server: X.Org 1.19.5 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@60.11hz
           GLX Renderer: ATI RV530 GLX Version: 2.1 Mesa 17.2.4
Network:   Card-1: Broadcom NetXtreme BCM5753M Gigabit Ethernet PCI Express
           driver: tg3
           Card-2: Intel PRO/Wireless 3945ABG [Golan] Network Connection
           driver: iwl3945
Drives:    HDD Total Size: 107.8GB (11.5% used)
Info:      Processes: 148 Uptime: 1:03 Memory: 2425.1/3026.7MB
           Client: Shell (bash) inxi: 2.2.35 
```

I loaded this laptop with Lubuntu so my daughter could work on her projects but its unusable right now because of the flickering.

Thanks for any assistance.
Jason

---

### Post by cruzer001 on 2018-02-05
> my flickering screen has returned after a few updates

You are currently on the latest kernel (4.13.0-32-generic).  Revert back to the previous kernel at boot (grub screen)>advance options.  See if that clears it up.

---

### Post by jjkrause on 2018-02-05
Ok, I did as you recommended and reverted back to kernel 4.10.0.28-Generic and video is fine.  So is there a way to force it to this older kernel without pulling up the GRUB menu?  Will future updates force new kernels as default? Sorry, I'm totally new to Lubuntu.

```
inxi -bG
System:    Host: LubuntuPC Kernel: 4.10.0-28-generic i686 (32 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP Compaq nx9420 (RB549UT#ABA) v: F.1C
           Mobo: Hewlett-Packard model: 309F v: KBC Version 54.3C
           Bios: Hewlett-Packard v: 68YAF Ver. F.1C date: 03/05/2008
CPU:       Dual core Intel Core2 T7200 (-MCP-) speed/max: 1333/2000 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV530/M56-P [Mobility Radeon X1600]
           Display Server: X.Org 1.19.5 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@60.11hz
           GLX Renderer: ATI RV530 GLX Version: 2.1 Mesa 17.2.4
Network:   Card-1: Broadcom NetXtreme BCM5753M Gigabit Ethernet PCI Express
           driver: tg3
           Card-2: Intel PRO/Wireless 3945ABG [Golan] Network Connection
           driver: iwl3945
Drives:    HDD Total Size: 100.0GB (12.4% used)
Info:      Processes: 158 Uptime: 2 min Memory: 412.8/3026.5MB
           Client: Shell (bash) inxi: 2.2.35
```

Thanks for your help!
Jason

---

### Post by jjkrause on 2018-02-05
Strange, now back on kernel 4.13.0-32-generic and the video is still working fine so I'm not sure what is going on...

---

### Post by cruzer001 on 2018-02-05
> **jjkrause said:**
> Strange, now back on kernel 4.13.0-32-generic and the video is still working fine so I'm not sure what is going on...

Run like this for a while, see if it sticks.

---

### Post by jjkrause on 2018-02-06
And now flickering on both kernels.  Are there any other video drivers I can use for the Radeon x1600?  I'm about to give up on Lubuntu.  :(

---

### Post by cruzer001 on 2018-02-06
> **jjkrause said:**
> Are there any other video drivers I can use for the Radeon x1600?

Hello

From what I have read, your chipset (rv530) is supported by the generic driver. 

[https://help.ubuntu.com/community/RadeonDriver#Fully_supported](https://help.ubuntu.com/community/RadeonDriver#Fully_supported)

AMD has stopped driver support for your card and you are now limited to the open source driver.

[https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-and-newer-on-amd-graphics](https://askubuntu.com/questions/815591/ubuntu-14-04-5-16-04-and-newer-on-amd-graphics)

There are some optional settings you can look at in terminal.

```
man radeon
```

Thats all I can tell you about Radeon.  I do not run them and my knowledge is limited to what I read.

---

### Post by deadflowr on 2018-02-06
What resolutions can you try outside of 1680x1050 and 800x600 which are 16:10 and 4:3, respectively.
Can you set the standard 1024x768?
And if so, does that flicker?

Edit:
Here: [https://askubuntu.com/questions/794865/16-04-ati-mobility-radeon-x1600-full-resolution-flickering]("https://askubuntu.com/questions/794865/16-04-ati-mobility-radeon-x1600-full-resolution-flickering")

---

### Post by mörgæs on 2018-02-06
If you open the [old hardware]("https://ubuntuforums.org/showthread.php?t=2130640") link and search the text for *flicker* there is an easy test to do.

---

### Post by jjkrause on 2018-02-06
Interesting, the flickering stopped immediately when I changed the resolution to 1024x768.  Not the ideal solution, but at least the laptop is usable.  Thanks!

---

### Post by mörgæs on 2018-02-07
Now you can mark the thread solved.

---

