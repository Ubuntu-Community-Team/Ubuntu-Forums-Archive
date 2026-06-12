---
title: "Can't access WD external HDD"
date: 2008-01-12
forum: General Help
---

### Post by arnabt on 2008-01-12
hi i m very new to ubuntu. I really like the speed and others. I have been having quite a few problems but this forum helped me a lot.

I cannot solve this particular problem however. I have a WD external hdd, which I was able to access and do everything previously. However, suddenly I can't access it anymore. It doesn't appear in the desktop but it does appear in file browser. However, I can't access it. I tried mounting it by rightclick>mount but nother happened.

I would really appreciate if anyone could help me with this.

---

### Post by arnabt on 2008-01-12
ok got it working. if anyone else is facing this problem then try the following

sudo mkdir /media/sdg1
sudo mount -t vfat /dev/sdg1 /media/sdg1

---

### Post by taurus on 2008-01-12
Is it ntfs or vfat?  Can you post the output of this command from a terminal and then will see if you can mount it from a terminal?  Chances are that you didn't unmount it cleanly when you had it connect to a windows system.

```
sudo fdisk -l
```

---

