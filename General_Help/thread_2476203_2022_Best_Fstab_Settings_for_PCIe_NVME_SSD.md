---
title: "2022 Best Fstab Settings for PCIe NVME SSD?"
date: 2022-06-19
forum: General Help
---

### Post by johntdavis on 2022-06-19
Hello,

I'm curious what the best practice is for auto-mounting partitions on NVME SSDs using fstab. I've not had to deal with this before, and a lot of the tutorials Google most readily surfaces are old enough that I'm not sure they're still good. (For instance, I found a tutorial mentioning that I should add "ssd," but a slightly newer one said that was not needed for modern drives. Whatever was modern in 2018.)

I've already enabled fstrim.timer, so I'm doing discard operations once a week.

Here's what I've got now:

```
# Docker File System
UUID=ca7c3890-66a7-4eae-a23f-e635a6dc47bd  /mnt/nvme/dockerfs  ext4    defaults,noatime,nodiratime,errors=remount-ro        0       0


# User Home Directories
UUID=9c7f54e1-da64-4946-87d2-96ca5120300a  /mnt/nvme/home      ext4    defaults,noatime,nodiratime,errors=remount-ro        0       0

```

Any suggestions would be appreciated. Thanks!

---

### Post by TheFu on 2022-06-19
I wouldn't permanently mount under /mnt/.  The standard says that location is for temporary administrative needs.
The *Linux File System Hierarchy Standards* spells out which directories are for what purposes.

I don't know enough about NVMe SSDs and the OS you are running to make other suggestions.
For my home, which is on NVMe on 1 system, I use these settings:
```
LABEL=home                         /export/home ext4 noatime,nodev,nosuid 0 1
```
I'm mounting using a label, not a UUID.
The HOME gets shared over NFS with other systems, so I won't use /home as the mount.  /home is for local users, not NFS.  Most people (99%) wouldn't do this.

---

### Post by oldfred on 2022-06-20
I have this in my notes from quite a while ago.

There&#8217;s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

Arch often has good information:
[https://wiki.archlinux.org/title/Solid_state_drive/NVMe](https://wiki.archlinux.org/title/Solid_state_drive/NVMe)

Most systems now have a weekly trim automatically implemented.
systemctl list-timers |grep fstrim

To update firmware on my Samsung I had to go to their web site & download an ISO that was just for my model NVMe drive.

---

