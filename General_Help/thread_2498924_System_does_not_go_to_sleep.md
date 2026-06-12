---
title: "System does not go to sleep"
date: 2024-07-03
forum: General Help
---

### Post by xxi on 2024-07-03
I am running Ubuntu 24.04 LTS on a Lenovo IdeaPad Pro 5 with an NVidia GeForceRTX 4050.

The system details says my firmware version is MECN63WW and kernel version Linux 6.8.0-36-generic.

Recently (like within the last two weeks) my system stopped going to sleep after a set amount of time (I believe the setting related to this is under power-->power saving-->Screen blank). To put it another way, no matter how long my computer sits without being used, it does not turn the screen off or lock the computer.

I've searched to see if anyone else was having this issue and haven't really found anything. Closest post I found was this askubuntu post [https://askubuntu.com/questions/1391976/ubuntu-20-04-suspend-logs-off-and-wakes-up/1393726#1393726](https://askubuntu.com/questions/1391976/ubuntu-20-04-suspend-logs-off-and-wakes-up/1393726#1393726)

I'm not really even sure where to begin with troubleshooting this issue so any help or guidance would be really appreciated!

---

### Post by TheFu on 2024-07-04
Beyond what is said here: [https://help.ubuntu.com/stable/ubuntu-help/power.html.en](https://help.ubuntu.com/stable/ubuntu-help/power.html.en)
I have no clue.

---

### Post by xxi on 2024-07-05
Thanks for the suggestion. Further digging has not resulted in anything.  But I think I can say this is an issue related to "Screen blank" or  rather, Screen blank not working. My point is, if I manually make the  system suspend it will, also when I close the lid of the laptop it  suspends, so I don't think this is an issue with suspend. The primary issue I am having is that regardless of how long  the system is idle, the screen never turns off and the system remains  unlocked.

---

### Post by currentshaft on 2024-07-05
What window manager are you using? Have you tried another one?

---

### Post by TheFu on 2024-07-05
Lenovo  almost always has their own firmware modules and their own power management tools. Have you loaded those? Are they not working?

I found a few posts about power management on lenovo forums, but since they require javascript, I wasn't willing to enable that just to read it. Anyway, here's 1 link: [https://forums.lenovo.com/t5/Ubuntu/lenovo-energy-manager-for-ubuntu/td-p/2031094](https://forums.lenovo.com/t5/Ubuntu/lenovo-energy-manager-for-ubuntu/td-p/2031094)

I don't think window managers have anything to do with power management.  To my knowledge, either there will be a hardware specific tool or the settings in /etc/systemd/logind.conf   which have a nice manpage, should work.  Of course, not all hardware is well supported, but Lenovo generally is.

---

