---
title: "Boot options w/ 2 SATA drives, one Ubuntu, one Vista"
date: 2007-11-02
forum: General Help
---

### Post by theknowledgeist on 2007-11-02
Hello,

I have 2 SATA drives on my computer, one just for Windows Vista and one for Ubuntu 7.10. When I boot up my computer, I want it to ask me if I want to load Vista or Ubuntu. How do I do this? Thanks.

---

### Post by Pumalite on 2007-11-02
It seems to me you installed Grub in it's own partition, maybe with one drive disconnected. Is this true?

---

### Post by theknowledgeist on 2007-11-02
Yes, I installed Grub on the Ubuntu HD with the Vista HD disconnected. I don't know if Grub is on its own partition: I only created two partitions (swap and /) and let the installer install grub.

---

### Post by Pumalite on 2007-11-02
Well, get in Ubuntu and from the terminal post:
sudo fdisk -lu
cat /boot/grub/menu.lst
(no assurances this will work)
(you should have installed with both hard drives and let Grub install itself in MBR if you wanted what you requested in post # 1)

---

### Post by theknowledgeist on 2007-11-02
I'll just re-install Ubuntu with the Vista HD plugged it. Thanks Pumalite.

---

