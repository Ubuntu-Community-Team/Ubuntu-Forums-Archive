---
title: "Display resolution switches automatically when TV turned off and on again"
date: 2014-02-16
forum: General Help
---

### Post by lonavera on 2014-02-16
Hello,

I am using Ubuntu 13.10 with KDE Desktop (Installed Ubuntu and added KDE. Is this Kubuntu???). I using the nvidia driver.

```
+------------------------------------------------------+                       
| NVIDIA-SMI 5.319.60   Driver Version: 319.60         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 525M     Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   51C  N/A     N/A /  N/A |      182MB /  2047MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
```

It is connected to my TV (better my audio receiver) using HDMI. Sometimes, when I turn off my TV and turn it on again, the resolution is automatically changed from 1080p to 720p. What can cause this? It always rearranges my desktop, causes KDE OpenGL to hang up and is terribly anoing. I have not much Ideas but found some log entries in Xorg.0.log that may help.

```
< [  1801.806] (II) NVIDIA(GPU-0): Display (ONKYO Corporation TX-NR609 (DFP-1)) does not support
< [  1801.806] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
< [  1801.806] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
< [  1801.807] (**) NVIDIA(0):     device ONKYO Corporation TX-NR609 (DFP-1) (Using EDID
< [  1801.807] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
< [  1801.870] (II) NVIDIA(GPU-0): Display (ONKYO Corporation TX-NR609 (DFP-1)) does not support
< [  1801.870] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
< [  1801.870] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
< [  1801.870] (**) NVIDIA(0):     device ONKYO Corporation TX-NR609 (DFP-1) (Using EDID
< [  1801.870] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
< [  1802.190] (II) NVIDIA(0): Setting mode "HDMI-0: 1280x720 @1280x720 +0+0 {ViewPortIn=1280x720, ViewPortOut=1280x720+0+0}"
< [  1802.419] (II) NVIDIA(GPU-0): Display (ONKYO Corporation TX-NR609 (DFP-1)) does not support
< [  1802.419] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
< [  1802.419] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
< [  1802.419] (**) NVIDIA(0):     device ONKYO Corporation TX-NR609 (DFP-1) (Using EDID
< [  1802.419] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
< [  1802.512] (II) NVIDIA(GPU-0): Display (ONKYO Corporation TX-NR609 (DFP-1)) does not support
< [  1802.512] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
< [  1802.512] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
< [  1802.512] (**) NVIDIA(0):     device ONKYO Corporation TX-NR609 (DFP-1) (Using EDID
< [  1802.512] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
< [  1802.557] (II) NVIDIA(GPU-0): Display (ONKYO Corporation TX-NR609 (DFP-1)) does not support
< [  1802.557] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
< [  1802.557] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
< [  1802.557] (**) NVIDIA(0):     device ONKYO Corporation TX-NR609 (DFP-1) (Using EDID
```

Can someone please help me?

Thanks in advance
lonavera

---

### Post by lonavera on 2014-02-18
push

---

### Post by teemu-3 on 2014-08-13
> **lonavera said:**
> push  

Old thread, but I just had a similar issue. I have a Kubuntu box connected to an AV receiver which is in turn connected to an LCD TV. When changing from 12.04 to 14.04, I noticed the following behavior: 

- When first turning the AV receiver on and turning the TV on afterwards, the resolution was messed up. When turning the AV receiver on while the TV was already on, everything was fine. 
- xrandr showed that the native resolution 1920x1080 was available all the time but for some reason a lower resolution was selected  when the AV receiver was turned on (in case the TV was off).
- the resolution could be changed, but this became quite annoying ( not to mention messed up menus etc. after changing resolution) 

I worked around this by disabling KScreen 2 service altogether (command 'kcmshell4 kded', then disable from list). KScreen is the screen management software, though, so you should think twice before disabling it if you have multiple monitors or otherwise a more complicated setup. There is probably a better solution, but hey, this worked for me :)

---

