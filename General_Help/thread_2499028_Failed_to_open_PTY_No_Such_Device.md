---
title: "Failed to open PTY: No Such Device"
date: 2024-07-08
forum: General Help
---

### Post by rolfbruge on 2024-07-08
After using chroot....

sudo mount /dev/sda2 /media/mount2 
sudo mount --rbind /dev /media/mount2/dev 
sudo mount --bind /proc /media/mount2/proc
sudo mount --bind /sys /media/mount2/sys ;
sudo mount --bind /run /media/mount2/run
sudo chroot /media/mount2

and after unmounting the target volume subsequent launching of terminal fails with the following message:

Failed to open PTY: No Such Device

Is there a way to recreate PTY device from terminal, or is the only recourse to reboot?

---

### Post by currentshaft on 2024-07-10
Use mknod to create the PTY

---

