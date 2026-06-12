---
title: "Hdd link disappears"
date: 2008-06-21
forum: General Help
---

### Post by hoangvu.che on 2008-06-21
i got 2 issues which seem come from a same problem, please help me.

1. Normally, after ubuntu starts, normally my drive D (called 100gb Media) link is automatically put on desktop.
However, now, it only appears on the desktop after I click it int the Places menu.

2. When I right click on the desktop and try to change the background image, I try to browse my disk which is the drive D above but it doesn't exists in places links. I also tried to browse for it thought File system/media. However, there are only cdrom items overthere.

Please help me to solve. Thanks.

---

### Post by VMC on 2008-06-21
> **hoangvu.che said:**
> i got 2 issues which seem come from a same problem, please help me.

1. Normally, after ubuntu starts, normally my drive D (called 100gb Media) link is automatically put on desktop.
However, now, it only appears on the desktop after I click it int the Places menu.

2. When I right click on the desktop and try to change the background image, I try to browse my disk which is the drive D above but it doesn't exists in places links. I also tried to browse for it thought File system/media. However, there are only cdrom items overthere.

Please help me to solve. Thanks.

Is the D drive a second drive or second partition. Either way, can you output fstab:
From Terminal

```
cat /etc/fstab
```

---

