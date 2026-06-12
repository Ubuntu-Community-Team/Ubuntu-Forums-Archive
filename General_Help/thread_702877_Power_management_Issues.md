---
title: "Power management Issues"
date: 2008-02-20
forum: General Help
---

### Post by lsutiger on 2008-02-20
This question has been raised many times on this forum, but no solution.

I have all the settings in the screensave/power management set to Never.

I have the screen saver set to start after 20 minutes.

My screen goes blank after 10 minutes. I can awake it by touching the mouse or keyboard.

What gives? Who else is having this issue? My laptop is in the sig.

Thanx in advance!

---

### Post by kiderjones on 2008-03-01
I'm having this problem.
Also, I can't change the workspaces at all. It remains at 2 columns and 1 row.
I do believe it's a compiz issue.

---

### Post by lsutiger on 2008-03-10
Bump

---

### Post by soldats on 2008-03-10
so do you want it to sleep after 20 minutes instead of 10 or sleep/turnoff never

edit:

if you open your xorg.conf file under the "ServerFlags" section you can add some lines to make it sleep after a preset amount of time. there are issues still with the power manager if i recall correctly. so a way for you to do a little research is like
```

man xorg.conf

```
 to view the man page.
there are a few options to input like blanktime offtime sleeptime etc. so you would add those to the serverflag section.

---

### Post by lsutiger on 2008-03-12
Thanx for the reply. I tried several different solutions (including editing my xorg file and adding relevant server flags) and still have the problem. 

Don't know what has happened, just know it is not working.
By the settings, the screen should never turn off. But it turns off before the screensaver starts. And no it is not a BIOS issue, FYI.

Thanx in advance

---

### Post by raven on 2008-03-13
this thing is driving me crazy

me too I'm experiencing same issue
my screensaver and power management are set to never

but still after 10min I get the screensaver,
when I watch a movie with totem or mplayer same issue 10min later and screensaver is on

cannot find solution till now

system:
gutsy amd64
gnome 2.20.1
Nvidia proprietary drivers
compiz on

---

