---
title: "Moving from NVMe/PCI-E to SATA"
date: 2020-06-01
forum: General Help
---

### Post by dinkidonk on 2020-06-01
Will it cause any problems if I move my current installation of 18.04 from a NVMe drive to a SATA SSD?

---

### Post by dino99 on 2020-06-01
I have no idea what 'move' means for you, but the main diff is that sata is much slower than nvme :confused:

---

### Post by dinkidonk on 2020-06-01
Move means "dd if=/dev/nvme0n1p1 of=/dev/sda" where sda is an SSD of equal size as the NVMe. I would like to preserve a bootable copy of my 18.04 system before I install 20.04 on the NVMe.

---

### Post by dino99 on 2020-06-01
in that case i suppose you will get a new uuid on sata; and so needs to adapt /etc/fstab with the related 'sudo blkid' output to get grub happy

---

### Post by TheFu on 2020-06-01
> **dinkidonk said:**
> Move means "dd if=/dev/nvme0n1p1 of=/dev/sda" where sda is an SSD of equal size as the NVMe. I would like to preserve a bootable copy of my 18.04 system before I install 20.04 on the NVMe.

That will be very slow and cloning a single partition to an entire disk is a mistake.  i'd use ddrescue after booting from a USB flash "try ubuntu" setup.

```
sudo ddrescue /dev/nvme0n1 /dev/sda   /tmp/log
```
You'll need to install gddrescue.

if you have to use dd, add a 4M block size so it isn't so slow.
When you are done, you'll probably need to fix the /etc/fstab on sda[123] as needed.  Use the "try ubuntu" environment for that too, after you've removed the NVMe storage.  Probably want to disable any fstrim calls too.

---

### Post by dinkidonk on 2020-08-22
As a follow up, I did the "dd if=/dev/nvme0n1p1 of=/dev/sda bs=1M" move from NVMe to a SATA SSD and it works without any modifications in any system files, so now I can finally get on with installing 20.04.1 on the NVMe :D

---

