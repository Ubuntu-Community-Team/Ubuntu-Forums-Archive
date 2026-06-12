---
title: "After using nvidia-xconfig, cannot reboot with a GUI."
date: 2013-05-12
forum: General Help
---

### Post by Calinou on 2013-05-12
Hi, fresh install of Xubuntu 13.04.

I used "sudo nvidia-xconfig" after installing nvidia-319 from the xorg-edgers PPA. I added "Option "CoolBits" "4"" to the "Device" section of /etc/X11/xorg.conf for fan control.

Reboot: just a bunch of console lines.

Live CD, remove CoolBits 4 then reboot: black screen.

Live CD, remove xorg.conf: works fine but no fan control. See below.

What can I do to fix the whole thing? I don't want to reinstall again.

Note that the driver worked fine before using nvidia-xconfig. Also, when not using nvidia-xconfig, I do not have any xorg.conf.

Thanks for helping.

**EDIT:** partially solved by removing xorg.conf. Stuff works fine now but I can't control fan speed. This is quite important since my GTX 570 (a reference one) is already quite noisy at idle, but even noisier at load (and I found out that forcing its speed to 40% doesn't make it overheat at all, 60°C in load). Was fan control removed in 319.xx?

---

