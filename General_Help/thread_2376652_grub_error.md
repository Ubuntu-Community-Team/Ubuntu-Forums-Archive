---
title: "grub error"
date: 2017-11-04
forum: General Help
---

### Post by ccyccxcl on 2017-11-04
hi.I have a problem when I tried to reboot my computer.And Windows 10 is ok,but the ubuntu met grub error.some ways have been tried:

 ls (hd0,msdos4)     
set boot=(hd0,msdos4)
set prefix=(hd0,msdos4)/boot/grub
insmod normal

so far,all is ok
as I type"insmod normal"
it reminds error:normal is already loaded.
and I could not move forward.
please help me.it took me almost the whole day.
I don't know what to do.please helpme.thank you.

---

### Post by Impavidus on 2017-11-04
Get your live disk and run [boot-repair](https://help.ubuntu.com/community/Boot-Repair). Don't run the recommended repair (yet), but create a boot info summary and share the link with us. That should give us some useful information on your system.

---

