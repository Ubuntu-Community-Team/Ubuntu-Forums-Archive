---
title: "Restart freeze 18.10"
date: 2018-11-11
forum: General Help
---

### Post by PantherStu on 2018-11-11
Hi all,
On Ubuntu 18.10 on restart I am having an issue where my PC just freezes. Screen shots attached, second screenshot is what shows and sits on after 1st screenshot.

Advice please.

---

### Post by hyottositara on 2018-11-11
If you can get to the terminal on that screen by pressing "CTRL+ALT++F2" or  "CTRL+ALT+F3," then login, you could try installing the proprietary  Nvidia drivers as per the second set of instructions here: [https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04](https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04)

If you can't even get to the terminal, or you don't want to use the proprietary drivers, you might try using "nomodeset" on boot as per this forum post: [https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by PantherStu on 2018-11-14
Thankyou, worked perfectly,  needed the proprietary drivers

---

