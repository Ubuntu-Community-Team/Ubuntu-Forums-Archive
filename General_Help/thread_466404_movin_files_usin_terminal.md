---
title: "movin files usin terminal"
date: 2007-06-06
forum: General Help
---

### Post by Irti on 2007-06-06
how can i move files usin the terminal......coz wen i try to move sum files on my d drive.....it says tht i dont hav the permissions......

---

### Post by meng on 2007-06-06
If you don't have permissions at user level, try the command with superuser privileges, i.e.:
sudo mv (files) (destination)

---

### Post by taurus on 2007-06-06
What filesystem is your d drive?  If it's ntfs, then you need to install ntfs-3g first before you can write to it, even if you are root.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

