---
title: "HDD Temperature no longer monitered with latest kernel update"
date: 2007-06-08
forum: General Help
---

### Post by ramjet_1953 on 2007-06-08
I downloaded the latest kernel update this morning and noticed that Hardware Sensors Monitor applet can no longer monitor my HDD temperature.

I tried manually re-starting the hddtemp daemon, but to no avail.

The HDD appears in the applet's list, but no icon is displayed on my top bar.
The CPU temperature is being displayed OK.

I also noticed that my HDD is now referred to as /dev/sda instead of /dev/hda.

I thought that the issue with scsi emulation had been sorted out in the previous update?

Anyone having the same problem?

Regards,
Roger :cool:

---

### Post by ramjet_1953 on 2007-06-08
Duh!

Sorted it!

What happened was that for some reason, when I updated the kernel, it unchecked the HDD temperature sensor and when you open the window for the sensors applet, it needs to be maximised, as the check box is hidden, unless you do this.

Regards,
Roger :cool:

---

