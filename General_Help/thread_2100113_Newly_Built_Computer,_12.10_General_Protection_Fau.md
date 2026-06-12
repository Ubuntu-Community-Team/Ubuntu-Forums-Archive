---
title: "Newly Built Computer, 12.10 General Protection Fault"
date: 2012-12-31
forum: General Help
---

### Post by kyleflan on 2012-12-31
I recently built my first computer and installed Ubuntu 12.10 on it. I've been using Ubuntu for years, so I installed it on here two nights ago and everything was running smoothly until last night. I'm not even sure this is an Ubuntu-specific issue; it may be an error I made in constructing the computer.

In Google Chrome and Firefox (the only two applications I've noticed the error explicitly) when I'm browsing the web I'll get a black screen with an error message about a general protection fault on CPU 5 like this ([https://www.dropbox.com/s/74gj6f7cmk0u3mx/2012-12-31%2016.19.49.jpg](https://www.dropbox.com/s/74gj6f7cmk0u3mx/2012-12-31%2016.19.49.jpg)) and/or compiz closes. Usually the computer also freezes and I can't do anything except power it off and back on.

The outputs from lspci (hw.txt), /var/log/dmesg (dmesg.txt) and /var/log/syslog (syslog.txt) are attached for inspection.

[https://www.dropbox.com/s/85kec517kh49lwf/hw.txt](https://www.dropbox.com/s/85kec517kh49lwf/hw.txt)
[https://www.dropbox.com/s/1779s87p479vzzl/dmesg.txt](https://www.dropbox.com/s/1779s87p479vzzl/dmesg.txt)
[https://www.dropbox.com/s/uj4lxmtj2btxykm/syslog.txt](https://www.dropbox.com/s/uj4lxmtj2btxykm/syslog.txt)

If anyone could provide some insight or help guide me to figure out what's going on, I'd really appreciate it!!

---

### Post by tgalati4 on 2013-01-01
Run memtest for 30 complete passes.  If it passes then remove everything and build a minimum machine--little RAM, one hard disk, and try to run for a few days.  Ssh into it from another machine so if it freezes you might be able to see log files and shutdown remotely.

---

### Post by 2F4U on 2013-01-01
Additional to verifying the RAM, did you check the temperatures of critical components such as CPU and graphics cards?

---

### Post by kyleflan on 2013-01-01
> **tgalati4 said:**
> Run memtest for 30 complete passes.  If it passes then remove everything and build a minimum machine--little RAM, one hard disk, and try to run for a few days.  Ssh into it from another machine so if it freezes you might be able to see log files and shutdown remotely.

Will do.

> **2F4U said:**
> Additional to verifying the RAM, did you check the temperatures of critical components such as CPU and graphics cards?

Right after the crash I restarted into the BIOS and the CPU temperature was fine. I don't remember the exact temperature, but it wasn't critical or anything. No graphics card. Using Intel's integrated graphics.

---

### Post by kyleflan on 2013-01-01
I ran memtest and about an hour in, red errors started being displayed (over 20 million errors). I exited memtest, booted into the BIOS and realized the BIOS was recognizing my memory as 1333Mhz, even though it was 1600Mhz. I changed from the auto DRAM speed to 1600Mhz and the auto voltage to 1.65V (as per the manufacturer's specifications). I'll let memtest run tonight and see if any more errors pop up.

---

