---
title: "let a specific module be loaded before other"
date: 2007-04-19
forum: General Help
---

### Post by zerwas on 2007-04-19
[SOLVED]
Hello,

My mouse driver needs to be loaded before usbhid and hid are loaded.
I don't know how i can handle this. Even deleting the .ko don't help, the modules are still shown with lsmod and therefore my mouse does not work properly.
Thanks for reading!

Regards,
zerwas

edit: one solution is, to make in script with rmmod usbhid, modprobe the module and then modprobe usbhid again.

---

