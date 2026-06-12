---
title: "Identifying destination for LuckyBackup"
date: 2013-02-16
forum: General Help
---

### Post by frenchian on 2013-02-16
I use Lucky Backup each night as an automatic backup for /home. The copy goes to a dedicated partition on an external, USB-connected hard drive.

When I set up the task, I can't define the partition by name, only as "/media/usb2/" or whatever.

The problem is that this address changes - sometimes it's "/media/usb2/", then when I check a few days later, it's become something different - "/media/usb0/" for example. Possibly after a restart?

Is there a way I can define the destination partition by name?

Thanks

---

### Post by Ms. Daisy on 2013-02-16
Yes.  You'll want to auto-mount the usb external drive to a designated spot using "mount."   Then you can tell LuckyBackup to use the designated device because it won't change.

See ```
man mount
``` and [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
and 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by frenchian on 2013-02-16
> **Ms. Daisy said:**
> Yes.  You'll want to auto-mount the usb external drive to a designated spot using "mount."   Then you can tell LuckyBackup to use the designated device because it won't change.

See ```
man mount
``` and [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
and 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Thank you, Ms. Daisy.

I'll go and read up on it.

Cheers

---

