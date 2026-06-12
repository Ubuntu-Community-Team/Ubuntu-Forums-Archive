---
title: "Ubuntu boots on a black screen"
date: 2013-11-21
forum: General Help
---

### Post by aleksandar.rachkov on 2013-11-21
Hi,

When I cam home today, I found out my computer with a black screen and a flashing underscore line. I restarted it and after the grub, I have only a black screen with underscore flashing.

Last time I touched my computer was last night, when I restarted it for some update. I have not touched it since.

Since I dual boot it alongside Windows 8, I am writing now from Win8.

Thank you for your help in advance,
Alex

---

### Post by fantab on 2013-11-22
There could be two reasons for the 'black Scree': either you use a 'proprietory Graphic driver' and its update may NOT have installed properly or your grub files got corrupted.

To confirm it its Graphic driver related try [**NOMODEST**]("http://ubuntuforums.org/showthread.php?t=1613132") during ubuntu boot. If it turns out to be a graphic issue then after booting with 'nomodest' install your 'proprietory graphics driver'. You can do this by checking the "Additional Drivers" from Software Center-> Software sources..

If its not a Graphics issue then boot with your Ubuntu DVD/USB, download, install and run [**BOOT-REPAIR**]("https://help.ubuntu.com/community/Boot-Repair"). The 'Recommended Repair' is usually enough. Make a note of the LINK which Boot-repair creates for *BootInfo Summary*, if you still find your Ubuntu not booting then post the link here.

Good luck.

---

