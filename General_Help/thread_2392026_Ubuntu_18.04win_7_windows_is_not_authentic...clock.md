---
title: "Ubuntu 18.04/win 7 windows is not authentic...clock?"
date: 2018-05-15
forum: General Help
---

### Post by techee1-5 on 2018-05-15
My question is, there is more than one way to correct the problem of clock off by 5 or 6 hours, what is the correct way to do this? I believe I took a shortcut, and now have problems with windows. "Your copy of Windows is not genuine."I think the problem is clock related???

---

### Post by QIII on 2018-05-15
Moved to General Help

---

### Post by hrsetrdr on 2018-05-15
> **techee1-5 said:**
> My question is, there is more than one way to correct the problem of clock off by 5 or 6 hours, what is the correct way to do this? I believe I took a shortcut, and now have problems with windows. "Your copy of Windows is not genuine."I think the problem is clock related???

I had the same issue with a system dual booting Linux and Win7,[ see this thread]("http://www.overclockers.com/forums/showthread.php/779370-Not-keeping-correct-time?p=7990622&viewfull=1#post7990622").

It is my observation that:

> **ihrsetrdr said:**
> 
So far, IF I just boot to Windows, reboot and go into the BIOS the time holds true.    However, when I reboot from Windows and boot into Linux, even though Linux time is correctly displayed as local time, when rebooting and going to the BIOS, the BIOS time setting has changed to UTC, which is 8 hours ahead of Pacific Time(here).   :shrug:


 
I believe this problem arises due to the following:

> Unified Extensible Firmware Interface (UEFI) is a specification for a software program that connects a computer's firmware to its operating system (OS)


On machines with traditional BIOS I doubt this would be an occurrence.

---

### Post by kerry_s on 2018-05-15
lol, not real cause the times wrong? really?

i think ubuntu uses utc, try disabling it. 
[http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/](http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)

check it first, my ubuntu 18 is using local time. so you might just need to change your windows.
```
timedatectl
```

[ATTACH=CONFIG]279709[/ATTACH]

---

