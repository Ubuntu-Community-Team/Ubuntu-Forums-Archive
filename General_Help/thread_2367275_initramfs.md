---
title: "initramfs"
date: 2017-07-28
forum: General Help
---

### Post by saraha2 on 2017-07-28
/dev/sdal1 file system errors....
What do I need to do?

---

### Post by A3M0N on 2017-07-28
You'll need to run: 
```
fsck /dev/sda1 
```

Hit "f", for every question.

When it's done enter
```
reboot 
```

That should get you back up and running.

---

