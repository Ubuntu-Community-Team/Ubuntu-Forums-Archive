---
title: "[boot menu] need to include windows safe mode"
date: 2008-01-23
forum: General Help
---

### Post by CactusWren on 2008-01-23
Hello, I have a dell laptop which had vista home edition installed on it at the factory. Over the Christmas holiday, I set it up to dual boot vista and gutsy.  All was working just fine until today. Now when I try to launch vista, it starts booting and then dumps memory and restarts the boot process for vista.  

I can still get into gutsy fine. My thought is that I need to go into vista in safe mode, but how do I tell grub to allow me into safe mode on vista?

---

### Post by Borbus on 2008-01-23
Booting into safe mode is part of the windows boot process... I think you have to press F6 or something... it's been a while since I used windows. Try booting from grub and then quickly bash F6 (or whatever key it is meant to be).

---

### Post by pointone on 2008-01-23
The correct key is F8, and as Borbus says, you need to do it after the Windows bootloader has started.

---

### Post by LaRoza on 2008-01-23
> **CactusWren said:**
> Hello, I have a dell laptop which had vista home edition installed on it at the factory. Over the Christmas holiday, I set it up to dual boot vista and gutsy.  All was working just fine until today. Now when I try to launch vista, it starts booting and then dumps memory and restarts the boot process for vista.  

I can still get into gutsy fine. My thought is that I need to go into vista in safe mode, but how do I tell grub to allow me into safe mode on vista?

If you mean a recovery console, you can add it to grub.

---

### Post by CactusWren on 2008-01-24
Ok how do I add the recovery console to my grub menu?
That sounds like whatI want.

---

