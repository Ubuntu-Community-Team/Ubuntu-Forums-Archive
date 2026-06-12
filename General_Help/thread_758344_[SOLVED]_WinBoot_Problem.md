---
title: "[SOLVED] WinBoot Problem"
date: 2008-04-17
forum: General Help
---

### Post by Crath on 2008-04-17
I have installed Ubuntu 2 times now with Wubi and it works great!! accept for one thing, when I go and try to run WinBoot, I get an error.

Error Popup Title: 16-Bit MS Dos Subsystem
Error Content: 

c:\ubuntu\winboot\wubildr.exe
The NTVDM CPU has encountered an illegal instruction.
CS:0e02 IP:44f9 OP:9d 61 07 1f fa Choose 'Close' to terminate the application.

Error Options: Close and Ignore

Trying both of the choices do nothing.

What can I do to make this work? Thanks!!

ps: booting into ubuntu via boot menu on startup works flawlessly!

---

### Post by Crath on 2008-04-19
bump

thanks

---

### Post by ago on 2008-04-20
The "16-Bit MS Dos Subsystem" is due to missing damaged files on your windows setup. This can be due to a virus.

Look for "16-Bit MS Dos Subsystem" in google for a few fixes.

You have to repair that first, then you can install wubi.

---

### Post by Crath on 2008-04-20
> **ago said:**
> The "16-Bit MS Dos Subsystem" is due to missing damaged files on your windows setup. This can be due to a virus.

Look for "16-Bit MS Dos Subsystem" in google for a few fixes.

You have to repair that first, then you can install wubi.

alright thanks, will it still work if i fix it now after I already have wubi installed?

---

### Post by ago on 2008-04-20
yes

---

