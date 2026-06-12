---
title: "Trouble logging in"
date: 2018-05-08
forum: General Help
---

### Post by jeo7 on 2018-05-08
I am running Ubuntu 18.04 with gdm3 and the vanilla Gnome Shell, and I have an intermittent problem that is not so rare that I can ignore it. I have two accounts on my system. One is an administrator account and the other is my work account. Sometimes when I log off of one account and try to log into the other account, I get a blank screen and nothing happens. And then sometimes it returns me to the login screen. Other times everything behaves as normal. But this happens at least once per day. Any ideas how to remedy this?

---

### Post by Xian on 2018-05-08
Most likely has to do with your graphics driver ... are you using [COLOR=#000000]nvidia?[/COLOR]

---

### Post by jeo7 on 2018-05-08
No. I have an AMD A12 series processor with integrated R7 series graphics, and I'm using the default Ubuntu driver.

---

### Post by Xian on 2018-05-08
Check for any boot messages/errors:

```
dmesg | egrep 'drm|radeon'
```

---

### Post by jeo7 on 2018-05-09
This is what I got:

```

[    1.246696] Warning: fail to get symbol drm_fb_helper_release_fbi, replace it with kcl stub
[    1.312247] [drm] amdgpu kernel modesetting enabled.
[    1.312249] [drm] amdgpu version: 18.20.2.15
[    1.321270] fb: switching to amdgpudrmfb from EFI VGA
[    1.321856] [drm] initializing kernel modesetting (CARRIZO 0x1002:0x9874 0x17AA:0x39FF 0xC8).
[    1.321873] [drm] register mmio base: 0xF0D00000
[    1.321874] [drm] register mmio size: 262144
[    1.321883] [drm] add ip block number 0 <vi_common>
[    1.321884] [drm] add ip block number 1 <gmc_v8_0>
[    1.321885] [drm] add ip block number 2 <cz_ih>
[    1.321886] [drm] add ip block number 3 <powerplay>
[    1.321888] [drm] add ip block number 4 <dm>
[    1.321889] [drm] add ip block number 5 <gfx_v8_0>
[    1.321890] [drm] add ip block number 6 <sdma_v3_0>
[    1.321891] [drm] add ip block number 7 <uvd_v6_0>
[    1.321892] [drm] add ip block number 8 <vce_v3_0>
[    1.321893] [drm] add ip block number 9 <acp_ip>
[    1.321905] [drm] UVD is enabled in physical mode
[    1.321907] [drm] VCE enabled in physical mode
[    1.334135] [drm] BIOS signature incorrect 1e 0
[    1.334221] [drm] vm size is 64 GB, 2 levels, block size is 10-bit, fragment size is 9-bit
[    1.334232] [drm] Detected VRAM RAM=512M, BAR=512M
[    1.334233] [drm] RAM width 128bits UNKNOWN
[    1.334539] [drm] amdgpu: 512M of VRAM memory ready
[    1.334541] [drm] amdgpu: 7425M of GTT memory ready.
[    1.334550] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.334590] [drm] PCIE GART of 1024M enabled (table at 0x000000F400040000).
[    1.334741] [drm] Chained IB support enabled!
[    1.336324] [drm] Found UVD firmware Version: 1.91 Family ID: 11
[    1.336334] [drm] UVD ENC is disabled
[    1.337343] [drm] Found VCE firmware Version: 52.4 Binary ID: 3
[    1.341647] [drm] DM_PPLIB: values for Engine clock
[    1.341649] [drm] DM_PPLIB:     30000
[    1.341650] [drm] DM_PPLIB:     48000
[    1.341650] [drm] DM_PPLIB:     53334
[    1.341651] [drm] DM_PPLIB:     57600
[    1.341651] [drm] DM_PPLIB:     62609
[    1.341652] [drm] DM_PPLIB:     68572
[    1.341652] [drm] DM_PPLIB:     72000
[    1.341652] [drm] DM_PPLIB:     75790
[    1.341653] [drm] DM_PPLIB: Validation clocks:
[    1.341654] [drm] DM_PPLIB:    engine_max_clock: 75790
[    1.341654] [drm] DM_PPLIB:    memory_max_clock: 93300
[    1.341654] [drm] DM_PPLIB:    level           : 0
[    1.341656] [drm] DM_PPLIB: values for Display clock
[    1.341656] [drm] DM_PPLIB:     30000
[    1.341656] [drm] DM_PPLIB:     40000
[    1.341657] [drm] DM_PPLIB:     49656
[    1.341657] [drm] DM_PPLIB:     62609
[    1.341657] [drm] DM_PPLIB:     68572
[    1.341658] [drm] DM_PPLIB:     75790
[    1.341658] [drm] DM_PPLIB:     80000
[    1.341658] [drm] DM_PPLIB:     84706
[    1.341659] [drm] DM_PPLIB: Validation clocks:
[    1.341659] [drm] DM_PPLIB:    engine_max_clock: 75790
[    1.341660] [drm] DM_PPLIB:    memory_max_clock: 93300
[    1.341660] [drm] DM_PPLIB:    level           : 0
[    1.341661] [drm] DM_PPLIB: values for Memory clock
[    1.341661] [drm] DM_PPLIB:     66700
[    1.341661] [drm] DM_PPLIB:     93300
[    1.341662] [drm] DM_PPLIB: Validation clocks:
[    1.341662] [drm] DM_PPLIB:    engine_max_clock: 75790
[    1.341663] [drm] DM_PPLIB:    memory_max_clock: 93300
[    1.341663] [drm] DM_PPLIB:    level           : 0
[    2.568329] [drm:hwss_wait_for_blank_complete [amdgpu]] *ERROR* DC: failed to blank crtc!
[    2.568358] [drm] Display Core initialized with v3.1.41!
[    2.575048] [drm] SADs count is: -2, don't need to read it
[    2.576226] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.576227] [drm] Driver supports precise vblank timestamp query.
[    3.602263] [drm] UVD initialized successfully.
[    3.802169] [drm] VCE initialized successfully.
[    3.807916] [drm] fb mappable at 0x1FF61E000
[    3.807917] [drm] vram apper at 0x1FF000000
[    3.807917] [drm] size 4325376
[    3.807918] [drm] fb depth is 24
[    3.807918] [drm]    pitch is 5632
[    3.808210] fbcon: amdgpudrmfb (fb0) is primary device
[    3.808294] amdgpu 0000:00:01.0: fb0: amdgpudrmfb frame buffer device
[    3.837808] [drm] Initialized amdgpu 3.25.0 20150101 for 0000:00:01.0 on mino 
```

---

### Post by jeo7 on 2018-05-09
I solved this problem, but I'm not going to post what I did because what I did was not legitimate and I almost broke my system. I'm afraid if I posted what I did, others would wind up breaking their systems and might not be able to get them back. I lost the desktop manager as well as Xorg, and I spent 3 hours working with the command line to get my system back. And when it came back ... it worked! All my problems with logging in, hesitating video playback, and problems waking the system from suspend just vanished. Though I must say that I am using lightdm as my desktop manager now even though my desktop environments remain vanilla Gnome.

One question I do have, however, is how do I know whether hardware acceleration is working or not?

---

### Post by Xian on 2018-05-09
> **jeo7 said:**
> 
One question I do have, however, is how do I know whether hardware acceleration is working or not?


Install (if not already present) the mesa-utils package from universe:
[https://packages.ubuntu.com/bionic/mesa-utils](https://packages.ubuntu.com/bionic/mesa-utils)


Then from the command line:
```
glxinfo | grep "direct rendering"
```
The output should be:
```
direct rendering: Yes
```

---

### Post by jeo7 on 2018-05-09
Thanks for your help, Xian. I really appreciate it.

The system is telling me that mesa-utils is installed and already the newest version. And I indeed do get the result you posted, i.e. Direct rendering: Yes.

---

### Post by jeo7 on 2018-05-09
If I run the following from a terminal:

```

mpv --hwdec=vdpau B.mp4 
```

then the video plays for a few seconds after which the video stops and the terminal keeps writing this:


```
 
AV: 00:00:13 / 00:03:52 (5%) A-V:  0.000
[vo/opengl] Mapping hardware decoded surface failed.
AV: 00:00:13 / 00:03:52 (5%) A-V:  0.000
[vo/opengl] Mapping hardware decoded surface failed.

```

Printing this out continues until the end of the file is reached (I guess).

---

### Post by Xian on 2018-05-09
> **jeo7 said:**
> If I run the following from a terminal:

```

mpv --hwdec=vdpau B.mp4 
```

then the video plays for a few seconds after which the video stops and the terminal keeps writing this:


```
 
AV: 00:00:13 / 00:03:52 (5%) A-V:  0.000
[vo/opengl] Mapping hardware decoded surface failed.
AV: 00:00:13 / 00:03:52 (5%) A-V:  0.000
[vo/opengl] Mapping hardware decoded surface failed.

```

Printing this out continues until the end of the file is reached (I guess).

I would suggest you start a new thread about this issue in the Multimedia Software forum section.

---

