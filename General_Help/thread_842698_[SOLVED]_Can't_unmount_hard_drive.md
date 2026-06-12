---
title: "[SOLVED] Can't unmount hard drive"
date: 2008-06-27
forum: General Help
---

### Post by drjonze on 2008-06-27
Hello,

I'm dual booting Windows and Ubuntu. I used the NTFS config. tool to auto-mount my c: drive as I wanted easy access to some files on that drive. I have since moved everything to Ubunutu so I no longer need that drive. I tried to unmount it by right-click-unmount volume but it says I do not have permission. I opened the config tool but it only gives me an option to enable write access. I just want to unmount it and then removed the cofig tool so it will not auto-mount it anymore. Any suggestion?

---

### Post by russlar on 2008-06-27
open terminal, and run df -h. this will tell you all the hard drives mounted. then, run sudo umount /dev/something, where somethign is the name of the hard drive that you want to unmount.

---

### Post by drjonze on 2008-06-27
> **russlar said:**
> open terminal, and run df -h. this will tell you all the hard drives mounted. then, run sudo umount /dev/something, where somethign is the name of the hard drive that you want to unmount.

Thanks!

---

