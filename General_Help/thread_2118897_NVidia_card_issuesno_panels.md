---
title: "NVidia card issues/no panels"
date: 2013-02-22
forum: General Help
---

### Post by andy_blah on 2013-02-22
I've been trying to make Ubuntu 12.10 to work on my older system (Intel Celeron D 2.26GHz single-core, 1.25GB RAM, NVidia 5500FX on AGP x4) but I'm having trouble with the graphical interface after I have installed the proprietary drivers. I'll try to explain the steps I took:

After installation I tries installing the NVidia Drivers from their site (173.1436 x86) and that gave me mixed results. It installed fine but after I started lighdm I would either be able to see graphical output but without the panels in Unity. I gave it a restart just in case some updates made by the driver weren't sifted through, but this time I got a "running in low graphics resolution mode" and I tried to troubleshoot it, asked me to restart afterwards so I did. This time it restarted with the same thing but without any mouse input, so I could only control by keyboard.

So at this point I decided that maybe Unity/lightdm doesn't work properly with this driver so I tried installing gnome-desktop and gdm (was going to do this afterwards anyway since I prefer it), and removed lightdm, started gdm, but I had the same problem as with Unity: no panels.
After I tried again to restart with the hope that it would fix the problem but this time uncannily stops at the Ubuntu textual splash screen without progressing further. I'm at loss on what to do.
Any suggestions?
Thanks in advance.

---

### Post by andy_blah on 2013-02-23
*bump*

---

### Post by bogan on 2013-02-23
Hi!, **andy_blah**,

Have you run nvidia-settings [ from a terminal ] or NVIDIA X Server Settings [ from Dash ] ??

If so, does it say: ' You seem not to be running an Nvidia ......' ?

Are you sure the 'linux-headers-generic', or  'linux-headers-'uname -r' are installed ?

If they are not, install them, remove the present nvidia driver and re-install it.```

uname -r # put output in place of 'uname -r',  in next command 
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install linux-headers-generic
sudo apt-get remove --purge nvidia-173
sudo apt-get install nvidia-173
```Or install nvidia from the .run file you downloaded.

Alternatively, install 'gnome-session-fallback' and log-in to 'gnome classic' or 'gnome classic ( no effects ' [ it' s available from Ubuntu Software Center].

Chao!, **bogan**.

---

### Post by andy_blah on 2013-02-23
Thanks for the reply, bogan.

> **bogan said:**
> Hi!, **andy_blah**,

Have you run nvidia-settings [ from a terminal ] or NVIDIA X Server Settings [ from Dash ] ??

nvidia-settings reports: "ERROR: The control display is undefined" on both nvidia-current and nvidia-173. 
If by "Dash" you mean Dashboard, I cannot access it, as I can't use any graphical part of Ubuntu/Gnome.

With the nvidia-current driver all I get is this:

[IMG]http://i.imgur.com/cUBwJHh.png[/IMG]

After that "Checking Battery Status" message shows up the entire screen flashes 4-5 times and then nothing. I tried pressing ESC to see the verbose but nothing shows up.

With nvidia-173 I get the graphical log-in screen but it's super slow (especially when there's animations) and there are some graphical glitches, like static noise where shadows should display.

> **bogan said:**
> Are you sure the 'linux-headers-generic', or  'linux-headers-'uname -r' are installed ?

linux-headers-generic was installed but linux-headers-<kern#> wasn't. Ofcourse I installed it but made no difference...

> **bogan said:**
> Alternatively, install 'gnome-session-fallback' and log-in to 'gnome classic' or 'gnome classic ( no effects ' [ it' s available from Ubuntu Software Center].

As I stated before, I can't get anything graphical to show up =(

---

### Post by bogan on 2013-02-24
Hi!, andy_blah,

The 173.14 driver is the correct one for a GeForce 5500FX_AGP card,and it works OK with 12.04.1, but I am not certain that it will run properly with 12.04.2 or 12.10.

I am a bit confused as to how you are getting into a terminal, is it via Recovery?  - do you get  Grub menu ? - or with 'text' as a boot command?

Does it run and boot to graphics from a LiveCD/USB ? 12.04 or 12.10 ??

Which  version of nvida-current are you trying? ```
apt-cache policy nvidia-current # or 
apt-cache policy nvidia-current*
```The error message: " "ERROR: The control display is undefined" is not one I have seen before.
 Do you have a /etc/X11/xorg.conf file, if so please post it.

Chao, **bogan.**

---

### Post by andy_blah on 2013-02-24
> **bogan said:**
> I am a bit confused as to how you are getting into a terminal, is it via Recovery?  - do you get  Grub menu ? - or with 'text' as a boot command?

I'm using the TTYs, seems much hassle free than to start with different boot parameters, right? =)

> **bogan said:**
> Does it run and boot to graphics from a LiveCD/USB ? 12.04 or 12.10 ??

I didn't try 12.04 yet but 12.10 works. Albeit the graphics are very slow (animation again) and I get it to work properly only if I add nomodeset to the boot parameters. I tried installing the nvidia driver (current) and it worked, but again, no panels.

> **bogan said:**
> Which  version of nvida-current are you trying? ```
apt-cache policy nvidia-current # or 
apt-cache policy nvidia-current*
```The error message: " "ERROR: The control display is undefined" is not one I have seen before.
 Do you have a /etc/X11/xorg.conf file, if so please post it.

nvidia-current here was this version: 304.51.really.304.43-0ubuntu1
The first time I installed it, it worked properly, except the panels (as in the live session).
Surprisingly there was no xorg.conf file with both drivers, but there were two back-up versions of it, one was titled xorg.conf.backup.#...# and the other was just xorg.conf.failsafe . I chose the latter and it booted properly and it worked, but when I ran nvidia-config it reported that I'm not using the driver, so supposedly the failsafe xorg.conf was the vanilla one. It promted me to run nvidia-xconf which I did, I restarted again and I got the corrupted graphics problem again... 

Seems that there's no end to this, anything else you'd suggest?

---

### Post by bogan on 2013-02-24
Hi!, **andy_blah**,

Exactly which driver is in use at present?

304.xx does not support 5xxxFX series cards and the 304.51- actually 304.43 has - in my experience - given problems with kernal module conflicts.

Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```My advice would be, First, to install 12.04.LTS; 
or,
 Second, to delete nvidia-current-304 by name, check it with apt-cache or Synaptic, use: ```
sudo apt-get remove --purge nvidia-current-304
sudo apt-get remove --purge nvidia* # and install 173 with:
sudo apt-get install nvidia-173 # or:
```Alternatively, the  latter may be available in Additional drivers or Synaptic; or you can use the nvidia.com downloaded .run file.

Chao!, **bogan**.

---

### Post by andy_blah on 2013-02-24
> **bogan said:**
> Exactly which driver is in use at present?

Before your post it was nvidia-173

> **bogan said:**
> Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```

uname -r:    3.5.0-17-generic

lspci -nnk | grep -iA3 vga:
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
            Kernel driver in use: nvidia
            Kernel modules: nvidia_173, nvidia, nouveau, nvidiafb
```

What I find weird about this is how it says the card is rev a1 when both the BIOS screen and the PCB of the video card report rev a2. Also I tried changing the driver in xorg.conf to the other modules listed above (besides nouveau) but all produce graphical glitches and it's very slow.

/usr/lib/nux/unity_support_test -p: This one requires the graphics to work, so far I can only use the TTYs because with nvidia-173 the animations are very slow and objects are drawn very very slowly so it's practically unsuable.

> **bogan said:**
> My advice would be, First, to install 12.04.LTS;

I'd like to try doing that when I have no other alternatives. Also do you think the issue will be fixed in future Ubuntu releases/updates? If not then I'd rather drop Ubuntu completely and move to another distro...

> **bogan said:**
> Second, to delete nvidia-current-304 by name, check it with apt-cache or Synaptic, use: ```
sudo apt-get remove --purge nvidia-current-304
sudo apt-get remove --purge nvidia* # and install 173 with:
sudo apt-get install nvidia-173 # or:
```Alternatively, the  latter may be available in Additional drivers or Synaptic; or you can use the nvidia.com downloaded .run file.

Did all that but ended up the same...
I also tried to sh the installer from nvidia but, again, same results. The first time when I installed this driver everything went well, except for the panels. When I restarted it reported that low graphics mode error.

---

### Post by bogan on 2013-02-24
Hi!, **andy_blah,**

In place of the unity-Support_test, try: ```
glxinfo | grep -i openGL
```I know many people have problems with 5xxxFX cards with newer kernals, but not as far as I know, as bad as you are reporting. It is, after all, in Graphics terms, a very outdated range.

If you can get to a GUI log-in, have you tried logging in to 'gnome classic' or 'gnome classic (no effects)'??

You may need to install gnome-session-fallback.

Alternatively, how does it run without the nvidia drivers, and using the default nouveau driver?
You will need to ensure it is not blacklisted in /etc/modprobe.d/ or the blacklist.conf file in that folder.

Chao!, **bogan**.

---

### Post by andy_blah on 2013-02-24
I have tried updating the packages and installed the driver from the .run file and now seemingly it works. I wanted to try updating in the hope that there might be an kernel update that might fix my issue. There weren't any kernel updates but the problem is still fixed!

> **bogan said:**
> In place of the unity-Support_test, try: ```
glxinfo | grep -i openGL
```

That command reports "Error: glXCreateContext failed"

But regardless, thanks bogan for your assistance.

---

