---
title: "Not correct resolution on terminal - Ubuntu Server 22.04 LTS"
date: 2023-01-05
forum: General Help
---

### Post by autominus on 2023-01-05
So I have an DELL monitor. The documentation for the monitor says that the optimum resolution using their supplied HDMI cable is 2560x1440@60Hz. When I boot into Windows, I  can get that resolution. But no matter what I try, I can't get that resolution in Ubuntu 22.04 LTS Server.

I am using DELL OptiPlex 7070 with i5-9500 and Intel graphics card (Intel UHD Graphics 630).

When I run Grub, I have correct resolution. Then by booting into Linux, I have not correct resolution (2048x1152) on terminal. In Linux, I only use text mode. 

How can I fix my problem.

---

### Post by TheFu on 2023-01-05
Ubuntu Server doesn't have any GUI, so besides installation, emergencies and "Frankenstein" setups, I don't understand.  99.9999% of the world would access their Unix server remotely using ssh.  The ssh text size is controlled by the terminal settings on the workstation you use.

For example, to ssh into another systems, set the font, size, location, I use:
```
$ XTERM_OPTS="-u8 -fs 12 -fa Monospace -sb -fg green -bg black"
$ xterm -geometry 80x22+0+630 $XTERM_OPTS -e ssh -X regulus &
```

regulus is the remote system. It is headless.  I use the same options, just change the location where the xterm is placed for each system. Over the decades, I've gotten muscle memory for which window is in which part of my screen ... because they are always in the exact same location. Always.
It is possible to place the terminals into different workspaces too. I use xdotool for that:
```
xdotool set_desktop_viewport 1980 0
```
then I move and resize specifically named windows to the desired location.
```
xdotool search --name "Mozilla Firefox" windowmove 170  0
xdotool search --name "Mozilla Firefox" windowsize 1600  815
```

As for setting a text console, I've not needed to do that in well over 20 yrs, but I'd guess that 'stty' would be the command.
```
stty cols 80
```

X/Windows is so much nicer.  xdotool doesn't work with Wayland, but I think someone tried to recreate most of the functionality using ydotool. Don't quote me on that name.  It has been about a year since I looked for a Wayland method.

Anyway, get ssh working and use any Unix-like OS as your terminal into the server.

---

### Post by ActionParsnip on 2023-01-05
Is the screen usable at the current resolution?

---

### Post by MAFoElffen on 2023-01-05
> **autominus said:**
> In Linux, I only use text mode. 
Yes. Ubuntu Server Edition is Text Mode. Sort of. 

You could certainly put into pure, native text mode, using Vesa modes 264 - 268, but... It is actually a pseudo vga framebuffer text type of mode in virtual console. Think more as "Console".

There are many things you can still do to customize Console. For example a quick easy way is
```

sudo dpkg-reconfigure console-setup

```
to change keyboard and console font. You can get into more detailed changes via '[setfont]("https://manpages.ubuntu.com/manpages/jammy/man8/setfont.8.html")' and [/etc/vconsole.conf]("https://manpages.ubuntu.com/manpages/jammy/en/man5/console-setup.5.html"). Then '[setterm]("https://manpages.ubuntu.com/manpages/jammy/man1/setterm.1.html")'. Look at the manpages.

Then there is using Byobu, or Tmux. Resetting the [VGA palette]("https://ubuntuforums.org/showthread.php?t=1743535&page=85&p=11548061#post11548061"). Changing the look and feel of the prompt. ETC.

Since VTTY is framebuffer, you could tweak and test how framebuffer is set up through the kernel boot KMS parameters. This is hit and miss, based on your hardware combination and how vtty is going to respect those changes. For example, I use
```

--- video=uvesafb:1920x1080-32@60,mttr:3,ywrap,noblank

```
Something like that may or may not work for you in /etc/default/grub.

Most people, including me, connect to their server via ssh from another  machine via a graphical terminal session. Which then create profiles  that you tweak the look and feel of.

I can remember having a VT-220 terminal with XWindows and thinking I was in heaven. We have evolved a lot since then.

---

### Post by Slimerang on 2023-04-26
Did anyone come up w/ a resolution to this issue?

I have two identical servers both running 23.04 as a few days ago that I toggle between w/ a KVM switch. When either of the systems comes up w/ the KVM switched over to that system, it detects the monitor and comes up w/ a nice text console resolution of 1920x1200. **No X Windows and GUI running on console, just text session across 6 virtual terminals**. In this situation:[INDENT][FONT=courier new]
# fbset -i
mode "1920x1200"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    geometry 1920 1200 1920 1200 32[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    timings 0 0 0 0 0 0 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    accel true[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    rgba 8/16,8/8,8/0,0/0[/FONT][/INDENT]
[INDENT][FONT=courier new]endmode[/FONT][/INDENT]
[INDENT][FONT=courier new]
[/FONT][/INDENT]
[INDENT][FONT=courier new]Frame buffer device information:[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Name        : mgag200drmfb[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Address     : 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Size        : 9216000[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Type        : PACKED PIXELS[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Visual      : TRUECOLOR[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    XPanStep    : 1[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    YPanStep    : 1[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    YWrapStep   : 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    LineLength  : 7680[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Accelerator : No[/FONT][/INDENT]


If the KVM is not switched to the server then the console comes up in 1024x768 resolution. The result here is:[INDENT][FONT=courier new]
# fbset -i
mode "1024x768"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    geometry 1024 768 1024 768 32[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    timings 0 0 0 0 0 0 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    accel true[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    rgba 8/16,8/8,8/0,0/0[/FONT][/INDENT]
[INDENT][FONT=courier new]endmode[/FONT][/INDENT]
[INDENT][FONT=courier new]
[/FONT][/INDENT]
[INDENT][FONT=courier new]Frame buffer device information:[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Name        : mgag200drmfb[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Address     : 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Size        : 3145728[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Type        : PACKED PIXELS[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Visual      : TRUECOLOR[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    XPanStep    : 1[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    YPanStep    : 1[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    YWrapStep   : 0[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    LineLength  : 4096[/FONT][/INDENT]
[INDENT=2][FONT=courier new]    Accelerator : No[/FONT][/INDENT]


If I reboot this same server while connected to this monitor via the KVM then it also comes up w/ the 1920x1200 resolution.

I have tried to force the resolution without luck:[INDENT][FONT=courier new]
# fbset -g 1920 1200 1920 1200 32[/FONT][/INDENT]
[INDENT][FONT=courier new]ioctl FBIOPUT_VSCREENINFO: Invalid argument[/FONT][/INDENT]
[INDENT]

[/INDENT]
Both systems report the frame buffer looking exactly the same even though it ends up having higher resolution than the modes show:[INDENT][FONT=courier new]
# hwinfo --framebuffer[/FONT][/INDENT]
[INDENT][FONT=courier new]02: None 00.0: 11001 VESA Framebuffer                           [/FONT][/INDENT]
[INDENT=2][FONT=courier new]  [Created at bios.459][/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Unique ID: rdCR.mCUP8WwEfLD[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Hardware Class: framebuffer[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Model: "Matrox MGA-G200"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Vendor: "Matrox"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Device: "MGA-G200"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  SubVendor: "Matrox Graphics Inc."[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  SubDevice: [/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Revision: "00"[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Memory Size: 16 MB[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Memory Range: 0x00000000-0x00ffffff (rw)[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0301: 640x480 (+640), 8 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0310: 640x480 (+1280), 15 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0311: 640x480 (+1280), 16 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0312: 640x480 (+2560), 24 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0300: 640x400 (+640), 8 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0303: 800x600 (+800), 8 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0313: 800x600 (+1600), 15 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0314: 800x600 (+1600), 16 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0315: 800x600 (+3200), 24 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0305: 1024x768 (+1024), 8 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0316: 1024x768 (+2048), 15 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0317: 1024x768 (+2048), 16 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0318: 1024x768 (+4096), 24 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0307: 1280x1024 (+1280), 8 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x0319: 1280x1024 (+2560), 15 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x031a: 1280x1024 (+2560), 16 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x031b: 1280x1024 (+5120), 24 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x031c: 1600x1200 (+3200), 15 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x031d: 1600x1200 (+3200), 16 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Mode 0x031e: 1600x1200 (+6400), 24 bits[/FONT][/INDENT]
[INDENT=2][FONT=courier new]  Config Status: cfg=new, avail=yes, need=no, active=unknown[/FONT][/INDENT]


I haven't tried the GRUB fixes b/c these servers will move and then I don't know what monitor will be connected and I'd have to change GRUB again. Not the end of the world but rebooting just get the monitor resolutions correct seems pretty lame.

I'm just looking for a command that would just make it auto analyze the monitor again and get to the max resolution available on whatever monitor I hook up to it on the fly.

---

### Post by MAFoElffen on 2023-04-26
> **Slimerang said:**
> I'm just looking for a command that would just make it auto analyze the monitor again and get to the max resolution available on whatever monitor I hook up to it on the fly.
Not "automated", but at boot, at the grub menu, if you get into the Grub CLI, do
```

videoinfo

```
That will return the EDID table resolutions of the connected display(s). On the same lines of xrandr, but X11 is not needed, and is before the kernel is even booted (directly from Grub2).

---

