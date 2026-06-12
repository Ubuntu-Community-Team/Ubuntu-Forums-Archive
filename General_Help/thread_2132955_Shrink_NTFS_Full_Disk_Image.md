---
title: "Shrink NTFS Full Disk Image"
date: 2013-04-06
forum: General Help
---

### Post by TTGRULES on 2013-04-06
So I am trying to migrate several Windows virtual machines from Vmware to Xen running on Ubuntu 12.04. I have everything in xen working perfectly and have also converted the Vmware images to .img files. Unfortunately, whoever set up these servers originally gave them 400gb dynamically sized disks, so when I convert them, I end up with 400gb .img files. I've been pulling my hair out trying to shrink them, but I keep coming up short. When I try to use ntfsresize I get the error : 

```
ERROR(2): Failed to check '/absolute/disk/path' mount state: No such file or directory
Probably /etc/mtab is missing. its too risky to continue. you might try another Linux distro

```

I have tried attaching it to loop using losetup but it gives the same error. Any ideas?

---

