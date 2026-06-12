---
title: "Special mount command for USB devices?"
date: 2008-06-17
forum: General Help
---

### Post by tonyr1988 on 2008-06-17
I have 2 USB external HDDs that I have permanently connected to my desktop. There are two entries (with paths like /dev/sda1 and /dev/sda2) in my /etc/fstab file, which usually works without a charm. However, if I switch where they are plugged in, it gets it backwards. If I plug them into another USB port, sometimes it goes crazy.

I think I remember reading sometime back about a special "mount" command for USB devices. It involved using some identifier (vendor and product ID, maybe?) special to each USB device, so that it would truly mount the device, not just the port.

Any information would be awesome.

---

### Post by ryanhaigh on 2008-06-17
What you want is the UUID which is unique to each partition. To find the UUID of the partion use 
```

vol_id -u /dev/sda1

```
Where sda1 is the partition you want to mount.

You could then use the information [here]("https://help.ubuntu.com/community/InstallingANewHardDrive#head-fff5ec7d7c523059a4518c5db5bb68075cb46a43")

But instead of using "/dev/hdd1" use a line like:
```

UUID=f0f68b8c-cf26-4c76-8a21-6a5c02c028dd /media/example ext3 defaults,errors=remount-ro 0 1

```

note: the options here are just an example, you will need to know what to put in for your partions as well as creating the mountpoint.

---

### Post by tonyr1988 on 2008-06-19
> **ryanhaigh said:**
> What you want is the UUID which is unique to each partition. To find the UUID of the partion use 
```

vol_id -u /dev/sda1

```
Where sda1 is the partition you want to mount.

You could then use the information [here]("https://help.ubuntu.com/community/InstallingANewHardDrive#head-fff5ec7d7c523059a4518c5db5bb68075cb46a43")

But instead of using "/dev/hdd1" use a line like:
```

UUID=f0f68b8c-cf26-4c76-8a21-6a5c02c028dd /media/example ext3 defaults,errors=remount-ro 0 1

```

note: the options here are just an example, you will need to know what to put in for your partions as well as creating the mountpoint.

That's exactly what I needed. Ironically, I was going to say "I want something similar to the UUID, just for USB devices" in my original post, but apparently I didn't want something *similar* to UUIDs, I wanted UUIDs themselves. :)

Thanks a ton, especially for the information on finding the UUID.

---

