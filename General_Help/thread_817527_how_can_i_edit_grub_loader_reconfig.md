---
title: "how can i edit grub loader reconfig"
date: 2008-06-03
forum: General Help
---

### Post by jason15417 on 2008-06-03
i wont it to stop listing the origanal .16 kernal it now shows .16 version and new .17 update i also want xp as my default load or atleast more then 7 secs to choose

---

### Post by hal8000 on 2008-06-03
You need to post the output of:

fdisk -l


and also

cat /boot/grub/menu.lst

---

### Post by EXCiD3 on 2008-06-03
Just open terminal, then run this to open your grub configuration:

```
sudo gedit /boot/grub/menu.lst
```

From there just read the comments and you will find the entries at the very bottom of the file. You can easily find which line says which entry is the default and also remove the text for the 16 kernel.

---

