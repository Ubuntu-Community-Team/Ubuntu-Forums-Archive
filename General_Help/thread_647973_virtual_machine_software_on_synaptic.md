---
title: "virtual machine software on synaptic"
date: 2007-12-23
forum: General Help
---

### Post by chrishere01 on 2007-12-23
whats a good virtual machine software on synaptic
i wanna load up a window environment

---

### Post by Craigus on 2007-12-23
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Follow the instructions to add the repo to /etc/apt/sources.list, and you're away.

You'll have to > sudo adduser yourusername vboxusers

after installation to be able to use it.

---

### Post by chrishere01 on 2007-12-23
> **Craigus said:**
> [http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

Follow the instructions to add the repo to /etc/apt/sources.list, and you're away.

You'll have to 

after installation to be able to use it.

soo i did that

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 and i got that as an error message

---

### Post by chrishere01 on 2007-12-23
wow should have read that

---

### Post by zhouxing on 2007-12-23
I have the same error message with virtual box! I could not start the VM I created. I tried sudo adduser myusername vboxusers, but I still could not start it.

---

### Post by Craigus on 2007-12-23
>  I have the same error message with virtual box! I could not start the VM I created. I tried sudo adduser myusername vboxusers, but I still could not start it.


You have to log out and in again for the change to become effective.

---

### Post by zhouxing on 2007-12-26
I could run virtual box and installed XP as guest. But I could not use USB device in XP, it keep saying USB device error. Any ideas?

---

### Post by Craigus on 2007-12-26
Discussion and fix here:

[http://ubuntuforums.org/showthread.php?p=2507870]("http://ubuntuforums.org/showthread.php?p=2507870")

---

