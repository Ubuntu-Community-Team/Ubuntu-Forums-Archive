---
title: "help computer wont boot"
date: 2008-02-27
forum: General Help
---

### Post by Zeke_777 on 2008-02-27
alright so i have vista and i decide to install ubuntu 7.10, i boot of live cd and install it on external usb, everything is fine and when i reboot and i am able to choose wether to boot windows or ubuntu. But then after i unplug my external and reboot i get grub loading error and i cant boot to my normal windows. i plug external back in and reboot and now i can go back on windows i dont get whats happening

---

### Post by Victormd on 2008-02-27
well, you installed ubuntu on the external drive, that means that your grub menu (menu.lst) is on the external drive, so every time you remove it, menu.lst "disapears" and grub doesn't know what to do...

---

