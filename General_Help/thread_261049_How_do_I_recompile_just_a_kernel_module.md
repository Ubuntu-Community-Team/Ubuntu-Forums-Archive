---
title: "How do I recompile just a kernel module?"
date: 2006-09-19
forum: General Help
---

### Post by jay_cee on 2006-09-19
Can anyone point me towards some instructions for recompiling kernel modules? I don't need/want to recompile my whole kernel, I just need to apply a USB patch and recompile the USB driver.

Thanks - J

---

### Post by darrenm on 2006-09-19
```
sudo apt-get install module-assistant
sudo module-assistant update,prepare
sudo module-assistant build,install new_modulename
```

should do you. the kernel module should be in /usr/src/linux (i think bzipped) as new_modulename.tar.bz2 IIRC

---

