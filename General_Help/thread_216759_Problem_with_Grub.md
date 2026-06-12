---
title: "Problem with Grub"
date: 2006-07-16
forum: General Help
---

### Post by mlys on 2006-07-16
My primany windows hard drive recently died, leaving me with my secondary hd with Ubuntu on it. I wanted to switch it to Master so I can use it until a new hard drive arrives. I'm able to chroot into it, but when I go to install grub, it gives me an error 23. I do "find /boot/grub/menu.lst" but it can't find that either. It's there though. Update-grub works, but I still can get my bootloader to work.

---

### Post by [S|G] on 2006-07-16
Grub error 23 is "Disk does not exist". It is probably trying to access the MBR from your old hard drive and cannot find it. Did you remove the drive physically from your computer? If so, did you also remove it from your BIOS?

---

### Post by Herman on 2006-07-16
Post deleted because I mis-read the question and gave an answer that wasn't relevant, now that I have read the question again I agree with the previous poster. (Sorry)

---

