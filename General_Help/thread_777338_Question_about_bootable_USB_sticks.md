---
title: "Question about bootable USB sticks"
date: 2008-05-01
forum: General Help
---

### Post by rouge568 on 2008-05-01
Is it possible to have boot files one directory down on a bootable usb stick?
I just installed Damn Small Linux on my portable usb flash drive, and it is working fine. As of now, it can start up from BIOS or inside windows or linux (with a portable web server: its quite nice). Huzzah! My only issue is that there are ~20 files and folders on the root directory of the flash stick, and it looks quite cluttered. (Especially since I have other data on the stick as well). Is there a way to move all those files down a level (in a folder called, say "boot") and still be able to boot from BIOS?

---

### Post by warp99 on 2008-05-01
> **rouge568 said:**
> Is it possible to have boot files one directory down on a bootable usb stick?
I just installed Damn Small Linux on my portable usb flash drive, and it is working fine. As of now, it can start up from BIOS or inside windows or linux. Huzzah! My only issue is that there are ~20 files and folders on the root directory of the flash stick, and it looks quite cluttered. (Especially since I have other data on the stick as well). Is there a way to move all those files down a level (in a folder called, say "boot") and still be able to boot from BIOS?

You could, but the stick may not boot properly if the files are moved to a subdirectory and the pointers changed.

---

### Post by rouge568 on 2008-05-01
Well, I guess my question is what folder name should I make to subdirectory if I want BIOS to automatically navigate to it? (Or what file do I need to execute that)

---

### Post by rouge568 on 2008-05-02
bump

---

### Post by rouge568 on 2008-05-05
Anybody?

---

