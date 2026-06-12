---
title: "moving /boot to new partition"
date: 2015-05-20
forum: General Help
---

### Post by Fire Raven on 2015-05-20
I want to move the /boot directory on the / partition to a dedicated /boot partition. I am comfortable with using the gparted live CD. I just need to know how to keep the system bootable.

---

### Post by yancek on 2015-05-20
You need to then reinstall grub so that it is pointing to the boot directory.  It is explained at the link below under the section "via the Live CD terminal".  

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by ajgreeny on 2015-05-21
Is there a good reason for wanting a separate /boot partition as it can cause you more problems than keeping it in root, in particular running out of space if /boot is not large enough.

There have been many threads just recently about this problem where users have chosen at installation time to use encryption or LVM.  In that case a /boot partition must be used and is made by the installer automatically; otherwise a separate /boot is unnecessary and potentially a problem in waiting.

---

### Post by Fire Raven on 2015-05-21
> **ajgreeny said:**
> Is there a good reason for wanting a separate /boot partition as it can cause you more problems than keeping it in root, in particular running out of space if /boot is not large enough.

There have been many threads just recently about this problem where users have chosen at installation time to use encryption or LVM.  In that case a /boot partition must be used and is made by the installer automatically; otherwise a separate /boot is unnecessary and potentially a problem in waiting.

I am unencrypted but want to switch to encryption. I already saw this  makes /boot necessary so I wanted to get through that step first.

One thing I still have to wonder, though. If /boot is unencrypted and an  attacker gains physical access, would it not be easy to install a  kernel that would record your passphrase?

---

### Post by ajgreeny on 2015-05-22
Not sure about the feasibility of your final query about the passphrase, but as a general rule, someone who really knows what he or she is doing will have free rein if they can get physical access to any machine that is unencrypted.

I am not sure either how you move /boot post installation from the root partition to a separate /boot partition, but it will include copying everything from the /boot folder to the /boot partition and then editing /etc/fstab to make the system aware of that.  There may well, however, be other actions needed and edits of other boot files, but I'm afraid that is beyond me.

---

