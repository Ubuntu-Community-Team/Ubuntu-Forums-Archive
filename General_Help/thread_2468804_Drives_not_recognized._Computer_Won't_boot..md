---
title: "Drives not recognized. Computer Won't boot."
date: 2021-11-10
forum: General Help
---

### Post by rsteinmetz70112 on 2021-11-10
Today one of my computers went down and won't boot. It starts to boot but drops into busybox. The main problem seems to be that the hard drives are not recognized. There are 4 internal SATA drives plus 1 USB drive.  The Motherboard it seems to recognize all of the hard drives. there are no black devices for the hard drives in /dev. The USB drive is fine and available in Busybox but doesn't contain any of the OS. 

The really odd thing is that if I boot a live system to recognizes all of the drives and the mdadm and lvm arrays can be assembled and mounted.  The hardware seems to be fine. I'm not sure where the boot process is breaking down.

---

### Post by rsteinmetz70112 on 2021-11-10
OK I've discovered if I go to the GRUB menu and boot into an older kernel it boots correctly.
I have also updated initramfs and grub, that had not effect.

---

