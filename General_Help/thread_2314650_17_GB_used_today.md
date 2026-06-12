---
title: "17 GB used today"
date: 2016-02-22
forum: General Help
---

### Post by cmcanulty on 2016-02-22
Suddenly gparted shows 17GB more used in /home than yesterday yet I didn't download anything large is there a way to pin down where this went? in thunar it lists size of most directories as a few kb, like documents is listed as 41 KB but on properties it is actually over 215GB so sorting by size doesn't help

---

### Post by v3.xx on 2016-02-22
Try this

[https://help.ubuntu.com/community/RecoverLostDiskSpace#Unexpectedly_Large_File](https://help.ubuntu.com/community/RecoverLostDiskSpace#Unexpectedly_Large_File)

---

### Post by cmcanulty on 2016-02-23
thanks that worked I found it was a virtual box snapshot that took nearly 20GB so I deleted the snapshot

---

### Post by v3.xx on 2016-02-23
Easy fix :)

I hope when you said removed that you used vBox to remove it.  Or your guest machine may not properly boot a snapshot.

---

### Post by grahammechanical on 2016-02-23
I experimented with BTFS (file system) and snapshots of the OS. I have no idea if the method is the same as that used for a virtual box snapshot. I found that certain utilities would show a size of the snapshot of the OS that was equal to the total file size of the OS but in actual fact the snapshot only contained the code differences and so the snapshot file was not as large as it seemed to be when using certain utilities.

Regards.

---

### Post by cmcanulty on 2016-02-23
yes I deleted it from VB. Snapshot is not worth it to me for 17GB. VB boots OK thanks

---

