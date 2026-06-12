---
title: "checks disk every 30 boots?"
date: 2007-07-28
forum: General Help
---

### Post by steve3226 on 2007-07-28
Feisty checks the disk file system every 30 boot ups. How can I change this to every 100?

Steve steve.rosen_gmail.com (substitute @ for _)

---

### Post by confused57 on 2007-07-28
This works for me:
```
sudo tune2fs -c 50 /dev/hda1
```

---

### Post by zach12 on 2007-07-28
would that work on dapper

---

### Post by jongkind on 2007-07-28
> **zach12 said:**
> would that work on dapper

Yes. Note that you need to adjust the number of reboots (50 in case of confused57) and path to your drive (/dev/hda1 in case of confused57) to what is suitable for you.

---

### Post by por100pre1 on 2007-07-28
Another solution is schedule fsck when you actually tell so:

```
sudo touch /forcefsck && sudo reboot
```

---

