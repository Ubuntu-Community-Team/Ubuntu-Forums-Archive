---
title: "[SOLVED] Help with Virtual Box"
date: 2007-10-02
forum: General Help
---

### Post by jrharvey on 2007-10-02
I installed VBox fine and when I start the program to try and install windows XP I get this message..... Does anyone know what to do about this???


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by tgm4883 on 2007-10-02
Have you thought about going to System > Administration > Users and Groups and adding the user to the vboxusers group?

---

### Post by jrharvey on 2007-10-02
Thank you soooo much. It was sooooo opbvious and i didnt even realize. thanks again.

---

