---
title: "Lubuntu 14.04 LTS suddenly screen lock is active when not wanted"
date: 2014-08-03
forum: General Help
---

### Post by rdh61 on 2014-08-03
OK, I go away for a month and when I come back suddenly my screen keeps locking if I leave the computer unattended for a few minutes. It did not do this before and I do not want it. I cannot find a setting which changes this behaviour. In Preferences -> Power Manager the checkbox "Lock screen when going for suspend/hibernate" is not checked. "Monitor power management control" is not checked. Please help me to get rid of this new annoyance.

Many thanks.

---

### Post by robbie 348 on 2014-08-03
Go into lightlocker in the menu, you should be able to set it in there.

---

### Post by rdh61 on 2014-08-03
Thanks. In Light Locker Settings under "Locking", "Enable Light Locker" was on, but "Automatically lock the session" was set to "Never" and "Lock on suspend" was off. I had to set "Enable Light Locker" to "off" in order to stop it locking the screen.

---

### Post by rdh61 on 2014-08-03
I spoke to soon. Disabling Light Locker _*does not*_, in fact, disable the screen lock. After the screen saver kicks in (blank screen), the screen is locked and I always have to re-enter my password. I do not want to have to do that. Any other solutions?

---

### Post by rdh61 on 2014-09-19
I'm bumping this thread because I have not been able to resolve this annoying problem, and I feel it must be something simple.

To recap:

1) My screen locks if the computer is inactive for a few minutes and I have to enter my password to unlock it. I do not want it to do this: it is annoying and time-consuming to have to keep re-entering my password.
2) My Light Locker settings (Menu -> Preferences -> Light Locker Settings) are:

Screensaver 
- Blank screen after 10 minutes
-Switch off display after 15 minutes.
Locking
- Enable light-locker: on
- Automatically lock the session: Never
- Lock on suspend: off

3) Even if I set "enable light-locker" to off, it still locks the screen.

Many thanks.

---

### Post by rdh61 on 2014-09-19
It seems I am not alone:

[http://askubuntu.com/questions/502942/lubuntu-enforces-screen-lock](http://askubuntu.com/questions/502942/lubuntu-enforces-screen-lock)

---

### Post by rdh61 on 2014-09-19
This bug report offers two possible solutions: (a) a workaround involving installing Xscrennsaver; (b) a "fixed" latest development version of xfce4-power-manager. I'll let you know how I get on.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716)

---

### Post by linux_dream on 2014-09-19
> **rdh61 said:**
> This bug report offers two possible solutions: (a) a workaround involving installing Xscrennsaver; (b) a "fixed" latest development version of xfce4-power-manager. I'll let you know how I get on.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716)

I personally solved the problem with the c) option:
c)Uninstall light-locker.

I had tried many, many other solutions and none worked. Since I don't need nor want to lock my screen anyway, option c) was great for me and I guess also for many other people.

---

### Post by rdh61 on 2014-09-24
My experience has been similar. I tried options (a) and (b) with no change in behaviour. The only option then is to uninstall light-locker, which I have done. I cannot mark this "solved": light-locker does not work properly.

---

### Post by linux_dream on 2014-09-24
> **rdh61 said:**
> My experience has been similar. I tried options (a) and (b) with no change in behaviour. The only option then is to uninstall light-locker, which I have done. I cannot mark this "solved": light-locker does not work properly.

You're not alone, it happened to me too ([http://ubuntuforums.org/showthread.php?t=2233295](http://ubuntuforums.org/showthread.php?t=2233295), I tried tons of stuffs!) and I've seen several threads in this forum with the exact same problem.
Option c) worked though... but as you said, you can't mark this thread as solved; and I can't mark mine as solved either.

---

