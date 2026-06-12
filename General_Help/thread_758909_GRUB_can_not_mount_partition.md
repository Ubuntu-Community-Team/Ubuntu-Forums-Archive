---
title: "GRUB can not mount partition"
date: 2008-04-18
forum: General Help
---

### Post by penguin5 on 2008-04-18
I just got my GRUB menu back and now when I select ubuntu it shows me Grub error 17, can not mount partition. It shows me that if I select vista too but only for a second and then lets me in. Not for ubuntu though.

How do I fix it? 

Thanks

---

### Post by penguin5 on 2008-04-18
does it have to do with grub not finding the partition? I just reinstalled grub and now its giving me the option of selection between vista and ubuntu and ubuntu refuses to load.

---

### Post by zvacet on 2008-04-18
```
sudo fdisk -lu
```

```
cat /boot/grub/menu.lst
```

Post both here.

---

