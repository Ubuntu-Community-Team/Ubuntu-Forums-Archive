---
title: "mounting local windows partition"
date: 2007-02-11
forum: General Help
---

### Post by Roman78 on 2007-02-11
I have a local windows installation were i have some files that i want in ubuntu. But when i mount my local drive i cannot access it whit the ubuntu gui, only whit the console.

I use:

 sudo mount /dev/hda1 /mnt


Than i can access the mnt only whit root permissions. Is there a ponsibilitie to logon as root or an other way to access the mnt?

---

### Post by taurus on 2007-02-11
```
sudo umount /dev/hda1
sudo mkdir /media/hda1
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
df -h
```

---

### Post by Roman78 on 2007-02-11
Thank you! 

It's working...

---

