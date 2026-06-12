---
title: "Issue with Ubuntu since 18.00"
date: 2020-07-21
forum: General Help
---

### Post by amiga500 on 2020-07-21
Hey guys,

I have one frustrating issue with Ubuntu even from older version, I am using the latest version of Ubuntu now but the issue remains the same. I have installed Ubuntu in a laptop, naturally when I close the screen lid Ubuntu immediately enters sleep mode. That is good so far. When I open the screen lid it wakes up, asks me to enter the password to login in, I do. Whether I enter the password or not Ubuntu re-enters into suspend mode forcing me to press the power button again, wake Ubuntu, then back to the login screen. I have to enter the password again before it remains awake. How do I fix the issue where after you open the screen lid and Ubuntu wakes up it goes back to sleep again to re-awake it up again before you can use it normally again?

Any help on this would be greatly appreciate it.

---

### Post by crip720 on 2020-07-22
Do you require needing password on wake,  does problem remain if password not required on wake?

---

### Post by TheFu on 2020-07-22
I'd check the system log files. Appears there are 2 events happening, both require entering a password.  Some possible settings:
[LIST]
[*]Password on wake
[*]Password on sleep
[*]Password after inactivity
[*]Screen saver password
[/LIST]

I'd check the settings for each of those.  Remember that the clock would jump as far as the frozen/unfrozen OS is concerned.

For example, if the screen saver only happens after 30 minutes, then putting the system to sleep, then waking it up in a minute wouldn't hit the threshold of the screen saver.

On my 16.04 systems with fvwm as the Window manager, I only get prompted once for a password when coming out of sleep and only if the screen saver had engaged due to the time passed.

---

### Post by amiga500 on 2020-07-30
It is not that it requires multiple password for password on wake, sleep, after inactivity and screen saver password it is that when I wake it up the HD goes busy to wake up then goes busy again to enter sleep mode again to wake it up again in order to stay awake. Every time I wake it up it goes to sleep again and I have to wake it up again in order to remain awake. That is my frustration.

---

