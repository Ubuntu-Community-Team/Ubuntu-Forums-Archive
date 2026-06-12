---
title: "Partitions gone?"
date: 2006-07-09
forum: General Help
---

### Post by Shampyon on 2006-07-09
Everything looked fine last time I logged in. I'd just installed VMWare Server according to the howto on these forums, I'd been tinkering with XP to get the sound working so I could use it to play DRM'd video.

When I start 'er up a few minutes ago, two of my partitions have failed to mount. I have partitions sda1 (Windows), which mounted. sda7 and 8 are my swap and Ubuntu partitions.

sda5 and 6 won't show up.

I've gone into /media/sda5 and /media/sda6, and it claims the folders are both empty. sda5 is a 37GB partition with about 20GB of data on it at least. Ubuntu claims it's empty, though it says there's on 6GB of free space :confused:

*Edit:* I went to SYSTEM>>ADMINISTRATION>>DISKS. The partitions are still there, still enabled, still browseable, still writeable. I was able to make links to open them. They just aren't showing up as automounted drives like my XP partition is.
Curious... it's probably because I restored an older version of fstab, one that was made while I had this same problem (which inexplicably vanished) a while ago...

---

### Post by OpsVentus on 2006-07-09
Hello Shampyon.

yes it's your fstab. There you specify which partitions should be mounted where and how.
Ubuntu mounts Media(cd-rom/usb-disks) in /media. If you want Ubuntu to ack the same way for sda5/6 then you have to specify the option "user" for the partitions sda5/6.

If you post your fstab here I can tell you what to change.

Cheers,
Bart.

---

### Post by Shampyon on 2006-07-09
They're back. I don't know why.
But hey, they're back!
If it happens again, I'll have to pay close attention to what I was doing just before.

Thanks for the help, though :)

---

