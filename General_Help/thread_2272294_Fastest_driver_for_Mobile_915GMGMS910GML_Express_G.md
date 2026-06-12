---
title: "Fastest driver for Mobile 915GM/GMS/910GML Express Graphics Controller"
date: 2015-04-05
forum: General Help
---

### Post by Ralph L on 2015-04-05
I am having trouble playing 1080p 60 frame per second camera video on my old Dell Latitude D610.  The computer just is too slow.  It has an Intel Mobile 915GM/GMS/910GML Express Graphics Controller.  I am running ubuntu 12.04, but am working on converting to ubuntu 14.04.  I am looking for the fastest graphic driver for my GPU.  My current driver from "sudo lshw -C display" is "driver=i915".  Does anybody know if there is a faster driver that would make my video run faster.  I have found that SMplayer/Mplayer is the fastest video program (out of SMplayer, Totem, and VLC) so I am using that.  
Any help is appreciated.

---

### Post by Mike_Walsh on 2015-04-05
Hallo, Ralph L.

Don't quite follow you, there. You say you want a 'faster' driver? I'm no expert with these kind of things, but I would have thought that whatever driver is in use is going to run at the system speed of your CPU. I don't think that any one driver is written to perform 'quicker' than another.

Can you let us have your system specs, please? CPU, RAM (we know your graphics card), etc? We CAN Google the computer, but it would help to know exactly what your specs are, as most models have various configuration options...

I like the way it's described as 'thin & light' in the cNet review.....at 4.7 lbs??  Well, I suppose it IS, compared to my old Dell Inspiron 1100; that tips the scales at a very portly 7.3... :lol: IF yours has the 512 MB RAM spec, I rather think you're simply asking too much of it.....especially if you're running Ubuntu. My Inspiron has 1 GB, and it runs 'Puppy' Linux (MUCH lighter!).....I wouldn't even ATTEMPT to run any kind of video device on there. You yourself state that it's just 'too slow'...

Need the exact specs.


Regards,

Mike. ;)

---

### Post by sandyd on 2015-04-05
> **Ralph L said:**
> I am having trouble playing 1080p 60 frame per second camera video on my old Dell Latitude D610.  The computer just is too slow.  It has an Intel Mobile 915GM/GMS/910GML Express Graphics Controller.  I am running ubuntu 12.04, but am working on converting to ubuntu 14.04.  I am looking for the fastest graphic driver for my GPU.  My current driver from "sudo lshw -C display" is "driver=i915".  Does anybody know if there is a faster driver that would make my video run faster.  I have found that SMplayer/Mplayer is the fastest video program (out of SMplayer, Totem, and VLC) so I am using that.  
Any help is appreciated.

Your card seems to be supported by Intel(R) Graphics Installer

Current release requires ubuntu 14.10.
See [https://01.org/linuxgraphics/downloads/2015/intelr-graphics-installer-linux-1.0.8](https://01.org/linuxgraphics/downloads/2015/intelr-graphics-installer-linux-1.0.8)

**Disclaimer: [There are issue with the installer and 14.04]("https://01.org/linuxgraphics/node/471")**
The last installer version for 14.04 is available at [https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/)

---

### Post by mc4man on 2015-04-05
> **sandyd said:**
> Your card seems to be supported by Intel(R) Graphics Installer

Current release requires ubuntu 14.10.
See [https://01.org/linuxgraphics/downloads/2015/intelr-graphics-installer-linux-1.0.8](https://01.org/linuxgraphics/downloads/2015/intelr-graphics-installer-linux-1.0.8)

**Disclaimer: [There are issue with the installer and 14.04]("https://01.org/linuxgraphics/node/471")**
The last installer version for 14.04 is available at [https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/)

Just to clear up something - the 14.04 installer package can be installed but it will not do anything when run (all that package has is an installer app
The actual packages that it would have installed have been pulled.

---

### Post by Ralph L on 2015-04-06
Mike_Walsh:  From System Monitor>System the processor is: Intel® Pentium(R) M processor 2.13GHz; 2GB of memory.  
sandyd:  I am an old guy.  40 years ago I wrote drivers for mainframes.  In those days, at least, there were vast differences in how fast hardware ran with differently designed drivers.  I am just wondering if there might be a driver for my gpu that runs faster than the default one used in ubuntu 12.04.  I don't know if the 14.04 or 14.10 driver might be faster, but maybe I should look into it.  If not I will just have to reduce the size and frame rate of videos that I take with my new camera.  Just asking............

Thanks to you guys for responding.

---

### Post by Mark Phelps on 2015-04-06
The difference in "speed" in video adapter drivers is due to the degree to which hardware acceleration is supported by the driver.  In the Nvidia/AMD worlds, the open source driver provides very little hardware acceleration; the restricted driver, a lot.

In the Intel driver world, there are no restricted drivers, so there's very likely to be no difference in "speed" due to the different versions of the drivers.

---

