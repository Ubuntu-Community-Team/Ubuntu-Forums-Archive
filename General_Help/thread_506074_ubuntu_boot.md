---
title: "ubuntu boot"
date: 2007-07-21
forum: General Help
---

### Post by drytear on 2007-07-21
you know the progress bar shown when ubuntu boots. Can i get rid of it somehow and make it show me the boot messages? like .. what's loading ? in real time?

---

### Post by Koybe on 2007-07-21
I think you need to remove the splash option in your grub configuration file. 
```
 sudo gedit /boot/grub/menu.lst
```Change this line 
```
# defoptions=quiet splash
```to
```
# defoptions=quiet
```then upgrade
```
sudo update-grub
```

Or maybe it's the quiet option I'm not really sure about this, but you can test it. This is no big deal.

---

