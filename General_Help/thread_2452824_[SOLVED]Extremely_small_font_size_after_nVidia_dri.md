---
title: "[SOLVED]Extremely small font size after nVidia driver installation"
date: 2020-10-29
forum: General Help
---

### Post by gdesilva on 2020-10-29
This is the solution that worked for me.

ISSUE : Installed Lubuntu 20.04 on a system with nVidia card and connected to a LCD display unit via a HDMI connector. After installation everything looks good with the nouveau driver but when I installed the nVidia driver the font size on the desktop becomes so small and hardly readable. 

SOLUTION:

The solution described here was found in [https://www.kubuntuforums.net/showthread.php/62680-Font-scales-With-HDMI-screen-ratios/page2?](https://www.kubuntuforums.net/showthread.php/62680-Font-scales-With-HDMI-screen-ratios/page2?) - thanks to phonic-otg. Read the last post.

1. Go to /usr/share/X11/xorg.conf.d
2. Edit 10-nvidia.conf file - this file contains only the definition for "OutputClass"
3. Add the following to this file

    Section "Monitor"
            Identifier "Monitor0"
            Option "DPI" "100x100"
    EndSection

    Section "Device"
            Identifier "Device0"
            Driver "nvidia"
            Option "UseEdidDpi" "False"
            Option "DPI" "100x100"
    EndSection

4. Save file and reboot

---

### Post by sudodus on 2020-10-29
Thanks for sharing this tweak :-)

---

