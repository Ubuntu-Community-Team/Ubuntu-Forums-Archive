---
title: "How to Restore Ubuntu Grub After Trying Other Distro?"
date: 2007-03-17
forum: General Help
---

### Post by LaneLester on 2007-03-17
For  reasons that need not be explored here, I installed another Linux distro on a spare partition, and now its grub is controlling the boot. I'd like to dump it and get my Ubuntu grub with its existing menu.lst back. Can I do that reliably? I see a bunch of scary messages about restoring grub.

Lane

---

### Post by chewearn on 2007-03-17
Unless you have a complicated setup like raid array or booting from usb drive, it should be quite easy and safe.  I have done it a bunch of times, haven't lost my install yet.

---

### Post by LaneLester on 2007-03-17
> **AstalaVista said:**
> Unless you have a complicated setup like raid array or booting from usb drive, it should be quite easy and safe.  I have done it a bunch of times, haven't lost my install yet.

Thanks, the only thing complicated is the number of partitions I have on two drives. So what is the procedure?

Lane

---

### Post by Irony on 2007-03-17
Try this;

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by fragos on 2007-03-17
When you install an additional Linux distro it appears that the MBR now points to /boot/grub in the paratition you just installed in.  menu.lst in that grub only recognizes kernels in its paratition.  To be able to pick between the two distros you'll have to edit the menu.lst to include the lines from the previous menu.lst.  Now either can be selected when you boot.  To me that was easier to figure out than how to use the grub command.

---

