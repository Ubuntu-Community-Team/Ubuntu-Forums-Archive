---
title: "Have to manually change grub menu.lst after a kernal update to be able to boot."
date: 2007-02-23
forum: General Help
---

### Post by blunden on 2007-02-23
I have recently gotten a small problem with grub on my laptop. I triple boot Ubuntu, Vista and XP on it. When I resized my windows partition to make a new Vista partition the Ubuntu partition changed from hd(0,1) to hd(0,2) using grubs syntax. Now everytime I install a bigger update like a kernel update Ubuntu won't boot because it resets it to hd(0,1) in grubs menu.lst. Is there any way to stop it from doing this?

---

### Post by llamakc on 2007-02-23
Yes. Edit your menu.lst. Show us what you have. After you edit it, you will run the `sudo update-grub` command. That should fix you right up.

---

### Post by blunden on 2007-02-24
Tried that now. Will see if it works after a kernel update. The menu.lst is still in working order at least. :D

---

