---
title: "NTFS automount on boot"
date: 2008-02-04
forum: General Help
---

### Post by stalefist on 2008-02-04
Hey everyone. Is it possible to have my NTFS partition automatically mounted when I boot into ubuntu? I'm using gusty 7.10. I can read/write once I double click the hard drive in my "Computer" shortcut (it's labeled 122.1GB Volume: disk) but that asks for my password. Basically I want to avoid all this and just have it mounted from boot. Any help is appreciated :D

---

### Post by taurus on 2008-02-04
Yes.  You just need to add an entry in /etc/fstab for it so it will be mounted automatically each time you boot Ubuntu.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

