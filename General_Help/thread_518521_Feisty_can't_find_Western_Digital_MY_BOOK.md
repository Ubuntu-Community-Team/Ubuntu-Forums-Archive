---
title: "Feisty can't find Western Digital MY BOOK"
date: 2007-08-06
forum: General Help
---

### Post by Uncle Spellbinder on 2007-08-06
I just did a clean install of Feisty, dual-booting with Vista Home Premium. My previous install had no problem recognizing the Western Digital My Book external drive. I have two Maxtor external drives (both appear on my desktop). My Western Digital My Book external drive is not being recognized. Ideas?

---

### Post by Uncle Spellbinder on 2007-08-06
Anyone?

---

### Post by Hallvor on 2007-08-06
This may happen when you don`t shut down your drive properly from the Windows NTFS-partition. Try logging in on Vista again, right click the drive icon and click "shut down", "remove device" or something like that (I never used the English version). Once done, try Ubuntu again.

You could also try mounting the drive in a terminal to see what is wrong.

---

### Post by Uncle Spellbinder on 2007-08-06
Thanks for the input.

Well, it wasn't showing up at all, like it didn't exist. So I shut down, unplugged the usb, booted into Feisty, plugged the usb in again and it's now available.

---

### Post by Uncle Spellbinder on 2007-08-06
Weird. Each time I reboot, it's not seen. The only way it becomes available is if I unplug the usb before booting Feisty.

Very odd.

---

### Post by strabes on 2007-08-07
You could just put a line into your /etc/fstab to mount it on bootup. If it doesn't happen to be plugged in on bootup (like if the computer is a laptop) then it shouldn't cause any problems.

---

### Post by Uncle Spellbinder on 2007-08-07
Desktop pc, the drive is always plugged in. Not sure what line to put into /etc/fstab, as I've never done that before.

---

