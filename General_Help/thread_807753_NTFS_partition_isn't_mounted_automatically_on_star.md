---
title: "NTFS partition isn't mounted automatically on startup"
date: 2008-05-26
forum: General Help
---

### Post by yostane on 2008-05-26
hello,
Look at the video to better understand, the wallpaper's source is the NTFS partition.
Thanks for the help

---

### Post by forestpixie on 2008-05-26
Make sure you have both ntfs-config and ntfs-3g installed
```
sudo apt-get install ntfs-3g ntfs-config
```

It will put a tool in system tools which you can use to get read/write and mount at start. Set up the ntfs drives as you want from the ntfs tool and reboot.

---

### Post by yostane on 2008-05-26
thanks for the help, but I didn't have this problem on Ubunutu 7.10. Does it have to do something with autorisations, because an autorisation window asked for a password the first time.

---

### Post by forestpixie on 2008-05-26
You'll probably need to unlock authorise yes

---

