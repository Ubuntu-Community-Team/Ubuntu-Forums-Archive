---
title: "Grub Error 17"
date: 2007-11-26
forum: General Help
---

### Post by nealeneale on 2007-11-26
i formatted my linux partition whilst in windows so i could do another install over it. rebooted the computer and was greeted with "GRUB Loading stage1.5. Grub Loading, please wait... Error 17"

laptop doesnt have cd-rom so i bought an external one and it wont boot from live cds. i boot the cdrom then im back into that text about grub.

cant type anything in, cant do anything. just have to switch it off. can anyone help?

---

### Post by qqzhenyi on 2007-11-26
Guessing...
You formatted the partition, but GRUB still there.

1) When you turn your computer on, go into the BIOS, set it to boot CD first.
2) Boot from your windows cd, when it ask you whether you want to install windows blabla, press R to enter the recovery console.
3) type fixmbr, it will remove GRUB.

(I assume you're using Windows XP professional edition)

---

