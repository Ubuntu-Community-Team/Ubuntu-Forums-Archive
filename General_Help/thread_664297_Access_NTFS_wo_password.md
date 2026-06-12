---
title: "Access NTFS w/o password?"
date: 2008-01-11
forum: General Help
---

### Post by renochew on 2008-01-11
HI all, is there way to alter the behavior that you need to enter password when accessing a windows partition everytime you boot up ubuntu? I use fedora for a while and it seems that it don't have such requirement.

Thanks in advanced!

---

### Post by PeterJS on 2008-01-11
Are you sure that it's the ntfs partiton? Outside of windows ntfs has no way of enforcing it's premissions. Further more I was under the impression that the ntfs-3g doesn't even try to use the ntfs file permissions.

Is it an encrypted file system?

---

### Post by renochew on 2008-01-11
Hi, thanks for the reply, you mean it shouldn't be prompted for password? Anyway, I am sure the drives are not encrypted and are NTFS, they are just ordinary windows partition. They are mounted right out of the box when I installed ubuntu and I didn't change anything.

Thanks!

---

### Post by PeterJS on 2008-01-11
What does the password prompt say? And what password does it want? Things that are running during the boot up process should be running as root alread and shouldn't need to have their privliages elevated.

---

