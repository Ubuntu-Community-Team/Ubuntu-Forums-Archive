---
title: "update-grub doesn't see multiple Ubuntu installations on software Raid"
date: 2017-10-11
forum: General Help
---

### Post by fz0001 on 2017-10-11
Apologizing if this is not the most appropriate forum for this question. Please feel free to move it where it might belong.

I have searched for a solution for this issue for quite some time, but couldn't find any. Basically, I have two disks containing multiple software RAID1 partitions. I installed Ubuntu 14.04 on /dev/md0 and /dev/md2 (corresponding to /boot and /, respectively) and Ubuntu 16.04 on /dev/md1 and /dev/md3. When I ran update-grub on either of the two OS', the other one could not be detected. I don't want to create a menuentry for the other OS under grub, because that means every time the kernel is upgraded for the other OS, I will have to manually edit the menuentry. Any suggestion is greatly appreciated.

Thanks,

feng

---

### Post by oldfred on 2017-10-11
I know os-prober works with Desktops, but with some other installs need to have those partitions mounted, so it can see the other installs.
Have you tried manually mounting the other RAID install and then running sudo update-grub?
You will have to have both installs /boot and / partitions mounted.

---

### Post by fz0001 on 2017-10-12
Yes, I did mount / of the other installation to /mnt/test and then /boot to /mnt/test/boot. When I ran os-prober, I got nothing.

---

