---
title: "Ubuntu Hibernation Shutdown Problems"
date: 2019-09-17
forum: General Help
---

### Post by tompouce on 2019-09-17
Hi! 

I'm currently on Ubuntu 19.04 with Kernel 5.3.0 but the problem has been happening for the past month or so and back then I was on Ubuntu 18.10 with kernel 5.1.* and 5.2.*

I'm using uswsusp to hibernate my XPS laptop. But for the past weeks, it hibernates without actually shutting down so I need to manually reboot my laptop and lose everything that was supposed to be "saved". I noticed I'm all over the place trying to reconfigure uswsusp properly, do I really need pm-utils for this? I noticed I can trigger hibernation via systemd, pm-utils, s2disk, etc. What is really THE tool I need?

I tried setting hibernate_mode to shutdown, also set /sys/power/disk to [shutdown] I noticed it always sets itself back to [platform] could that be part of my problem?

Any ideas or suggestions are welcome!

Thanks a lot and have a wonderful day!

---

### Post by tompouce on 2019-09-17
pm-suspend.log: [http://ix.io/1Vz9](http://ix.io/1Vz9)

---

### Post by tompouce on 2019-09-17
journalctl -b: [https://termbin.com/yuym](https://termbin.com/yuym)

---

### Post by ej-112 on 2019-09-18
Could passing acpi settings in grub help perhaps?
To give it a try type "sudo strings /sys/firmware/acpi/tables/DSDT | grep -i windows"
Get the latest windows entry there and in grub press "e" to modify the ubuntu entry
In the line that says 'linux /boot/vmlinuz quiet splash', add '  acpi_osi=! acpi_osi="Windows XXXX" ' after quiet splash replacing  Windows XXXX with what you got in the previous command
Then press ctrl+x or F10 to boot.

---

