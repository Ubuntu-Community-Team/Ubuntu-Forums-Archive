---
title: "access to other &quot;device&quot;"
date: 2013-02-25
forum: General Help
---

### Post by alabamatoy on 2013-02-25
Ubuntu and Wxp dual boot machine.  Need a user to be able to access some files on the Windows XP partition.  As admin, I can see and access the partition.  How do I allow a Ubuntu user to also access it?  It doesnt show up on the home folder listing.

Attempts to right click on the device and change the permissions thus far havent worked, as soon as I change something, the interface changes it right back to what it was.

---

### Post by Impavidus on 2013-02-25
You can list the windows partition in your /etc/fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
It's best to set your system partition to read only (although win XP often seems OK), data partitions can be set to read-write. You can pick any mountpoint you like and set the type to ntfs. Set it to automount at boot.

---

