---
title: "lvm not found, UUID does not exist"
date: 2022-12-23
forum: General Help
---

### Post by alejross12 on 2022-12-23
When restarting my computer today I was booted into the built-in shell with the error message:
/scripts/local-top/lvm-workaround: line 22: lvm: not found
Gave up waiting for suspend/resume device
Gave up waiting for root file system device. Common Problems:
- Boot args (cat /proc/cmdline)
     - Check rootdelay = (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=ebc... does not exist. Dropping to a shell!

I shortened the UUID because it is really long to write out.
Preceding this error message is a bunch of messages about "Invalid name" and "Invalid name_offset:2157422".
I was able to create an Ubuntu live-USB and access my hard drive through it, recovering some of my files manually. I also see that the hard drive containing everything is listed in GParted with the same UUID the above error claims to not exist. I ran boot-repair and got the following paste bin: [https://paste.ubuntu.com/p/XGDYvZZnYq/](https://paste.ubuntu.com/p/XGDYvZZnYq/)

I would appreciate any help I can get! Thank you.

---

### Post by VMC on 2022-12-24
I don't know lvm, but here's a similar situation with solution:
[https://askubuntu.com/questions/551446/cant-find-lvm-root-dropped-back-to-initramfs](https://askubuntu.com/questions/551446/cant-find-lvm-root-dropped-back-to-initramfs)

Your ext4 does exists with UUID = ebc6d7c0-8bb7-46b0-a71e-fac405cc0a61

---

### Post by alejross12 on 2022-12-24
I've tried, but nothing works in that thread because, doing everything in (initramfs) gives me:
- /etc/initramfs-tools does not exist
- vgchange command not found
- ls /dev/mapper only shows 'control' folder
- /boot does not exist
- cat /proc/partitions gives me "major minor #blocks name"
- blkid doesn't give me anything

---

### Post by alejross12 on 2022-12-24
Found a solution! Followed the steps at [https://support.system76.com/articles/bootloader/](https://support.system76.com/articles/bootloader/). Apparently it was an issue with the systemd-boot; I followed the steps on how to reinstall it from live-USB for EFI boot.

---

### Post by VMC on 2022-12-24
mark thread solved.

---

