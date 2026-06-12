---
title: "[Lubuntu] Cannot force text mode boot"
date: 2018-07-03
forum: General Help
---

### Post by ronank on 2018-07-03
I have just installed Lubuntu 18.04 on an Asus Eee 1000H. I would prefer to boot this in console mode. I have followed the instructions at [https://linoxide.com/ubuntu-how-to/5-steps-start-ubuntu-text-mode/](https://linoxide.com/ubuntu-how-to/5-steps-start-ubuntu-text-mode/) and GRUB seemed to update correctly. However, the netbook still boots into graphical mode. What could be going wrong?

---

### Post by nlee2 on 2018-07-03
The instructions are for bios boot.

What is the output of
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

---

### Post by ronank on 2018-07-04
The output of that command is

```
BIOS
```

---

### Post by nlee2 on 2018-07-04
Try

```
GRUB_CMDLINE_LINUX="3"
```

---

### Post by ronank on 2018-07-05
That works, thanks.

---

