---
title: "After hours, ubuntu is STILL slow"
date: 2007-11-05
forum: General Help
---

### Post by professorTHC on 2007-11-05
Hello there!
Im new to the whole linux community, a recent transfer-ee from windows...ich.
make no mistake, i have no regrets, but ubuntu is a bit slow..
is it wrong to expect ubuntu to fly if i have 1.5g of PC2100 ram, 512mb Nvidia 7600 GS, an OK 2.0intel processor  etc?
i have the newest graphics, i enabled it through the restricted drivers thing.
after the manager said that the resricted accelerated graphics driver was enabled i figured it would act like a 7600GS but, ubuntu is pretty damn slow....dragging windows usually leaves a trail, scrolling is jumpy, you get the point. also, Counter-strike 1.6 was very laggy, regardless of the games video settings. 
how can i fix this problem?

---

### Post by njparton on 2007-11-05
Did you go for Gutsy (7.10)? Did you choose the 32 (i386) or 64 bit (AMD64) edition?

Do you have an intel celeron processor? Even so, you should be OK.

I get very sluggish performance if I use a compact flash card as a boot disk so I'm thinking of switching to xubuntu instead...

---

### Post by professorTHC on 2007-11-05
i got gutsy, 7.10 i386.
and it was a clean install on a desktop. new partition. 
it should be FAST shouldnt it?

---

### Post by mali2297 on 2007-11-05
Do you use desktop effects (Compiz Fusion)? If so, it might help to disable them.

EDIT:
1.5 GB of RAM?  Then it shouldn't be a problem. :-k

---

### Post by njparton on 2007-11-05
It shouldn't be too bad on that system.  1.5GB of  ram is a bit of a wierd combination have you got 3x512 sticks in there?

If so try removing a stick and see if that makes a difference. It's a long shot but I know that some games have performance issues with recent graphics cards with wierd amounts of ram: some games perform better with a 512MB graphics card than a 640MB graphics card. I'm just wondering if you have a similar issue with your system ram?

How big is your swap partition? Try and make sure it's at least 2048MB.

Have you enabled DMA transfers in your BIOS (if it supports this)?

It may also be worth trying Xubuntu.

My ubuntu 7.10 AMD64 system runs quicker than my Q6600, 4GB RAM Vista x64 computer even though I log onto the former via my LAN!

---

### Post by bingoUV on 2007-11-05
Can you answer the following questions :

1. Graphics performance issues. For preliminary check, post the output of the following 
```

glxinfo

```

2. Is tracker running? Verify by 
```

ps -aef | grep tracker

```

3. Could be some process taking large amount of memory. Post the output of the following command :
```

cat /proc/meminfo

```

---

### Post by professorTHC on 2007-11-05
I have 1GB stick and a 512mb stick, i created a new partition, my hardrive is only 40gigs, but it should be enough..
[B]
glxinfo just spat out: [/B]

"eran@eran-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:
" 
along with a bunch of random letters nad numbers
[B]
then the tracker said this:
[/B]
"eran@eran-desktop:~$ ps -aef | grep tracker
eran      5193  5017  0 03:21 ?        00:00:00 trackerd
eran      6325  6306  0 12:35 pts/0    00:00:00 grep tracker
eran@eran-desktop:~$ 
"
**the memory command said this:**

 "eran@eran-desktop:~$ cat /proc/meminfo
MemTotal:      1555048 kB
MemFree:        418132 kB
Buffers:         62880 kB
Cached:         698716 kB
SwapCached:          0 kB
Active:         733972 kB
Inactive:       355968 kB
HighTotal:      654528 kB
HighFree:         1120 kB
LowTotal:       900520 kB
LowFree:        417012 kB
SwapTotal:     1646620 kB
SwapFree:      1646620 kB
Dirty:              64 kB
Writeback:           0 kB
AnonPages:      328396 kB
Mapped:          80128 kB
Slab:            23864 kB
SReclaimable:    13980 kB
SUnreclaim:       9884 kB
PageTables:       2232 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2424144 kB
Committed_AS:   736600 kB
VmallocTotal:   114680 kB
VmallocUsed:     44356 kB
VmallocChunk:    66036 kB
"

---

### Post by dcstar on 2007-11-05
> **professorTHC said:**
> i got gutsy, 7.10 i386.
and it was a clean install on a desktop. new partition. 
it should be FAST shouldnt it?

Do not use the i386 kernel, install the "-rt" (real time) version you will find in Synaptic.

386 kernels are made for CPUs that are 20 years old and are installed by default to ensure a basic functional system, use a kernel better optimised for later CPUs.

---

### Post by professorTHC on 2007-11-05
what search should i do? 
i dont know if everything i have is i386 or some of them..
does that mean i should use the x64 download even though i dont have AMD?
should i reinstall ubuntu?

---

### Post by bingoUV on 2007-11-06
> **professorTHC said:**
> what search should i do? 
i dont know if everything i have is i386 or some of them..
does that mean i should use the x64 download even though i dont have AMD?
should i reinstall ubuntu?

There does not a-priori seem a problem with lack of RAM or bad graphics driver. But try stopping tracker, and see if that helps. 
```

killall -9 trackerd

```

Now after about 5 minutes, you might see some speeding up.

I don't think kernel will make much of a difference. i386 is reasonably fast and small performance gain by AMD 64 is not worth the hassle for everyone.

---

### Post by njparton on 2007-11-06
I've just switched to i386 from AMD64 and it's fixed my suspend issues and performs just fine.

---

### Post by professorTHC on 2007-11-06
It said no tracker killed, its possible i killed it myself earlier through use of this forum.
but for some reason maximized windows continue to be grayed out kind of, but when you scroll over the X and "-" buttons itll go back to normal. 
Thank you so much for your help btw!
the linux community is awesome.

---

### Post by mdurham on 2007-11-06
Can I suggest using the system monitor and seeing which process is hogging things. Sometimes Nautilus goes bananas on my system dragging things down, and I have to kill it.

---

### Post by professorTHC on 2007-11-07
XGL and Gnome System monitor and Banshee are usually the only ones with a percentage value OTHER than 0. and XGL only seems to jump to 30-40 every so often.
I dont understand what the problem is, its like, when i scroll, its not smooth, its jagged. if you can understand what i mean =X
Thanks so much for your help!

---

### Post by mdurham on 2007-11-07
professorTHC, did you enable 'view all processes' in the System Monitor? If there is nothing hogging the cpu I guess the problem must be within the video driver. I have a very old video card and a Celeron 2.4  cpu and don't have any lag at all.

---

