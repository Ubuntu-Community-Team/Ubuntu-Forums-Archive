---
title: "UDISKSCTL: spins up all drives on 20.04 but not on 18.04 :-|"
date: 2020-09-09
forum: General Help
---

### Post by dinkidonk on 2020-09-09
I have a bunch of HDD's in my computer, all encrypted using LUKS, and all drives are normally unmounted and in standby mode with "hdparm -y /dev/sd*". Whenever I want to access one of the drives, either using Gnome Disks or Dolphin as GUI or the command line (udisksctl unlock -b /dev/sd* && udisksctl mount -b /dev/sd*) ALL HDD's in the computer are spun up for no reason. This behaviour is only present on *buntu 20.04, on *buntu 18.04 only the requested drive was spun up, as expected. If I use "cryptsetup unlock /dev/sd* && mkdir /path/to/mount && mount /dev/some-mapper /path/to/mount" only the requested drive is spun up, but this requires sudo which is not wanted.

Is this a bug? Any workarounds?

Thanks! :-)

---

