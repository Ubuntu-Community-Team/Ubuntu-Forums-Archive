---
title: "Harddisk Permissions"
date: 2006-08-23
forum: General Help
---

### Post by zapho on 2006-08-23
I managed to install Dapper onto an external usb drive and everything works grand, cept it won't let me access my main harddrive, which is NTFS and holds my windows partition. I can only access it as root, but if I try to change the permissions it says "Cannot change permissions as disk is read only". Is there someway around this so any user can read it? I don't need to write to it using ntfs-3g.

---

### Post by mlind on 2006-08-24
Look in your /etc/fstab file. Does it contain a line that mounts you NTFS drive? You need to speficy umask attribute to allow access permissions to regular users.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by zapho on 2006-08-24
Yeah there's an entry for it in fstab, but what is the umask option?

---

### Post by Ramses de Norre on 2006-08-24
It sets the permissions, you'll like umask=0222 for ntfs, which is r-x for everyone. (writing is unsupported)

---

### Post by zapho on 2006-08-24
Thanks mate, I'm going to test this now.

---

### Post by zapho on 2006-08-24
Arg! Now I've lost permissions to both drives! 

I can only access both drives as root now (I have an ntfs partition on the Usb drive also). It says that the owner of both is unknown and perivalges suggest that I should be at least able to read it, but no luck!

---

### Post by Ramses de Norre on 2006-08-24
You must have missed something.. Can you post your fstab file and tell us which partitions are having the issue?

---

### Post by zapho on 2006-08-24
You're right, I had a typo in it : "unmask" instead of "umask". Its finally working. Thanks for all the help ;)

---

