---
title: "Amiga WinUAE emulator fails to start in WINE"
date: 2021-09-19
forum: General Help
---

### Post by Brent_Santin on 2021-09-19
Hi,

I've used the Amiga emulator WinUAE (Windows version) in WINE (under Linux) for years. Hadn't used it for about a month and went to start it today and got the following error message (starting from terminal):
[INDENT]
> 000f:err:service: process_send_command receiving command result timed out
0023:err:ntdll:RtlpWaitForCriticalSection section 0x7bee54e0 "loader.c: loader_section" wait timed out in thread 0023, blocked by 0025, retrying (60 sec)
000f:err:service: process_send_command receiving command result timed out
X Error of failed request:  GLXBadFBConfig
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  0 ()
  Serial number of failed request:  261
  Current serial number in output stream:  261
[/INDENT]

Funny thing is all my other Windows software still starts fine in WINE. Does anyone know what might be causing this error only with WinUAE? Wine version is 5.0. WinUAE version is 4.4.0.

Thanks.

---

### Post by aug7744 on 2021-09-21
What your video card ?
Nvidia driver 470.63.01 is doing some issues crashing softwares (Shutter Enconder, Kdenlive, PCSX2).

---

