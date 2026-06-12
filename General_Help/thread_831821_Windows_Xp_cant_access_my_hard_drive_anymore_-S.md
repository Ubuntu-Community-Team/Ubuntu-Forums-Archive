---
title: "Windows Xp cant access my hard drive anymore :-S"
date: 2008-06-17
forum: General Help
---

### Post by mattgaunt on 2008-06-17
Hey everyone

After installing ubuntu hardy heron, when i boot into windows xp it just says it can't access the drive.

Does anyone have any idea how to fix this? i it to work until i can sort out my ubuntu to automatically mount my hard drives when i boot into ubuntu.

Any help would be greatly appreciated

Gaunt

---

### Post by rampageoberon on 2008-06-17
Are you trying to access the ext3 drives from windows? Or NTFS drives from ubuntu?

---

### Post by mattgaunt on 2008-06-17
sorry i didnt make that very clear, its a second hard drive that is NTFS that i want both ubuntu and windows xp to have access to

Gaunt

---

### Post by rampageoberon on 2008-06-17
Windows XP should have access to the NTFS drive without any issues. Check drive management in windows for more info.

Hardy supports ntfs drives using the ntfs-3g driver. But it needs that the drives were powered down properly, so a full shutdown in windows, or if its usb, then safely remove hardware.

To automount it add the drive to /etc/mtab

Hope that helps

---

