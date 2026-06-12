---
title: "Help Mounting External Drive on LiveCD version"
date: 2013-08-14
forum: General Help
---

### Post by fjcostanzo on 2013-08-14
I'm trying to help a friend recover files from windows partition that won't start. I'm running from the ubuntu live cd and I was able to get the windows partition mounted successfully. However, I'm trying to mount her external harddrive but I keep getting: 

"Error creating mount point `/media/ubuntu/FreeAgent GoFlex Drive': Read-only file system"

The external harddrive is a Seagate Freeagent Goflex

any help would be very much appreciated.

---

### Post by TheFu on 2013-08-14
google "ubuntu boot repair" and follow those instructions.  That will probably fix the boot issue if there isn't any bad hardware or file corruption ... or UEFI or encryption.
I don't see any issue mounting a file system as read-only. Is that a problem?  If the file system is a Linux, then run **fsck** against it.  If it is Window-whatever (NTFS, fat32, or xfat), use the Windows tools.

google "ubuntu boot info" and follow those instructions to provide relevant data about the connected HDDs and partitions.

---

### Post by oldfred on 2013-08-14
It is not a hard drive that you directly mount but a NAS, that you network into.

[http://www.rangify.com/solved-how-to-mount-seagate-freeagent-goflex-home-nas-drive-to-linuxubuntu-permanently/](http://www.rangify.com/solved-how-to-mount-seagate-freeagent-goflex-home-nas-drive-to-linuxubuntu-permanently/)

---

