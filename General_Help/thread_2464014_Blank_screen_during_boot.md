---
title: "Blank screen during boot"
date: 2021-06-23
forum: General Help
---

### Post by manoj88 on 2021-06-23
My Lenovo legion Y540 laptop (with Ubuntu 20.04) is going blank after boot before login screen.(Please refer attached image where the screen goes blank exactly at same point after the commands shown in image everytime) Please let me know how can it be resolved as i am new to using Ubuntu.

---

### Post by grahammechanical on 2021-06-23
There is nothing to resolve. What do you expect to see? 

The Linux boot loader (called Grub) loads the Linux kernel. What you are seeing are kernel messages printed to the screen. At some point the kernel will load a display manager which should present a purple screen with Ubuntu 20.04 printed on it. Then the login screen will appear. All this takes time and is not always a smooth operation.

A Linux distribution is made up of software developed by different groups of software developers and stitched together. Boot loader, kernel, display manager, video display driver, login screen, user name & password utility, desktop environment, user interface, OS utilities - all developed by different groups of developers and stitched together. It is a wonder that it works at all. Oh, and lets not forget all the work done to make Linux a secure operating system.

Regards

---

### Post by manoj88 on 2021-06-23
Thanks for the response. Fyi, Login screen is not shown. Only blank dark screen is shown. That is the issue.

---

### Post by manoj88 on 2021-06-23
Thanks for the response. Fyi, Login screen is not shown. Only blank dark screen is shown. That is the issue.

---

