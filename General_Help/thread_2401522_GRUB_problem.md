---
title: "GRUB problem"
date: 2018-09-19
forum: General Help
---

### Post by sandrerk30 on 2018-09-19
Hello community, I have windows 7 and Ubuntu in the same partition. Well the problem is: In the grub I can't select the Windows option 'cause I broke my keyboard (only my down arrow is broken). I don't know if I can enter Windows manually or if I can change grub entry settings, I mean put another key instead.  Thanks for paying attention. ):P

---

### Post by yancek on 2018-09-19
> I have windows 7 and Ubuntu in the same partition

Do you mean on the same hard drive since the only way this would work otherwise is if you have either windows or Ubuntu installed virtually with something like VirtualBox or VMWare.

 If only your down arrow key is broken, you can set a different option to boot first and then use the up arrow key to access another option.  This can be done by editing as root user (use sudo) the /etc/default/grub file.  You can also manually create an entry on boot by using the 'e' key on your keyboard when you see the grub menu.  If you want someone to give you more details, post the grub.cfg file here, only need the section listing the various menuentry lines.

---

### Post by sandrerk30 on 2018-09-19
Thx a lot, I can solved my problem changing the grub_default. Thank you!

---

