---
title: "Grub  17 Error"
date: 2007-03-21
forum: General Help
---

### Post by dustin0 on 2007-03-21
FIrst I have looked on the forums and tried stuff but it didnt work.  So this is what happened. On boot up ubuntu did a disk check. Then   when it  restarted   i got error 17.
This is what   fdisk -l prints out

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         676     5429938+  82  Linux swap
/dev/hda2             677        1339     5325547+  82  Linux swap
/dev/hda3            1340       19452   145492672+  83  Linux

hda1 is   /boot
hda2 is /swap  
hda3 is /

I tried to mount   hda3  to get my stuff off of it but it says 

mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab

So  help please 

 - D ustin

---

