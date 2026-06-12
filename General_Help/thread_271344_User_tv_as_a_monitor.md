---
title: "User tv as a monitor"
date: 2006-10-04
forum: General Help
---

### Post by hnugz on 2006-10-04
I have just setup ubuntu 6.06 with myth 0.20 and I wanted to be able to connect the pc to my tv using s-video.  I plugged it in and the post screens appear ok.  As soon as grub starts to load the picture is skewed and unreadable.  I would assume this is a resolution issue?

I have an ati radeon 9800 pro vid card.  How can configure unbutu to display on the tv?  Thanks.

---

### Post by reclusivemonkey on 2006-10-30
> **hnugz said:**
> I have just setup ubuntu 6.06 with myth 0.20 and I wanted to be able to connect the pc to my tv using s-video.  I plugged it in and the post screens appear ok.  As soon as grub starts to load the picture is skewed and unreadable.  I would assume this is a resolution issue?

I have an ati radeon 9800 pro vid card.  How can configure unbutu to display on the tv?  Thanks.

You'll need to plug a monitor back in to configure xorg.conf. I am not sure whether this will work as I have a NVIDIA card. Here is the relevant section from my xorg.conf; it might work for you, but I don't profess to know much about this, I just know it works for my MythTV setup, using S-Video;

```

Section "Device"

    #VideoRam    131072
    # Insert Clocks lines here if appropriate
    Identifier     "** NVIDIA (generic)                   [nv]"
    Driver         "nvidia"
        Option  "TwinView"
        Option  "SecondMonitorHorizSync"        "30-60"
        Option  "SecondMonitorVertSync"         "50-60"
        Option  "MetaModes"                      "720x576, 720x576"
        Option  "TwinViewOrientation"           "Clone"
        Option  "ConnectedMonitor"              "TV"
        Option  "TVStandard"                    "PAL-I"
        Option  "TVOutFormat"                   "S-VIDEO"
EndSection

```

Obviously, change the nvidia driver and identifier. Make sure you have both your monitor and TV connected at the same time at first, so if something goes screwy, you at least have a chance of seeing the error ;-)

If you are in America, you will obviously need to change PAL-I to NTSC.

---

