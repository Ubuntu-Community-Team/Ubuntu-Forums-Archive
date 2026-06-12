---
title: "Dark Screen Problem"
date: 2018-02-13
forum: General Help
---

### Post by gus_zernial on 2018-02-13
I'm using kubuntu 17.10 with kernel 4.14.15-041415-generic, on an Asus Z370-E mobo with integrated Intel 630 (i915) graphics, and the monitor screen is very dark. I've increased screen brightness/contrast settings to max values using the buttons on the monitor, problem is still there.

The monitor is a QNIX QX2710, and both it and the new 630 graphics require some special settings in an xorg, which I've copied below, along with an lsmod and a special line required in /etc/default/grub/. So my question is, are there any other configuration settings I could use to increase brightness.

Thx, Gus

$ cat 20-intel.conf 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
EndSection

Section "Files"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "QNIX"
    ModelName      "2710"
    HorizSync       88.8
    VertRefresh     59.5
    # 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
    Modeline "2560x1440"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
    DisplaySize 597 336
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
    Option         "DRI"    "false" 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes "2560x1440"
    EndSubSection
    Option "UseEDID" "False"
    Option "UseEDIDDPI" "False"
    Option "UseEDIDFreqs" "False"
    Option "ExactModeTimingsDVI" "True"

## Metamode for single QX2710 (2560x1440)
    Option "metamodes" "DFP-0: 2560x1440 +0 +0"

EndSection

$ lsmod | grep i915
i915                 1888256  3
i2c_algo_bit           16384  1 i915
drm_kms_helper        204800  1 i915
drm                   438272  4 i915,drm_kms_helper
video                  45056  2 asus_wmi,i915

$ cat /etc/default/grub | grep i915
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  i915.alpha_support=1"

---

### Post by cruzer001 on 2018-02-13
There could well be settings available for this, I am just not knowledgeable in that area.  The only thing I found that could possibly help is the latest stable kernel (4.15) that would take you off of the alpha build that your currently running.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-CFL-No-Alpha](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-CFL-No-Alpha)

Or you could just load up a copy of 18.04 and give it a test drive.

Good luck

---

