---
title: "Converting root dir from ext2 to ext3"
date: 2007-03-20
forum: General Help
---

### Post by NTITech on 2007-03-20
I wish to convert my root directory from ext2 to ext3.  I have read the instructions at [http://www.troubleshooters.com/linux/ext2toext3.htm#_two2three](http://www.troubleshooters.com/linux/ext2toext3.htm#_two2three) but I have a little problem.  It says to run the command ```
mkinitrd initrd-2.4.18-26.8.0.img 2.4.18-26.8.0
``` inside the /boot directory.  But, the command 'mkinitrd' is not on my system.  And my file is named 'initrd.img-2.6.17-11-386'  What should I do?  Do I use 'mkinitramfs'?  And, if so how do I?

---

### Post by mcduck on 2007-03-20
Just boot from the live CD, run tune2fs -j /dev/hd?? (use the correct device/partition), then mount the disk and edit /etc/fstab to mount it as ext3 instead of ext2. Forget about everything else in those instructions. :)

---

### Post by NTITech on 2007-03-20
You sure that I dont need to run 'mkinitrd'?

---

### Post by mcduck on 2007-03-21
No :D

Anyway, it you want to be sure, the mkinitrd tool is in 'initrd-tools'-package..

---

