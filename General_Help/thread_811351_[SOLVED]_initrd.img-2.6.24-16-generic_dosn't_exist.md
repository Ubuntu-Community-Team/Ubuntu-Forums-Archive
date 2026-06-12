---
title: "[SOLVED] initrd.img-2.6.24-16-generic dosn't exist"
date: 2008-05-29
forum: General Help
---

### Post by ttocsrox on 2008-05-29
hi guys
 initrd.img-2.6.24-16-generic doesn't exist
 what do i do?

---

### Post by forestpixie on 2008-05-29
What did you do to find out that it doens't exist in the first place?

---

### Post by ttocsrox on 2008-05-29
it came up with a error message when i try to boot ubuntu

---

### Post by WRDN on 2008-05-29
Try reinstalling the linux image, by booting into recovery mode, selecting the "root" option and entering:

> apt-get install --reinstall linux-image-2.6.24-16-generic

---

### Post by forestpixie on 2008-05-29
If that doesn't work can you boot with an old kernel, if not then recovery mode - then check you have these in /boot

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic

If they are all there you might need to update-initramfs and update-grub, but not completely sure.

---

### Post by ttocsrox on 2008-05-30
initrd.img-2.6.24-16-generic dosnt exist the rest do

---

### Post by gdzsi on 2008-05-30
try "update-initramfs -k all -u" or "update-initramfs -k all -c" in recovery mode!

---

### Post by ttocsrox on 2008-05-31
> **gdzsi said:**
> try "update-initramfs -k all -u" or "update-initramfs -k all -c" in recovery mode!i tried this but when i was in the recovery mode the computer turned off

---

### Post by forestpixie on 2008-05-31
Try this

```
update-initramfs -c -k 2.6.24-16-generic
```

If that doesn't work I'm not sure, you could try to enable the proposed updates and then install 2.6.24-17-generic

---

### Post by ttocsrox on 2008-05-31
were do it try this

---

### Post by forestpixie on 2008-06-01
at the command propmt in recovery mode

---

