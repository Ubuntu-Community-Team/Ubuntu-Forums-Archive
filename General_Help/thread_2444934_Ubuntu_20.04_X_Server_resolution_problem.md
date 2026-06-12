---
title: "Ubuntu 20.04 X Server resolution problem"
date: 2020-06-06
forum: General Help
---

### Post by pankaj13 on 2020-06-06
Hi,


Here is more information about the problem related to X settings on my Ubuntu 20.04 desktop.


$ lspci | grep VGA
03:00.0 VGA compatible controller: NVIDIA Corporation GF100GL [Quadro 5000] (rev a3)




And I have two monitors: Dell U2412M and Dell E2414H. The issue is that Dell U2414M has 1920x1200 resolution and works great but Dell E2414H only has 1280x1024 resolution (as the highest setting). Under Nvidia X Server Settings, this one actually shows up as NVIDIA_LCD_VGA and not as Dell like the other monitor.


My /etc/X11/xorg.conf file is [https://pastebin.com/Pzf2jbjx](https://pastebin.com/Pzf2jbjx)


Both the monitors had 1920x1200 resolution and were working find till one of the recent updates from Ubuntu and I cannot get the higher resolution back on second monitor.


Any tips or guidance would be appreciated.
Regards,


Pankaj

---

### Post by pankaj13 on 2020-06-06
Attached is the output from nvidia-bug-report.sh for reference.
Thanks.

---

