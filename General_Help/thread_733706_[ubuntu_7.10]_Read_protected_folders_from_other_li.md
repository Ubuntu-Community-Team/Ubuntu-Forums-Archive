---
title: "[ubuntu 7.10] Read protected folders from other linux drive?"
date: 2008-03-24
forum: General Help
---

### Post by earithramir on 2008-03-24
Hi,

I am trying to open folders on a hard disk from an other computer (running linux) in ubuntu 7.10.
But the folders are protected and i can not view the content.
I do know the root username and password and the username and password from the samba shares.

Ill try to explain the best i can:

The harddiskdrive i connected to my computer is from my NAS storage device, this device is running linux as a operating system and i know that the root acces only requires a username (root) and no password.
The folder im trying to open is a shared folder on that operating system and i do have the username and password, and i shared it to be used without username and password.

Steps i took:
1. disconnected drive from NAS
2. connected drive from NAS to my computer
3. booted computer using live CD from ubuntu.
4. succesfully mounted the partition

Is there a way to open that folder using an username and password , if sow how?
Im trying to write files to the directory so i need read/write permission.

thanks in advance!

---

### Post by dcstar on 2008-03-24
> **earithramir said:**
> Hi,

I am trying to open folders on a hard disk from an other computer (running linux) in ubuntu 7.10.
But the folders are protected and i can not view the content.
I do know the root username and password and the username and password from the samba shares.

Ill try to explain the best i can:

The harddiskdrive i connected to my computer is from my NAS storage device, this device is running linux as a operating system and i know that the root acces only requires a username (root) and no password.
The folder im trying to open is a shared folder on that operating system and i do have the username and password, and i shared it to be used without username and password.

Steps i took:
1. disconnected drive from NAS
2. connected drive from NAS to my computer
3. booted computer using live CD from ubuntu.
4. succesfully mounted the partition

Is there a way to open that folder using an username and password , if sow how?
Im trying to write files to the directory so i need read/write permission.

thanks in advance!

Create a launcher with the following and you should have root access to any folder/file:

```
gksudo nautilus
```

---

### Post by earithramir on 2008-03-24
> **dcstar said:**
> Create a launcher with the following and you should have root access to any folder/file:

```
gksudo nautilus
```

Thanks a million!
This works really great, i did not expect such a simple and fast solution!
appreciate it really much!

You just saved me week !!

---

