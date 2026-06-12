---
title: "How to start synergyc on boot or login ?"
date: 2016-04-18
forum: General Help
---

### Post by elpidiovaldez5 on 2016-04-18
I want to use the keyboard and mouse from my laptop (running lubuntu 14.04) on another machine, also using lubuntu 14.04.  I have googled this and found various people struggling with the same problem.  As a result I tried setting the last line of /etc/init.d/rc.local to:

```
synegyc xxx.xxx.xxx.xxx
```

The program does not appear to run on startup.  I also tried the full path, '/usr/bin/synergyc'.  That did not work either.

I'd be quite happy if I could run the program on login.  Following other peoples attempts, I tried putting the same program invocation in /etc/xdg/lxsession/Lubuntu/autostart

That did not do anything either.

Has anybody managed to do this, or know how it could be done ? It seems a pretty reasonable requirement since most people will not want to have to connect a local keyboard in order to enable using a shared keyboard.

---

