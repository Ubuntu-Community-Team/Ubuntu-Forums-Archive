---
title: "Grub error after update"
date: 2017-10-30
forum: General Help
---

### Post by Hewjr100 on 2017-10-30
Freshinstall of Ubuntu 16.04.3 got this message after updating system,rebooting, and updated grub manually.  This is what I got.  Also got this error in Grub Customizer.

```
sudoupdate-grub
Generatinggrub configuration file ...
usingcustom appearance settings
Foundbackground image: /home/henry/Pictures/Lake & Forest.jpeg
Foundlinux image: /boot/vmlinuz-4.10.0-37-generic
Foundinitrd image: /boot/initrd.img-4.10.0-37-generic
Foundlinux image: /boot/vmlinuz-4.10.0-28-generic
Foundinitrd image: /boot/initrd.img-4.10.0-28-generic
Foundmemtest86+ image: /boot/memtest86+.elf
Foundmemtest86+ image: /boot/memtest86+.bin
Foundlinux image: /boot/vmlinuz-4.10.0-37-generic
Foundinitrd image: /boot/initrd.img-4.10.0-37-generic
Foundlinux image: /boot/vmlinuz-4.10.0-28-generic
Foundinitrd image: /boot/initrd.img-4.10.0-28-generic
error:syntax error.
error:Incorrect command.
error:syntax error.
Syntaxerror at line 109
Syntaxerrors are detected in generated GRUB config file.
Ensurethat there are no errors in /etc/default/grub
and/etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.newfile attached.
```

Henry

---

### Post by yancek on 2017-10-30
[QUOTE]Syntaxerror at line 109[\QUOTE]

There's a clue.  You might post what is actually on line 109 of the grub.cfg, maybe a few lines before/after for context.

---

### Post by Hewjr100 on 2017-10-30
Can't right now installing  Ubuntu 17.04 instead.  If problem is in 17.04, then I will check line 109.

Henry

---

### Post by Hewjr100 on 2017-10-30
OK installed Ubuntu 17.04, updated and no issues with grub.  Noticed that kernel is now at 4.10.0-38.  For whatever reasons the previous kernel 4.10.0-37 or something else was causing my fan to run at top speed.  Now it's hardly running at all.  Go figure.

Henry

---

