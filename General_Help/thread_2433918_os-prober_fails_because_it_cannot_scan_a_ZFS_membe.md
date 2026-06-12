---
title: "os-prober fails because it cannot scan a ZFS member"
date: 2019-12-27
forum: General Help
---

### Post by untouchedwagons on 2019-12-27
I replaced Fedora with Ubuntu 19.10 on ZFS. Before installing I unplugged my SSD that has windows 10 on it so that it wouldn't get messed up. After rebooting into Ubuntu I connected the SSD and then ran update-grub but so that I can dual-boot but os-prober failed:

```
device-mapper: reload ioctl on osprober-linux-nvme0n1p5  failed: Device or resource busy
Command failed.
```

For some reason os-prober is trying to find other operating systems but I guess it can't read ZFS and instead of continuing it just exits. Any ideas?

---

### Post by oldfred on 2019-12-28
What is nvme0n1p5 ?

sudo parted -l

If that is your Windows, is Windows fast boot which sets hibernation flag set?
Linux driver will not see hibernated Windows. And Windows updates often turn fast start up back on, even if you turned it off before.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

---

### Post by untouchedwagons on 2019-12-28
nvme0n1p5 is the zfs member of the rpool pool. I'm pretty sure fast boot is disabled because Fedora was able to find windows just fine and add a grub menu entry for it

---

### Post by untouchedwagons on 2019-12-28
I just tried to boot into windows directly using my motherboard's boot menu but that wasn't an option. That's weird. I installed Windows after I installed Fedora, maybe for some silly reason windows put its EFI stuff on the same partition as Fedora's which got nuked by Ubuntu.

---

### Post by oldfred on 2019-12-28
Windows normally puts its UEFI boot files on drive set as default in UEFI boot. And usually same drive you install it into.
You can run Windows repairs to restore /EFI/Microsoft & all the files it needs in the ESP. Or if that exist just add a new entry in UEFI using efibootmgr.

Ubuntu would not delete Windows folder in ESP.

Do not know zfs, but does your Ubuntu have driver for that? If not part of install, it does not have drivers for other formats.

---

### Post by untouchedwagons on 2019-12-28
19.10 has experimental support for root on ZFS

---

