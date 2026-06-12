---
title: "mdadm degraded raid preventing boot"
date: 2013-01-27
forum: General Help
---

### Post by Ozymandias007 on 2013-01-27
mdadm throws error about degraded raid, choosing "yes" continues the boot but hangs a few seconds later. This was a result of removing a softraid from the GUI (RAID 5 - 3 drives).  Ubuntu install is on non-RAID drive not associated with RAID 5 setup.

Upon removal of the 3 RAID drives, the system will boot properly.  When they are connected, they show back up as a RAID5 container.  How do I remove this container from all drives?

---

### Post by Bucky Ball on 2013-01-27
[I]Thread moved to [B]General Help

Reason:[/B][/I] Not related to desktop environments.

Welcome to the forums.

---

### Post by tgalati4 on 2013-01-27
Boot a Live DVD, mount the boot drive, open a terminal and post the output of:

```
cat /media/disk/etc/fstab
sudo fdisk -l
```

Normally you would put a comment # in front of the RAID to prevent automounting and then troubleshoot once you have booted.  It could be a power supply or a hardware problem.  Sounds strange that you can't boot without the RAID.

---

### Post by SaturnusDJ on 2013-01-29
I experienced something similar. It doesn't seem to be a bug, but more a flaw in design.
After saying yes, initramfs should come up. Typing exit there should resume the boot process.

If you want a clean removal, the best is to reconnect the array (I understand this is possible for you and booting goes fine then).

Edit /etc/mdadm/mdadm.conf
Remove the array you don't want anymore.
Run ```
update-initramfs -u
```

Then, like tgalati4 says, edit /etc/fstab. Remove the md device (or corresponding uuid) there.


If booting with the array connected is not possible anymore, use a live cd, chroot to the original install and do they same thing as above.

---

