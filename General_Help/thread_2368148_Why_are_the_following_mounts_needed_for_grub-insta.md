---
title: "Why are the following mounts needed for grub-install ?"
date: 2017-08-07
forum: General Help
---

### Post by sreyan32 on 2017-08-07
Can someone please tell me why in a chrooted environment the following mounts are required before actually running grub-install or update-grub ?

```
$ mount -t proc none /mnt/ubuntu/proc
$ mount -o bind /dev /mnt/ubuntu/dev
$ mount -o bind /sys /mnt/ubuntu/sys

```

I understand that grub needs information about the OS before it can generation the configuration files but my question is the above mounts usually belong to the live system from which we are chrooting into. So shouldn't that information be different from the actual be different from that of the OS for which we are installing grub ?

---

### Post by VMC on 2017-08-07
For  grub-install you don't need those. Here's what I have used for years without errors:
```
sudo grub-install --recheck --root-directory=/ /dev/sda
```

edit: It also depends on where your installing grub from. I'm installing grub from the distro-partition that I want installed.
example:
sudo mount /dev/sda7 /mnt <<change '7' to the partition you want grub installed
sudo grub-install --root-directory=/mnt /dev/sda
reboot, then:
sudo update-grub

---

### Post by sreyan32 on 2017-08-08
And if I am installing grub from a non-distro partition ? then would I need the mounts ?

---

