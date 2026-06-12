---
title: "sudo bruteforce-luks returns"
date: 2017-08-30
forum: General Help
---

### Post by bold33 on 2017-08-30
```
sudo bruteforce-luks -t 1 -l 20 -m 27  /dev/sda
``` returns ```
Error: either /dev/sda is not a valid LUKS volume, or you don't have permission to access it.

```

/dev/sda is a luks partition.I made it 2 years ago. How do I get permission to access it?

xubuntu 17.04 64 bits, passphrase lost yesterday, you may want to read: [https://ubuntuforums.org/showthread.php?t=2370072&p=13681178#post13681178](https://ubuntuforums.org/showthread.php?t=2370072&p=13681178#post13681178)

thanks

---

### Post by TheFu on 2017-08-30
You are referencing the entire drive.  Normally, dm-crypt would be setup on a partition inside the drive.  I'd check that first. It is a common thing.

Use **parted -l /dev/sda** to see which, if any, partitions exist.

If you want to unlock/decrypt the md-crypt data, use the **cryptsetup** tool.  Some GUI file managers, **caja**, will do this automatically (I assume if all the crypt-stuff is loaded on the machine already) - prompting for the passphrase and loading any logical volumes inside.  There is an edge situation that can happen if the names of the VGs or LVs conflict with an existing VG or LV used by the current system. Then you'll need to rename those - but that happens AFTER dm-crypt has been opened.

Whenever encryption is used, having excellent backups that you've tested the restore from is mandatory.  Trying to recall how to restore yrs later is harder than taking notes at the time of creation, I've found.

---

