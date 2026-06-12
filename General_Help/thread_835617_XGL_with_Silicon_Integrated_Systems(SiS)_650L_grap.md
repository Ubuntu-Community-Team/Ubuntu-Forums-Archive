---
title: "XGL with Silicon Integrated Systems(SiS) 650L graphics card on Dell Inspiron 1000"
date: 2008-06-20
forum: General Help
---

### Post by bonini on 2008-06-20
I've been using ubuntu for a while on my desktop, and just put xubuntu on an old laptop that was given to me.  I am trying to get compiz fusion working, but I don't have XGL working.  The graphics card doesn't show up in Applications --> System --> Hardware Drivers.  I'm not sure if compiz would even be worth running or if its even possible to run, but I figured I'd give it a try anyway.  I already installed compiz, compizconfig-settings-manager, emerald, libgl1-mesa-dri, and libgl1-mesa-glx, I'm not sure what those last two are exactly, I tried downloading them after seeing this:[http://ubuntuforums.org/showthread.php?t=623752](http://ubuntuforums.org/showthread.php?t=623752)

The laptop is a Dell Inspiron 1000, 2.2 Ghz processor, 256 MB of Ram and has a SiS 650L integrated graphics card.

Any help would be appreciated.

---

### Post by bonini on 2008-06-21
Anyone..?
I basicly just need to know if SiS integrated graphics cards are compatible with Xgl and if so how do I get it working.

---

### Post by Forlong on 2008-06-22
I doubt that it's possible to run Compiz on that card.

What's the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by bonini on 2008-06-22
So the output from compiz-check:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   Xfce
 Graphics chip:         Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...grep: /home/john/.config/xfce4/mcs_settings/wmtweaks.xml: No such file or directory
           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

```

If I needed more confirmation that this card won't work I found it here:[http://www.winischhofer.eu/linuxsispart1.shtml#12](http://www.winischhofer.eu/linuxsispart1.shtml#12)
> There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.

Thanks anyway

P.S. compiz-check is a very useful tool Ill try to remember for next time.

---

### Post by Forlong on 2008-06-22
Can you please re-download Compiz-Check and run it (and post the whole output) again?
Thank you.

---

