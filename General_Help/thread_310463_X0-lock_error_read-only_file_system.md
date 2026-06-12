---
title: "X0-lock error: read-only file system"
date: 2006-12-01
forum: General Help
---

### Post by Prospero2006 on 2006-12-01
Symptoms:
  -My X windows won't come up.
  -The error it indicates is that the filesystem
   is set to read-only and it can't set the .Xauthority,
   X0-Lock etc....

  **When I boot to recovery mode, I can't edit or change file permissions
   on anything because it claims the entire filesystem is set to   
   read-only**??? (Yes, I'm root)
  -When I boot a live CD, I can erase the lock files, but Ubuntu still
   mounts the whole filesystem as Read-only afterward, thus I get the 
   errors  hat the lock files can't be set.

  -Any thoughts? Can I provide any information that will help you help me?
           -Thanks,
             Pros

---

### Post by taurus on 2006-12-01
Boot into recovery mode and paste the output of this command here!

```
cat /etc/fstab
```

---

### Post by Prospero2006 on 2006-12-01
Brilliant!

I copied fstab from another machine to quickly set up samba shares. 
I didn't think for a second about the root partition.

I had to rewrite the thing manually, but it works great now.

Right on!

Thanks,

Pros

---

