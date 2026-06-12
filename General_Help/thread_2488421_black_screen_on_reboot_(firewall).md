---
title: "black screen on reboot (firewall)"
date: 2023-07-04
forum: General Help
---

### Post by sohlinux on 2023-07-04
Hello,

When I reboot my computer or shut down and restart it I get a black screen.
The only way I have found to get the screen back to normal again is to reboot in recovery mode and disable the firewall with sudo ufw disable. there are no specific firewall rules set, only the default deny in and allow out. What could be causing this and how can I fix it? other than disabling the firewall before I reboot. Thanks

Ubuntu 22.04.2 LTS 64 Bit

---

### Post by #&amp;thj^% on 2023-07-04
Please run the system-info script found here:[https://ubuntuforums.org/showthread.php?t=2465764&page=12](https://ubuntuforums.org/showthread.php?t=2465764&page=12)

Please run it with "--details" flag added so we can have some information to go off to help you. Include the link it gives you when uploaded please.
Also have you yet tried removing "ufw" and reinstalling it? Sometimes that sets things proper again.
My suggestion first:
```
sudo apt autoremove --purge ufw
```
that tries to have a new like install.

---

### Post by sohlinux on 2023-07-04
I reinstalled ufw and now its working fine. Thanks

---

