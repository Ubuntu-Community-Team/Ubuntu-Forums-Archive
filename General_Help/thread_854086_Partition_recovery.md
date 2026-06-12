---
title: "Partition recovery"
date: 2008-07-09
forum: General Help
---

### Post by Delts on 2008-07-09
One of the other users of the laptop had been trying to put Arch on a usb stick and instead put it on the hard drive wiping the partitions.  Is there any way to reverse the damage?  There had been some non-backed up photos and things on it.

Installed was 8.04 and I have a 7.04 Live CD so I can get on the laptop.  I also have an external HDD that can be used for backing up if possible.

Thanks

---

### Post by VMC on 2008-07-09
> **Delts said:**
> One of the other users of the laptop had been trying to put Arch on a usb stick and instead put it on the hard drive wiping the partitions.  Is there any way to reverse the damage?  There had been some non-backed up photos and things on it.

Installed was 8.04 and I have a 7.04 Live CD so I can get on the laptop.  I also have an external HDD that can be used for backing up if possible.

Thanks

Not sure what he did. Was it that Arch actually wrote over an existing partition or just took control. Windows has a program called Recover My Files that can search for erased files. You could use that to search for your photos extensions. There's many programs that will do that.

If your unsure what Arch did then output drive info, from a Terminal:

```
sudo fdisk -l
```

---

