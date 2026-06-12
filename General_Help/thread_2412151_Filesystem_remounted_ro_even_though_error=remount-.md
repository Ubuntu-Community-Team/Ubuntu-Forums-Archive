---
title: "Filesystem remounted ro even though error=remount-ro is not in fstab"
date: 2019-02-08
forum: General Help
---

### Post by dman7773 on 2019-02-08
The other day my ext4 filesystem remounted itself as read only when it got some errors. In fstab I removed error=remount-ro but it still did it. How is this possible since I removed error=remount-ro from fstab?

---

### Post by deadflowr on 2019-02-08
What *does* fstab say?

---

### Post by dmnur on 2019-02-08
From **ext4(5)** (**man 5 ext4**):
```

errors={continue|remount-ro|panic}
              Define the behavior  when  an  error  is  encountered.   (Either
              ignore  errors  and  just mark the filesystem erroneous and con&#8208;
              tinue, or remount the filesystem read-only, or  panic  and  halt
              the  system.)   The default is set in the filesystem superblock,
              and can be changed using tune2fs(8).

```

You can check your default value using this command (replace **/dev/sda1** with your partition device path):
```
sudo tune2fs -l /dev/sda1 | grep Errors
```

---

### Post by dman7773 on 2019-02-08
It shows  [FONT=Ubuntu Mono, monospace][COLOR=#000000]'Errors behavior: Continue'


[/COLOR][/FONT]

---

