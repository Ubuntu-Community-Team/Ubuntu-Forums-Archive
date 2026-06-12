---
title: "HELP------   wubi install error"
date: 2007-07-08
forum: General Help
---

### Post by herculesdoo on 2007-07-08
i'm a very very new user,  when i have installed wubi in-- disk d --(my windows xp files in disk c),then reboot , i choose ubuntu ,but the screen   gose like this :  boot “ubuntu"
                                                                                             kernel...................................
                                                                                             initrd.......................................
                                                                                             boot ...(the problem is  it gets  frozen  with the cursor continue to twinkling)

---

### Post by herculesdoo on 2007-07-08
oh ,add something  my cpu is AMD turion 64 ,is that the problem?

---

### Post by ago on 2007-07-08
remove the "quiet splash" words from c:\wubi\boot\grub\menu.lst to get a more verbose boot. See if there is any relevant error.

---

### Post by herculesdoo on 2007-07-09
remove the "quiet splash" words from c:\wubi\boot\grub\menu.lst to get a more verbose boot. See if there is any relevant error.
__________________

 it does't work !

---

### Post by ago on 2007-07-09
Replace all instances of "quiet splash" on each line that starts with "kernel"

---

