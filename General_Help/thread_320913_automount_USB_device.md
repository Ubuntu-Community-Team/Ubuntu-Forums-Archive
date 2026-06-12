---
title: "automount USB device"
date: 2006-12-18
forum: General Help
---

### Post by bricedebrignaisplage on 2006-12-18
I have a creative player. It is possible to set it in USB storage mode, with a partition of adjustable size (VFAT of course). I am using Dapper.
It works fine if the size of the partition is below 2GB. After that it doesn't automount.
If I do 'sudo mount /dev/sda /tmp' it mounts ok though.
What's going on and how to fix?

note:
under Edgy the problem is different: it automounts (although I haven't tried with a different size than 2GB), but IO errors occurs while transferring then the device gets disconnected.


Thanks guys

---

