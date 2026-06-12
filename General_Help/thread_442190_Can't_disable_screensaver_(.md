---
title: "Can't disable screensaver :("
date: 2007-05-13
forum: General Help
---

### Post by Znupi on 2007-05-13
Ok so I go to **System -> Preferences -> Screensaver** and **Activate screensaver when computer is idle** is disabled. I click on **Power Management** and both options are set to **Never**. In contradiction to these settings, my screen goes black after 10 mins of idle time. It goes black, but doesn't go in standby. Why?? Could it be that I have Beryl installed? Maybe beryl has its own screensaver and I don't know about it? Help!

---

### Post by baka_rob on 2007-05-13
If the screensaver should never be active at all, you may want to look for any stray screensaver processes:

user@shellprompt$ ps aux | grep screensaver
user    pid  0.0  0.5   5932  2476 ?        S    10:58   0:00 xscreensaver -nosplash

Then you could xscreensaver-command -kill to get rid of the daemon.  It may not persist through reboot (xscreensaver will probably restart when the computer does), but if it works it's a step in the right direction.

You may also be able go back to the screensaver preferences and do a File -> Kill Daemon, but I'm apparently on a different version of ubuntu, as my options are different on that screen.

---

### Post by m.musashi on 2007-05-13
I am unable to reproduce the same problem. When I deselect "activate screensaver when computer is idle" my screensaver does not activate (I have mine set to blank screen). I am also running beryl so I don't think it's related unless you activated something in beryl that I didn't.

What version of ubuntu are you using? I'm on feisty so it could be a bug in an older version that was fixed.

You could just change the time from 10 mins to 2 hours (max on my system). That would also be a good way to check if it's the screensaver or something else. If you set it to 2 hours and it still goes black after 10 mins then something else is the culprit.

---

### Post by Znupi on 2007-05-13
I'm on feisty, too.

The time is set to 30 mins, but in 10 mins it goes black (although it's set to the GLMatrix screensaver).

I used **System Monitor** and there was indeed a process named **gnome-screensaver**. I killed it. I thought this was strange since this problem occured even after rebooting. After killing it I rebooted but it started again.

Anyway, I'll test to see if it starts again after killing that process... I'll let you know :)

---

### Post by Znupi on 2007-05-14
Nope, it still happens, screen goes black after 10 minutes or so. I have no idea why, I'm baffled.

---

### Post by mcduck on 2007-05-14
Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```

---

### Post by m.musashi on 2007-05-14
> **Znupi said:**
> I'm on feisty, too.

The time is set to 30 mins, but in 10 mins it goes black (although it's set to the GLMatrix screensaver).

I used **System Monitor** and there was indeed a process named **gnome-screensaver**. I killed it. I thought this was strange since this problem occured even after rebooting. After killing it I rebooted but it started again.

Anyway, I'll test to see if it starts again after killing that process... I'll let you know :)

Any process that is auto loading, and the screen-saver is probably one, will load again after a reboot. You will have to stop it from auto loading if you don't want to kill it each time you boot. However, I'm not sure how to do that. I know you can add stuff under system -> admin -> sessions and I think there are some things there you can remove too. I'm not sure if screen-saver is one (on windows at work at the moment - blah).

However, I don't think it's your screen-saver. If it goes black after 10 mins but the screen-saver is set to 30 then something else is the cause. Maybe the bug mcduck mentions.

---

### Post by Znupi on 2007-05-14
> **mcduck said:**
> Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```
Thanks, that did it :)

---

