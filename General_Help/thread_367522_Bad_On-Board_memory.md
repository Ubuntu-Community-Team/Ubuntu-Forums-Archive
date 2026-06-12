---
title: "Bad On-Board memory"
date: 2007-02-22
forum: General Help
---

### Post by broy55 on 2007-02-22
I own a Gateway laptop with 512MB of on-board memory. The memory is bad at the 381MB mark. It seems that more laptops these days come with on-board memory and when they go bad your laptop turns into a brick. Since it's too costly to repair or replace the laptop, I would like to install Ubuntu with a memory patch like 'BADRAM' or 'BADMEM'.  I'm still a rookie when it comes to Linux so I was wondering if anyone has had any success with this and can explain how they did it. Perhaps someone knows of a Distro with these options built in?

---

### Post by broy55 on 2007-02-22
bump

---

### Post by broy55 on 2007-02-22
Someone must have a solution to this problem. I really hate to dump this laptop because of a bad memory region.

---

### Post by jeffathehutt on 2007-02-22
I can't guarantee this will work, but try adding mem=370M to your kernel arguments.  Once grub starts, select your linux kernel and hit the 'e' key to edit the arguments.  Type 'mem=370M' at the end and try booting with it.  If this solves your problem, you can permanently add it to the boot line in /boot/grub/menu.lst

Do note that you will only have access to 370 MB of ram if you do this.

---

### Post by broy55 on 2007-02-23
I tried that with Ubuntu but it didn't seem to work. It did work with Mandriva though. Maybe Ubuntu doesn't have that command function in grub?

---

