---
title: "GRUB repair"
date: 2015-02-08
forum: General Help
---

### Post by cl-netbox on 2015-02-08
Having read about problems to restore GRUB I tried different methods.
Now I want to share the easiest and most secure way that realy works:

Boot from ubuntu install media.
Execute commands in terminal:

Solution for GPT partition table | EFI mode
(X=disk | Y=root partition | Z=EFI partition)

sudo mount /dev/sdXY /mnt
sudo mount /dev/sdXZ /mnt/boot/efi
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install /dev/sdX
update-grub

Solution for MSDOS partition table | MBR mode
(X=disk | Y=root partition)

sudo mount /dev/sdXY /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX

---

