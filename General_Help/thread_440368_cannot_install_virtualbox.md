---
title: "cannot install virtualbox"
date: 2007-05-11
forum: General Help
---

### Post by Bashed on 2007-05-11
Trying to install virtualbox, get the attached error even after full reboot

---

### Post by Bashed on 2007-05-11
I finally got it installed and created a Windows virtual disk. But now, it won't start (VD)


VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Bashed on 2007-05-11
Found fix:
Open **System --> Administration --> Users and Groups**
Click **Manage Groups**
Look up the *vboxusers* group in the list, select it and click **Properties**
In the users list find yourself and mark yourself.
Click **OK**, close any left open windows _and reboot_.

---

