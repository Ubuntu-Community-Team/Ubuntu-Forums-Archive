---
title: "windows ntfs partition mounted, but access denied: please help"
date: 2006-12-27
forum: General Help
---

### Post by fredxor on 2006-12-27
I used Disks Manager to mount a Windows NTFS partition in Ubuntu 6.06 LTS. It's mounted to /pie. It's mounted fine, but it tells me that I lack the necessarry permissions when I try to browse it. Please help!

---

### Post by taurus on 2006-12-27
Try browsing it as root!!!

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by fredxor on 2006-12-27
It says: "Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

---

### Post by taurus on 2006-12-27
Applications -> Accessories -> Terminal
```
sudo ls -la /pie
```

---

### Post by fredxor on 2006-12-27
it lists the files in the root directory of the drive, but i still can't browse the drive (same error as before)

i'd like to be able to delete and create files and folders on the drive

---

### Post by taurus on 2006-12-27
I bet you mounted it as only root can browse it!  And if you want to write, delete, or modify your Windows partition, ntfs, then you need to install ntfs-3g and use it to mount your Windows then...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by fredxor on 2006-12-27
thanks a ton guys. I really appreciate your help. i hope it works

---

