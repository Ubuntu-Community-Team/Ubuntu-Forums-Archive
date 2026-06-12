---
title: "Grub error 21?"
date: 2007-04-30
forum: General Help
---

### Post by rock_bottom on 2007-04-30
Yeah, so, I'm new here. I'm new to Linux all together. So the other day I finally took the time to install Ubuntu (Feisty, by the way) on my computer which already has WindowsXP on it. Only problem is, I can't get to either of them because GRUB keeps giving me error message 21. I know that this means that it can't find the OS's on the drives. Please help! Would it work to take all of the Ubuntu files off and reinstall it, or is there a faster way?
Thanks so much (in advance).

---

### Post by zvacet on 2007-05-01
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by rock_bottom on 2007-05-04
Tried it, and it didn't work. There are a couple things that I figure are wrong, but one thing in particular is troubling me. In my menu.lst file, I see this for my Ubuntu partitions:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=23317e51-1ef4-4152-8a2d-1e9cbb6edb59 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=23317e51-1ef4-4152-8a2d-1e9cbb6edb59 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

What does "root=UUID=23317e51-1ef4-4152-8a2d-1e9cbb6edb59" mean, and should/can I change it?

---

