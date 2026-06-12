---
title: "lenovo Z50-70 battery not charging while using Ubuntu 14.04.2"
date: 2017-12-05
forum: General Help
---

### Post by nakul777 on 2017-12-05
Hi All,

I have installed the above mentioned OS for almost 3 yrs. Initially there was no problem with the battery. I updated the OS (Ubuntu 14.04.2). The system worked fine for few days. But now the battery does not charge at all while the OS is running. When the OS is shut down, the battery charges to 98%. When the OS gets started, it shows discharging. Now I have also removed the battery and connected the power supply directly. But the system does not even powers on.  I also reset the bios back to initial state but to no use.

On searching the syslog file, following relevant information was found:-


```
Dec  5 18:41:39  Lenovo-Z50-70 kernel: [    2.875842] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec  5 18:41:39  Lenovo-Z50-70 kernel: [    2.877487] ACPI: Battery Slot [BAT0] (battery present)
``` 

I also installed battery-monitor and powertop but to little help.

Thanking you for the help.

Regards,
nakul777

---

### Post by gordintoronto on 2017-12-05
This really sounds like a hardware problem.

---

### Post by johnnyzee on 2018-01-06
I have a similar problem running Ubuntu 16.04 on a Toshiba laptop in that the battery stops charging shortly after booting. If I unplug it from power either at the PC port or the power source and plug in again, it starts charging. I have replaced the battery and tried two different cables / power adaptors. After plugging in and out four or five times it seems to fix the problem and continues charging. I can wiggle the adaptor pin in the PC port to see if it is a connection issue but that seems to make no difference unless I cut the power and reconnect it.

My limited research and the previous post suggests that it has to do with the ACPI software that controls charging but I do not know how to approach that. Any advice would be appreciated.

---

### Post by #&amp;thj^% on 2018-01-06
I really Like this for Linux [https://launchpad.net/~linrunner/+archive/ubuntu/tlp](https://launchpad.net/~linrunner/+archive/ubuntu/tlp)
I prefer the app installed from the above PPA. (Just my 2 cents worth)

Some more information to absorb: [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html)
And: [https://wiki.archlinux.org/index.php/TLP](https://wiki.archlinux.org/index.php/TLP)


Sometime it is just as easy to first:
Unplug your Power Cord, Open a video or Music and run till the battery runs Very Low.
Now if you can remove the  battery.
Reattach the power cord and reinstall the battery and power on your machine.
This has worked for me on more than a handful of various lappy's
**Note Please make sure you are first finished with all your mission critical work and saved.**

---

