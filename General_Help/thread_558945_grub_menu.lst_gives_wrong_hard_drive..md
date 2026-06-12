---
title: "grub menu.lst gives wrong hard drive."
date: 2007-09-24
forum: General Help
---

### Post by keeler1 on 2007-09-24
After installation the bootloader could not find the initrd image.  When trying to boot any OS it said file not found.  So I edited the configuration while running the bootloader.  Turns out it had said to find Ubuntu on root(hd2,0) when it should have been on hd0,0.  So I went and changed my menu.lst once inside Ubuntu to be correct.  Then after doing another kernel update, it screwed itself up again.  Is there any way to fix this from happening again?

---

### Post by logos34 on 2007-09-24
maybe you forgot to change the 'groot' line?

---

