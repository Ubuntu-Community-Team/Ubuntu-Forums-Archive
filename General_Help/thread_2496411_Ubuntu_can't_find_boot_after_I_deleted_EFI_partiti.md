---
title: "Ubuntu can't find /boot after I deleted EFI partition (and restored it)"
date: 2024-03-26
forum: General Help
---

### Post by chortle on 2024-03-26
I mistakenly deleted the first partition on a little media box (sda1). The data is still there. It was only the partition table. I quickly downloaded testdisk and restored it. The partition contains /EFI. 

/boot is on the main partition that never got touched. I think I may have deleted the 1.84mb partition at the end of the disk. I'm not sure what is there, probably backup partition data. It shows unallocated.

When I boot again Ubuntu says it can't find /boot. The sda1 partition shows up as "boot" "esp" on gparted. I am using secure boot. I appreciate I will have to enroll my drivers again. 

What am I forgetting that is stopping the machine from booting?

---

### Post by Tadaen_Sylvermane on 2024-03-26
Does the partition restore restore the UUID as well? If your fstab is going by uuid, which it should then boot doesn't exist according to it. You need to update the fstab if this is the case. You will likely need to load a live image and reinstall grub and such in this case as well.

---

### Post by chortle on 2024-03-27
Thanks for your help. On the second boot it worked fine. I don't know why the first time failed. I didn't change anything.

---

