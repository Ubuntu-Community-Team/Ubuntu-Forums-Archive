---
title: "How do I install Windows XP from Ubuntu?"
date: 2007-01-07
forum: General Help
---

### Post by JoeyM on 2007-01-07
Alright, well, I installed Ubuntu on my parent's computer and they want to go back to Windows. Well, I have a Windows XP install disc and I don't know how to install it from Ubuntu. When I insert it on start-up, it's like Ubuntu skips it and just boots itself. I can't run setup.exe from Ubuntu either.

---

### Post by scrooge_74 on 2007-01-07
change the bios settings so the Pc will boot from the CD instead of the HD

---

### Post by yager on 2007-01-07
> **JoeyM said:**
> and they want to go back to Windows

Please tell everyone that you backed up their data before you blew away their Windows XP partition.

When you set them up, did you partition their drive to dual boot or did you wipe the entire drive to put Ubuntu on their system?  If you are dual boot, then you can choose to boot into Windows and then
```
fdisk /mbr
```

This will remove GRUB, the bootloader, and replace it with the bootloader that Windows uses.

You can recover the physical space that was partitioned out by using GPartd.  There is a LiveCD you can download and burn that will allow you to remove the unwanted partitions and resize the Windows partition or allow you to create a new partition that would be their D:, E: or some other letter drive.

In the future, be careful with your evangelizing.  Leave the LiveCD with your convert  for a few days and let them play around with that.  Then when they are comfortable, offer to help them to take the next step.

---

