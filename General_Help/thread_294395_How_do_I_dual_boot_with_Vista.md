---
title: "How do I dual boot with Vista?"
date: 2006-11-06
forum: General Help
---

### Post by morgue on 2006-11-06
I was running Ubuntu 6.10 and I installed Windows Vista RC1, when I turn on the computer I don't get an option to select Ubuntu to start, it just goes directly to Vista.

What do I have to do?
Thanks.

---

### Post by Kateikyoushi on 2006-11-06
Vista uses it's own bootloader and not grub so it has overwritten the mbr on your hdd.
You can use the ubuntu live cd or the grub disc to restore it. Read this for more information. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by Joe_CoT on 2006-11-06
Please see the [Grub Wiki Article](https://help.ubuntu.com/community/GrubHowto). Basically, Windows overwrote grub, because that's what it does. You need to add a windows option to grub, and then install grub again.

---

