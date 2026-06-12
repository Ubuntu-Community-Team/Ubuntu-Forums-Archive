---
title: "won't mount partitions from other HDD if pen drive is connected during boot"
date: 2013-02-05
forum: General Help
---

### Post by kaustubhg123 on 2013-02-05
Hello,

1st SATA HDD = Ubuntu Linux with all Linux partitions
2nd SATA HDD = Windows with all NTFS partitions

Now If I boot, ubuntu boots normally.
However, if pen drive, or even My android is connected in USB debugging mode, the OS will not mount NTFS partitions during boot and will give error while booting.

Any workarounds?:confused:

---

### Post by The Cog on 2013-02-05
Can you post a copy of your /etc/fstab, and say what the error is?

---

### Post by dargaud on 2013-02-05
Check your BIOS: you probably have the USB boot before the HD boot.

---

