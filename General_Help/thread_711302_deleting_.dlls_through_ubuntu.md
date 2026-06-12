---
title: "deleting .dlls through ubuntu?"
date: 2008-02-29
forum: General Help
---

### Post by Kinslayer|*= on 2008-02-29
Hi there,
I downloaded some bad files and now I want to get rid or this spyware .dll in my windows/system32 folder. Now is there anyway I can delete this .dll through ubuntu also if anyone knows anything about the  virus called Win re animator and how to remove it plz let me know 



thx

---

### Post by taurus on 2008-02-29
If you want to delete files on your windows, ntfs filesystem, you need to mount it with ntfs-3g first.  _Assuming_ your windows partition is /dev/sda1, open a terminal and run

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

---

