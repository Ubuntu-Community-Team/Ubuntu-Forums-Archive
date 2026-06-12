---
title: "Partitioning help"
date: 2007-07-28
forum: General Help
---

### Post by Mostlyharmless42 on 2007-07-28
I currently have Feisty Fawn installed on my hard drive, but i'd like to have a windows partition for easy gaming and i was wondering how i would go about partitioning my hard drive for a windows install.

---

### Post by Happy_Man on 2007-07-28
Well.... since Windows *loves* being first.... you will have to wipe your drive and reinstall Windows. Then,

If using XP: use the Ubuntu partitioner on the LiveCD to get your Ubuntu back

If using Vista: use Vista's partitioner to set aside some space, and then install Ubuntu.

Back everything up first!

---

### Post by Mostlyharmless42 on 2007-07-28
i was kinda hoping i wouldn't have to loose my data....

---

### Post by Happy_Man on 2007-07-28
> **Mostlyharmless42 said:**
> i was kinda hoping i wouldn't have to loose my data....
You don't have to.... just back everything up.

---

### Post by rillip on 2007-07-28
Bottom line is that Windows doesn't work well unless it's on the first partition, typically.  And in either case, it will overwrite the mbr so that grub no longer appears.  This is why dual boots always recommend installing Windows first.

What you can try is to download something like the gparted or qparted live cd, boot from it, and try resizing your partition by moving the start.  If you can, then after you install Windows to that partition, you'll have to boot from the live CD and reinstall grub.  Make sure to back up your /boot/grub/menu.lst first.  This might or migh tnot work, I've not tried it before.  Total reinstalls are really the only absolute option.

---

