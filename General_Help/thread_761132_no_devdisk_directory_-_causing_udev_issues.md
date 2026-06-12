---
title: "no dev/disk directory - causing udev issues"
date: 2008-04-20
forum: General Help
---

### Post by dmrlook on 2008-04-20
Hey all - I do not have a /dev/disk directory, and I believe this is the root if all of my problems (sound not working properly, can not mount USB drives or my camera, etc.  How do I get the /dev/disk directory and all subdirectories under that populated?  Can I just "sudo mkdir disk"  Of course, yes I can, but I don't believe it is that easy.  I imaging I need to set the permissions just right, and I don't know what those are.  How do I get this back so udev works?

Thanks,
Rob

---

### Post by -Zeus- on 2008-04-21
Here's what I have I dunno if it'll help

```
/dev:$ ll
drwxr-xr-x  6 root   root         120 2008-04-20 11:55 disk
/dev:$ ll disk
drwxr-xr-x 2 root root 200 2008-04-20 17:14 by-id
drwxr-xr-x 2 root root  60 2008-04-20 17:14 by-label
drwxr-xr-x 2 root root 140 2008-04-20 17:14 by-path
drwxr-xr-x 2 root root 100 2008-04-20 17:14 by-uuid
```

---

### Post by dmrlook on 2008-04-21
Thanks - I will try creating those directories with the same permissions and see what happens.  Hopefully some process somewhere will fill in the holes.

---

### Post by dmrlook on 2008-04-22
Well, I was able to create the directories with no issues, but they were deleted the next time I rebooted.  So obviously UDEV is doing something to rebuild those directories every time, and then something is deleting them.  Does anyone know enough about UDEV to explain what might be going on here.

Thanks!

---

