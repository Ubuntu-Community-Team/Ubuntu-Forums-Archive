---
title: "Boot to Windows on default"
date: 2007-03-04
forum: General Help
---

### Post by RUGUNIT on 2007-03-04
Im having trouble figuring out how to alter menu.lst to make grub boot to windows xp by default. I read a different thread on this topic and it said to alter the list to make the default setting the windows entry, but it didnt go into enough detail. Can anyone expand on this for me? Thanks.

---

### Post by seldenthuis on 2007-03-04
You can change the default in menu.lst on line 14. After an Ubuntu installation it is set to 0, which will boot Ubuntu. You will probably have 5 entries in your menu.lst:

0. Ubuntu, kernel 2.6.17-11-generic
1. Ubuntu, kernel 2.6.17-11-generic (recovery mode)
2. Ubuntu, memtest86+
3. Other operating systems:
4. Windows XP

Although number 3 is just a spacer, it still counts. Just change 'default 0' to 'default 4' to make GRUB boot into Windows by default.

---

