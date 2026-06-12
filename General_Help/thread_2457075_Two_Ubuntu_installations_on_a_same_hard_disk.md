---
title: "Two Ubuntu installations on a same hard disk?"
date: 2021-01-25
forum: General Help
---

### Post by username2758 on 2021-01-25
Hello,

Is it possible to have two completely identical installations of the same Ubuntu distribution (or any Linux-based distribution) on a same hard disk?

My goal here is to have one default Ubuntu installation for daily use, and the other for testing purposes.

Thanks!

---

### Post by Hagar Delest on 2021-01-25
Of course it is. I've 2 different partitions for /. At each Ubuntu upgrade, I use the other partition to install from scratch. Thus, if something goes wrong (it happened twice in 10+ years), I still have the previous flavor.
Of course my documents are on another partition and I mount this partition at the same location so that it's transparent whatever the system booted.

---

### Post by username2758 on 2021-01-25
Thank you!

It's actually pretty good advice to have a different partition of the same distribution installation so that if something goes south, you still have your main installation intact.

Also, can you do that with any other Linux distributions no problem too?

---

### Post by Hagar Delest on 2021-01-25
I've never tried but I think that any other distro that supports multi-boot should be OK.
A boot loader may be replaced by another one depending on the one used by the last distro installed. But I guess that they would also detect the other OS' already installed.

---

### Post by crip720 on 2021-01-25
Most OSs will be quite happy to share a hard drive.  As long as each has enough space, you can have almost any mix of Linux, Windows and/or Mac OSs you want.

---

### Post by yancek on 2021-01-25
If you have an older machine with a Legacy BIOS, the default install will overwrite the Grub Code in the MBR so understand that if you leave defaults, the 2nd install will be in charge of booting.  If you don't want that, you will need to use the manual installation method to select where to install Grub. 

If you have a UEFI install, the second Ubuntu install would overwrite the first install Grub files on the EFI partition so the 2nd install would be in charge of booting.  This of course can be changed after install.

---

### Post by username2758 on 2021-01-27
> **yancek said:**
> If you have an older machine with a Legacy BIOS, the default install will overwrite the Grub Code in the MBR so understand that if you leave defaults, the 2nd install will be in charge of booting.  If you don't want that, you will need to use the manual installation method to select where to install Grub. 

If you have a UEFI install, the second Ubuntu install would overwrite the first install Grub files on the EFI partition so the 2nd install would be in charge of booting.  This of course can be changed after install.

Yes, thank you.

---

