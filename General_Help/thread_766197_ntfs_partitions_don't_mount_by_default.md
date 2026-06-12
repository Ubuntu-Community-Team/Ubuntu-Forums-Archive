---
title: "ntfs partitions don't mount by default"
date: 2008-04-25
forum: General Help
---

### Post by adityakavoor on 2008-04-25
Its so irritating in hardy. NTFS files do not mount by default.

Only once the partitioned is manually opened by the user, the partitions 

get mounted. Soft links of directories in ntfs partitions cannot be 

accessed on startup.

Please help.:(

---

### Post by TeoBigusGeekus on 2008-04-25
You can modify your /etc/fstab file so that the drive gets mounted on startup.
[http://ubuntuforums.org/showthread.php?t=762027]("http://ubuntuforums.org/showthread.php?t=762027")

---

### Post by Alienist on 2008-04-25
If you installed Hardy using Wubi your Windows stuff is located in a folder called *host*. Just go to Filesystem and it's one of the main folders. You can then make a link to the folder on your desktop by doing a sudo nautilus, right clicking the host folder and select make link.
At least that's what I did. From what I understand the Windows partition isn't mounted because you're already in it if you went the Wubi route. It's apparently not very well publicized though.

---

### Post by adityakavoor on 2008-04-25
> **TeoBigusGeekus said:**
> You can modify your /etc/fstab file so that the drive gets mounted on startup.
[http://ubuntuforums.org/showthread.php?t=762027]("http://ubuntuforums.org/showthread.php?t=762027")

its not about editing these files and getting this done.

When it was perfect in previous releases, why does an LTS have this flaw ?

---

### Post by adityakavoor on 2008-04-25
> **Alienist said:**
> If you installed Hardy using Wubi your Windows stuff is located in a folder called *host*. Just go to Filesystem and it's one of the main folders. You can then make a link to the folder on your desktop by doing a sudo nautilus, right clicking the host folder and select make link.
At least that's what I did. From what I understand the Windows partition isn't mounted because you're already in it if you went the Wubi route. It's apparently not very well publicized though.

I did'nt use wubi. It was a fresh install

---

### Post by dgel on 2008-04-25
I have the same problem, with both ntfs and fat32 disks. They are all simply other partitions of the same drive and it's a normal install.
Its very annoying that they don't get mounted immediately, especially since the icons for mounted drives appear on different places on the desktop every time.
An easy fix ould be appreciated.

---

### Post by compacho on 2008-04-25
Ok, I got my partitions to auto-mount at boot using this guide:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

Problem is, I am unable to  edit anything in my partitions. They are just READ ONLY. I try to adjust the permissions, but ubuntu wouldn't allow me. Any ideas?

---

