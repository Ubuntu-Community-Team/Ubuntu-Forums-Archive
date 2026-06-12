---
title: "Folder permissions keep reseting"
date: 2013-10-16
forum: General Help
---

### Post by Marek_Luk on 2013-10-16
I have problem.I'm trying to share second hdd formated to NTFS via samba.I installed system-config-samba and correctly set settings through it(it works on other lubuntu computer).Problem comes when I want to change permissions on second HDD to read/write/view to "anyone".I change them, hit OK and when I open this window again it's reseted again to "only owner".My account is administrator.

---

### Post by sudodus on 2013-10-16
Welcome to the Ubuntu Forums :-)

Linux cannot set permissions individually for files in Windows filesystems (NTFS and FAT). Instead the permissions are set when the partition is mounted, and that can be controlled in the mount command or in /etc/fstab. See ```
man mount
``` and ```
man fstab
```

---

### Post by Habitual on 2013-10-16
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Marek_Luk on 2013-10-18
Thank you for your answer.After looking at tutorial how to do it I just reformated that hdd with ext4 and it works like charm. :D

---

### Post by Habitual on 2013-10-18
I did exactly that on a USB drive after "finding" the correct fstab permissions.
Makes it soooo much easier.

---

