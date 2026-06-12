---
title: "Set time reverts to previous hour"
date: 2017-02-20
forum: General Help
---

### Post by freshie on 2017-02-20
I'm new to Ubuntu. This may seem like a trivial question and may have answered previously, but I haven't found an answer to this on the forums. 

I set the correct time for my locality on BIOS then on 'settings' chose the correct time zone and then set the correct hour. The clock changes to the correct hour, but after the next restart, the hour shown is always exactly 4 hours earlier then the actual time, as if the time zone were incorrect, but on the 'set time' window is set correctly, Central Time zone and the correct city within that time zone. 

Thanks for the help.

---

### Post by Irihapeti on 2017-02-20
Is this a Xubuntu-only machine, or do you have Windows installed as well?

---

### Post by Impavidus on 2017-02-20
Windows usually sets the bios clock to local time, Ubuntu usually sets it to UTC. If dual booting multiple Linux systems, the latter is more convenient. But when the Ubuntu installer detects you're dual booting with Windows, it sets the bios clock to local time.

You can change that setting: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876) (valid for Ubuntu 16.04 and up)

---

### Post by freshie on 2017-02-21
Thanks for the comments.

There is only Xubuntu installed, no Windows anywhere, no dual boot. I don't know where the computer sets the clock 4 hours earlier than the time I set, there's only the BIOS time and the system's which I set exactly the same, taking care of choosing the correct time zone.

---

### Post by efflandt on 2017-02-21
I typically use **hwclock** to set the hardware (cmos) clock to system time and to tell Linux whether the hardware clock is localtime or UTC. See "man hwclock". Normally Ubuntu seemed to automatically recognize whether a computer is using Windows where the hw clock is localtime, but when I installed 16.04 on a Win10 laptop it did not. So typically assuming that your system time is correct:```
If computer dual boots Windows:
sudo hwclock -w --localtime

If Linux is the only OS:
sudo hwclock -w -u
```

---

