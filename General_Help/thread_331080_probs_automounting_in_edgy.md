---
title: "probs automounting in edgy?"
date: 2007-01-04
forum: General Help
---

### Post by broughcut on 2007-01-04
# /dev/hdaNth /a/mnt/point ext3 defaults 0 0

doesn't appear to work (well, it categorically does not work in my installation) in an fstab were other devices have UUIDs specified (I haven't checked the situation when fstab has no devices with UUIDs specified, it may be an either/or thing).... 

If your clean Edgy installation is anything like mine, you must provide a device id in fstab for it to automount the device at startup or via *mount -a* .

> 
vol_id -u /dev/hdaNth

# /dev/hdaNth UUID=d76adfae-35ee-4e9d-ba5a-076ec986ee0c /a/mnt/point ext defaults 0 0

I had no probs manually mounting, but it was not possible to get devices without UUIDs to mount automatically.


Edit:

this was very silly of me.... of course I took care to blindly copy the fstab format, not realising the device names are commented out when there's a UUID. :roll: :-# 

# /dev/hdaNth 
UUID=d76adfae-35ee-4e9d-ba5a-076ec986ee0c  /a/mnt/point ext3 defaults 0 0

I was literally adding "# /dev/hda..."

---

