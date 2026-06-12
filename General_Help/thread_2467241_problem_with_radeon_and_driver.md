---
title: "problem with radeon and driver"
date: 2021-09-20
forum: General Help
---

### Post by jgw on 2021-09-20
I am having a problem with my display (I think) and Kodi.  I have spent days trying to figure it out and I just get more confused. 
Here are some things I have:

Radeon Driver:
```
reg@movies:~$ sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
greg@movies:~$ dmesg | grep -i radeon
[    0.319277] smpboot: CPU0: AMD A8-7650K Radeon R7, 10 Compute Cores 4C+6G (family: 0x15, model: 0x30, stepping: 0x1)
[   30.920313] [drm] radeon kernel modesetting enabled.
[   30.920388] fb0: switching to radeondrmfb from VESA VGA
[   30.920707] radeon 0000:00:01.0: vgaarb: deactivate vga console
[   30.921325] radeon 0000:00:01.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   30.921332] radeon 0000:00:01.0: GTT: 2048M 0x0000000040000000 - 0x00000000BFFFFFFF
[   30.921488] [drm] radeon: 1024M of VRAM memory ready
[   30.921491] [drm] radeon: 2048M of GTT memory ready.
[   31.073962] [drm] radeon: dpm initialized
[   31.164553] radeon 0000:00:01.0: WB enabled
[   31.164581] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000040000c00
[   31.164586] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000040000c04
[   31.164590] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000040000c08
[   31.164593] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c
[   31.164597] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000040000c10
[   31.165060] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000078d30
[   31.165226] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000040000c18
[   31.165230] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c
[   31.165629] radeon 0000:00:01.0: radeon: using MSI.
[   31.165665] [drm] radeon: irq initialized.
[   32.432879] [drm] Radeon Display Connectors
[   32.683954] fbcon: radeondrmfb (fb0) is primary device
[   32.684083] radeon 0000:00:01.0: [drm] fb0: radeondrmfb frame buffer device
[   32.715271] [drm] Initialized radeon 2.50.0 20080528 for 0000:00:01.0 on minor 0

```

Vainfo
```
greg@movies:~$ vainfo
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/radeonsi_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Mesa Gallium driver 21.0.3 for AMD KAVERI (DRM 2.50.0, 5.11.0-34-generic, LLVM 12.0.0)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileNone                   :	VAEntrypointVideoProc
greg@movies:~$ 


```

I also have a report from glxinfo if you want it.

Basically I am not even sure what driver I am using.  Sometimes it says its "Radeon" and, sometimes "mesa".  I haven't a clue.  All I really know is that I have a problem with Kodi.  I have been to their forum and voiced my problem but there has only been one reply which was not really helpful, other than to possible point at my video stuff.  OH, I just installed 20.04.3 on this machine.  Before that I was running with the same video with absolutely no problems with Kodi.  Now its a disaster.  I open the program choose something to watch, it runs but the screen doesn't clear and the picture doesn't even start until I go through pushing random keys and, in a bit of time I can see the video buried in the initial screen but with a bit more button pushing it starts doing it so I can watch the video.  Then, if I want to watch another there are also no problems.  

I just thought I might get lucky and somebody has an answer.

Thank you......................

---

### Post by GhX6GZMB on 2021-09-20
Your signature says you have an nVidia graphics card. So why are you messing around with Radeon drivers?

---

### Post by QIII on 2021-09-20
The user has a Kaveri APU with an AMD R7 GPU.

If there is actually an NVIDIA unit as well in a hybrid system configuration, one or the other will have to be black listed in the BIOS/EFI and the appropriate driver module used.

---

### Post by jgw on 2021-09-21
Sorry about that.  I am maintaining more than one system and forget about the signiture.  Here is my system:

Computer
Processor	AMD A8-7650K Radeon R7, 10 Compute Cores 4C+6G
Memory	15307MB (4282MB used)
Machine Type	Desktop
Operating System	Ubuntu 20.04.3 LTS
Date/Time	Tue 21 Sep 2021 12:24:35 PM PDT

Display
Resolution	3840x2160 pixels
OpenGL Renderer	AMD KAVERI (DRM 2.50.0, 5.11.0-34-generic, LLVM 12.0.0)
X11 Vendor	The X.Org Foundation

---

### Post by jgw on 2021-09-21
Thank you for the replies.

I went to Kodi and turned off vidpau and that seemed to fix it so it works.  I also suspect I still have a problem with my video driver (not even sure which one I have).   In my reading it looks like whatever I might have it probably needs some kind of update.  Everytime I have messed with video drivers its not ended well.  

Still would appreciate any thoughts on the initial thread whine.

This is the machine I am dealing with:
Processor	                  MD A8-7650K Radeon R7, 10 Compute Cores 4C+6G
Memory	                          15307MB (4282MB used)
Machine Type	                  Desktop
Operating System	          Ubuntu 20.04.3 LTS
Resolution	                  3840x2160 pixels
OpenGL Renderer	          AMD KAVERI (DRM 2.50.0, 5.11.0-34-generic, LLVM 12.0.0)
X11 Vendor	                  The X.Org Foundation

---

### Post by mikewhatever on 2021-09-21
There seems to be nothing wrong with "my video driver". It is "radeon", and it does not need an update.
You broke Kodi with vdpau, but now it is fixed. So, if it's not broken, don't fix it.

---

### Post by jgw on 2021-09-21
Thanks for the help and replies.

I think I have it working, now.   I dinked with it a little and now I can also stop Kodi without going to the system monitor and killing it.

I will mark this as solved.

---

