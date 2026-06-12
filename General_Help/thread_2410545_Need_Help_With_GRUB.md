---
title: "Need Help With GRUB"
date: 2019-01-16
forum: General Help
---

### Post by tb75252 on 2019-01-16
I am using Ubuntu 18.04.1 LTS, 64-bit.  GRUB is installed in /dev/sda.

I recently installed   android-x86_64-8.1-rc2 in its on partition (/dev/sda9).  I downloaded it from:
[http://www.android-x86.org/download](http://www.android-x86.org/download)

I then modified /etc/grub.d/40_custom as follows:
```
menuentry "Android-x86_64-8.1-rc2"
{
set root='(hd0,9)'
linux /android-8.1-rc2/kernel quiet root=/dev/ram0 androidboot.selinux=permissive acpi_sleep=s3_bios,s3_mode SRC=/android-8.1-rc2
initrd /android-8.1-rc2/initrd.img
}
```

But upon running
```
sudo update-grub
```
I get the following error message:
> error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 512
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.

Is there anybody running both Ubuntu and Android who can help me with GRUB?

---

