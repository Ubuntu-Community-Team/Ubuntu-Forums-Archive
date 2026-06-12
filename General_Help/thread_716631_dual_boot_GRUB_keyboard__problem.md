---
title: "dual boot GRUB keyboard  problem"
date: 2008-03-06
forum: General Help
---

### Post by drumanart on 2008-03-06
Since a couple of days I cannot select WindowsXP, or other Kernel (recovery mode) partitions, because of the fact that the keyboard doesn’t work at the stage of the boot-process. After loading UBUNTU the keyboard works fine.
Thks.

---

### Post by kesman on 2008-03-06
Can you still access the BIOS? If not, then use another keyboard.

---

### Post by Distro Jockey on 2008-03-06
What changed on your system "a couple of days" ago?
I have seen some distro/hardware combo's that don't like USB keyboards.

---

### Post by drumanart on 2008-03-06
I can access the BIOS and the keyboard has a conventional plug (not USB). I installed new the UBUNTU STUDIO, but I can't tell whether this caused the problem.

---

### Post by tripmix on 2008-07-12
I'm having the same problem in debian, also a ps2 keyboard. My temporary workaround is I edit /boot/grub/menu.lst put the OS I want on top and let it timeout on boot. Just remember to have a linux boot disk ready if you plan to boot win. Very annoying bug...

Edit: I just noticed how old this post is, anyone find a fix?

---

### Post by Tod Merley on 2008-07-13
> **drumanart said:**
> Since a couple of days I cannot select WindowsXP, or other Kernel (recovery mode) partitions, because of the fact that the keyboard doesn’t work at the stage of the boot-process. After loading UBUNTU the keyboard works fine.
Thks.

Most say that when dual booting XP and other OSs, that the XP boot loader is the best choice (rather than grub) simply because XP tends to try to take back the boot load position whenever it happens to feel like it (probably an MS philosiphy thing).

It would be good for us to know what you did a few days ago, if anything, that may have been party to the change.

It may well also be helpful for us to see your "/boot/grub/menu.lst".

Try making the time out longer and hitting escape about half into the time out.?.

Good Hunting!

Tod

---

