---
title: "Control Networked Windows from Ubuntu"
date: 2008-05-03
forum: General Help
---

### Post by Literati on 2008-05-03
Hi everyone
I have 2 computers in my house, hooked up via router.
I have an Ubuntu computer, and a Windows XP Professional computer. 
They each have their own static IP adresses (Ubuntu: 192.168.1.101) (Windows: 192.168.1.137)

How can I, for example, use my Ubuntu PC to control the desktop of the Windows PC? Such as log in to a user, and run a program on that computer?

Thanks for the help!

Also, I've tried rdesktop with the following command

rdesktop -u Matt 192.168.1.137

But it just hangs. (Matt is the user on the Windows PC I want to use)

---

### Post by trdc on 2008-05-03
Sounds obvious but have you made sure that enable remote users to connect is enabled on the windows machine. If still no luck you could always use VNC?

---

