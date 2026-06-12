---
title: "freeze and kernel panic (caps lock flashing)"
date: 2018-01-08
forum: General Help
---

### Post by eli. on 2018-01-08
hi
[FONT=inherit]I installed ubuntu 16.04 on my laptop a month ago, and about two weeks in, my computer first froze and caps lock started blinking. Since then, it has happened at least 5 times, each with shortening intervals. Each time I had to shut down using the power button.
[/FONT]
[FONT=inherit]The freeze happens randomly-did not happen under heavy use (Happened when using only browser, while everything was fine when playing a cpu heavy game), hasn't happened during boot yet. In windows would get BSOD once in a while (every six months, maybe?), but other than that nothing indicated hardware failure.[/FONT]
[FONT=inherit]
Here are the things I've tried:
- Waiting. 8 hours did nothing. 
- Updating Kernel (was up to date). 
- Updating graphic card driver. 
- Every single thing here: [Ubuntu 15.10 and 16.04 keep freezing randomly]("https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly")[/FONT]
[FONT=inherit]
Some more relevant information:
**I have an external wireless adapter (TL-WN7200ND)** because my internal one is almost dead (it is disabled). 
When frozen, does not react to Alt+SysRq+REISUB, alt+sysrq+F, ctrl+Alt+F1, ctrl+Alt+delete[/FONT]
[FONT=inherit]System and computer info: 
Ubuntu 16.04 LTS, 
Asus laptop N550JV (4.5 years old), 
Nvidia Geforce 750M with proprietary driver, 
Intel i7-4700HQ CPU 2.4Hz[/FONT]
[FONT=inherit]
syslog: [https://pastebin.com/wmAUQtvn](https://pastebin.com/wmAUQtvn) crash happened at 17:38:34[/FONT]
[FONT=inherit]
From askubuntu got the following answer:
The log indicates faults with *two USB devices. You may wish to move this question to [ubuntuforums.org]("http://ubuntuforums.org/"), where gurus can take the time one-on-one to help you probe the problem further. At the moment, looks like freeze-caused-by-defective-hardware...which is indeed what most freezes are caused by. The Q&A format of AskUbuntu means that future users are unlikely to be helped by the question.*

edit:
Kernel panicked again. On waking from sleep, **as the external wi-fi adapter was turning on**.
syslog for second crash: [/FONT]https://pastebin.com/QnbadsU1 crash happened at 9:05:21.

[FONT=inherit]After the crash, I turned computer on and the wi-fi adapter turned on fine.
Could anybody tell me if there is a fix? it was a fairly expensive adapter and it's new..


Thank you.[/FONT]

---

### Post by eli. on 2018-01-10
Bump

---

