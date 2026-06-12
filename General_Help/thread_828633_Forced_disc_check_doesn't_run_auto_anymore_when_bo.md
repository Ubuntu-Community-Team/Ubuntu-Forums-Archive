---
title: "Forced disc check doesn't run auto anymore when booting..."
date: 2008-06-13
forum: General Help
---

### Post by Lord Xeb on 2008-06-13
After 23 mounts, Ubuntu will boot about 1/4 of the way, then stop and I get a black screen with a blinking cursor. Nothing happens from there. Not it just stops. Then when I go into recovery mode, the disc check commences automatically and after a reboot it works just fine. What is going on?

---

### Post by Lord Xeb on 2008-06-16
Any suggestions? This thing is driving me nuts. It use to occur automatically while my system booted and did so then moved on to my login screen. Why is this happening?

---

### Post by plucky on 2008-06-17
Post the output of ```
cat /etc/fstab
```


Also:-

You could try next time to hit the <esc> key,to stop the fsck and continue the boot.If that doesn't work,then in your menu.lst remove the word **quiet** from the kernel line and the other line so you can see what part of boot sequence is failing.

```
gksudo gedit /boot/grub/menu.lst
``` to edit the menu.lst file.

> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro splash 
initrd		/boot/initrd.img-2.6.24-19-generic


Should look similar to this.


Good Luck

---

