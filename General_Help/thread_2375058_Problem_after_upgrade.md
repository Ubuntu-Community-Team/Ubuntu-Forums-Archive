---
title: "Problem after upgrade"
date: 2017-10-21
forum: General Help
---

### Post by carlos125 on 2017-10-21
Hi, I was installing Ubuntu 17.10 from 17.04 and my computer just shutted down when installing packages. After that I turned on my computer and it doesn't start, just charging before login screen. Can someone help me please?

---

### Post by Xian on 2017-10-21
If your computer shut down while an system upgrade was being performed - you will likely need to use a LiveCD to chroot into the Ubuntu partition and complete the upgrade. Instructions for doing this can be found here: 

[LiveCd Update System]("https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure")

---

### Post by carlos125 on 2017-10-22
> **Xian said:**
> If your computer shut down while an system upgrade was being performed - you will likely need to use a LiveCD to chroot into the Ubuntu partition and complete the upgrade. Instructions for doing this can be found here: 

[LiveCd Update System]("https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure")

Thank you! But I fixed the problem just with the opition of repairing dpkg in recovery mode. Maybe this could be useful for somebody else :):)

---

