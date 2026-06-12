---
title: "drives in mdadm array lose configuration when unplugged"
date: 2013-05-01
forum: General Help
---

### Post by acidd22 on 2013-05-01
I've been using mdadm arrays for a couple years, and i noticed that i can pop the drives into a new computer and if i have enough to build the array, mdadm discovers them and puts it together.  I recently switched to an sata controller on a PCI card and noticed that when i unplug one of my drives in a 6 drive raid (4 drives, 2 spares), i have to rebuild that drive after i plug it in.  This seems to be different than when i used to plug a drive in and it discovered where it belonged in the array.  So if i unplug TWO drives and reboot, then plug them back in and reboot both drives need rebuilt.  is this normal?  is it because the 5 connected drives were writing to the disks and the 6th drive got out of sync?  I don't want to lose my array if a few get unplugged and its lost even after i reconnect them.

---

### Post by SaturnusDJ on 2013-05-02
When a drive of the array gets unplugged, and meanwhile the content on the array changes, it is needed to resync. I've read it is possible to speed up this process by using a bitmap. Performance is a bit affected by this.
There should not be a resync when unplugging spares.
If you stop the array before unplugging (and don't start it until you plug back in), no resync will take place.

---

