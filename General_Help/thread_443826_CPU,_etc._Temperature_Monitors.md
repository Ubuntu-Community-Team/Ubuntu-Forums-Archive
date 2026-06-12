---
title: "CPU, etc. Temperature Monitors"
date: 2007-05-14
forum: General Help
---

### Post by rscott5 on 2007-05-14
Hey everyone,

I'm running Feisty on an "old" Gateway desktop machine that has a Pentium4 1.5 GHz processor in it. When I used to run Windows XP on it, I had an application which would run in the system tray and monitor my temperatures for the CPU and board, among other things. I was wondering if there is any sort of app for Linux that would support my proc. I'm using gDesklets for diskspace, memory, etc. so something like that would be awesome. I tried the gDesklets temperature extensions, but they didn't seem to work. Is there an app out there that would accomplish this task for me? I just want to be able to see the temp of my processor as the summer gets hotter here. Thanks in advance for your help.

---

### Post by Talon2 on 2007-05-14
> **rscott5 said:**
> Hey everyone,

I'm running Feisty on an "old" Gateway desktop machine that has a Pentium4 1.5 GHz processor in it. When I used to run Windows XP on it, I had an application which would run in the system tray and monitor my temperatures for the CPU and board, among other things. I was wondering if there is any sort of app for Linux that would support my proc. I'm using gDesklets for diskspace, memory, etc. so something like that would be awesome. I tried the gDesklets temperature extensions, but they didn't seem to work. Is there an app out there that would accomplish this task for me? I just want to be able to see the temp of my processor as the summer gets hotter here. Thanks in advance for your help.

Install these packages:

- lm-sensors (then run sensors-detect to configure)
- sensors-applet

---

### Post by rscott5 on 2007-05-14
> **Talon2 said:**
> Install these packages:

- lm-sensors (then run sensors-detect to configure)
- sensors-applet

It worked perfectly for my hard drives (once I also installed hddtemp), but is unable to find sensors for my CPU. I don't know anything about how sensors-detect works, but here is what is added to /etc/modules: ```
# I2c adapter drivers
i2c-i801
# Chip drivers
adm1025
eeprom
smsc47m1
```

Any ideas?

---

### Post by confused57 on 2007-05-14
Maybe this will help?:
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

---

### Post by rscott5 on 2007-05-14
> **confused57 said:**
> Maybe this will help?:
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

Thanks that worked :-D

---

