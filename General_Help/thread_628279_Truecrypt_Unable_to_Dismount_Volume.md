---
title: "Truecrypt Unable to Dismount Volume"
date: 2007-12-01
forum: General Help
---

### Post by mahousaru on 2007-12-01
If you get the following error when trying to dismount a TC volume:

```

device-mapper: remove ioctl failed: Device or resource busy
Command failed
Cannot dismount /dev/mapper/truecrypt0

```

Lets say that  the volume is mounted in /mnt then before running truecrypt -d /dev/mapper/truecrypt0 do the following instead:

```

sudo umount /mnt
truecrypt -d /dev/mapper/truecrypt0

```

---

### Post by adpads on 2008-02-19
And if umount still says "device is busy"?

---

