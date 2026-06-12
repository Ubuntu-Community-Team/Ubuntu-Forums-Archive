---
title: "External hard drive problem"
date: 2008-05-15
forum: General Help
---

### Post by mtblock on 2008-05-15
I have switched to ubuntu because my vista OS crashed. at that time, my external hard drive was connected, and it has since been disconnected. When I plug it in, ubuntu tells me I must go back to windows to eject, which is impossible. What should I do?

---

### Post by tamoneya on 2008-05-15
you just need to force the mounting:```
sudo mount -t ntfs /dev/sdb1 /some/directory -o force
```
 If you dont know what I mean when I say /dev/sdb1 you should post the result of ```
sudo fdisk -l
```

---

