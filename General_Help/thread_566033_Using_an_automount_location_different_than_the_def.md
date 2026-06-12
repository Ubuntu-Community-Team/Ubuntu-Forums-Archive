---
title: "Using an automount location different than the default /media"
date: 2007-10-03
forum: General Help
---

### Post by beysseb on 2007-10-03
Hi All,

How one would change the default automount location of USB devices from /media to a different folder? 

For the DVDrom I can do that manually in /etc/fstab, but for USB devices there is no mounting location explicitely expressed in fstab, yet if I plug a USB pen drive it is automatically mounted in /media, which configuration file can be modified to change this mounting location?


Reason: the use of /media as the default mounting location conflicts with other environments settings over which I have no control.

Thanks,
Seb

---

### Post by bodhi.zazen on 2007-10-03
In theory, the easiest way is to list the device in fstab, using LABEL or UUID

LABEL=<u-name-it> /mnt/usb ....

In practice it does not always work ...

See this link for how to label and mount : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

In that case I believe you would need to configure gnome-volume-manager, which I find poorly documented ...

Hopefully someone here has more experience ...

---

