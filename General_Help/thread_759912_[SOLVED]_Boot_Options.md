---
title: "[SOLVED] Boot Options"
date: 2008-04-19
forum: General Help
---

### Post by seandgibbonsy on 2008-04-19
I understand that Ubuntu 8.04 is coming with Wubi. This let's it install like any normal program then you can select which OS to boot when the computer boots up. My question is, when the boot screen comes up does Wubi automatically select what OS to load after a few seconds and can I set which OS it automatically loads? My parents and sister still use this computer and they like Windows XP so I don't want them to get mad when it automatically loads Ubuntu or they have to click Launch Windows everytime they want to boot up the computer. So I want to make Wubi automatically launch Windows (after like 5 seconds) when The power is turned on.

---

### Post by lswest on 2008-04-19
i'm pretty sure you can edit the GRUB menu.lst using startupmanager or a normal text editor through a WUBI install just like a normal HDD install.  If you need more information on how to do it just post back, and i'll explain thoroughly.

*EDIT* read up on it, uses the XP bootloader and an entry there, so my suggestion above is irrelevant.

---

### Post by ago on 2008-04-19
> **seandgibbonsy said:**
> My question is, when the boot screen comes up does Wubi automatically select what OS to load after a few seconds and can I set which OS it automatically loads?
The default is always windows, you can change that from the control panel.
As a not, the bootloader relevant for that is ntldr not grub

---

### Post by seandgibbonsy on 2008-04-19
> **ago said:**
> The default is always windows, you can change that from the control panel.
As a not, the bootloader relevant for that is ntldr not grub

Okay good.  For a minute I was a little worried.  I'm glad that it will run windows automatically if told otherwise.  But after how many seconds will it boot up the OS.  Meaning, how long will it stay at the Wubi OS select screen?

---

### Post by ago on 2008-04-20
10 if memory does not fail me

---

### Post by airjer on 2008-04-20
> **ago said:**
> 10 if memory does not fail me

Yep, 10. Grab a copy of EasyBCD and you can change the timeout to your liking.

---

