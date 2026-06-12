---
title: "[SOLVED] CPU-Z doesn't work on Windows XP/2000 in VMWare"
date: 2007-01-21
forum: General Help
---

### Post by altonbr on 2007-01-21
So I recently got VMWare player and QEMU working in and have been able to install Ubuntu 4.10 Warty, Ubuntu 7.04 Feisty Herd 2, Windows XP Pro and Windows 2000 Pro.

I have a DVD full of useful win32 software (that I regularly update) that has several versions of CPU-Z. I wanted to try Win2000's compatibility with them, and same with XP. What I found though, was quite odd... none of them worked. I have CPU-Z 1.09 all the way up to 1.38, and the only .exe file that worked was latency.exe ... "cpuz.exe" seemed the change the mouse cursor to "busy" but then no program ran. I checked the processes and programs list, but it didn't appear. I ran them through Command Prompt as well, but that failed to receive a positive result.

Does anyone know what might be going on? I was able to install AVG Free, Adobe Reader 8 (wanted to try it out) and WinRaR 3.62...

Oh yeah, I also tried changing the compatibility layer to Windows 95, 98 and NT, but it didn't change anything.

---

### Post by mindwarp on 2007-01-22
VMWare is a **V**irtual **M**achine.  Applications inside this have no access to the real processors specs, only the virtual vmware processor.  CPU-Z probably isn't programmed to handle that. This is not a ubuntu related question, you would find better help from vmware.

---

### Post by altonbr on 2007-01-22
That's true, I was just wondering if anyone had an opinion. Thanks.

---

