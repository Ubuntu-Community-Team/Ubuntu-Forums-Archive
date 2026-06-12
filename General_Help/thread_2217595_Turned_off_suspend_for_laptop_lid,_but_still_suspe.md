---
title: "Turned off suspend for laptop lid, but still suspends when shut"
date: 2014-04-18
forum: General Help
---

### Post by cbraxton on 2014-04-18
I just updated my Lenovo G555 laptop to Xubuntu 14.04 from 12.04 via clean install. Overall it is working well but I'm having an issue with the power management settings. In the Power Manager, in the "On AC" section I selected "nothing" as the action to take when closing the lid. However when the lid is closed the system still suspends. Setting the "On Battery" section the same way has the same result, the laptop still suspends when the lid is closed.

I am aware of the *"Xfce4 Power Manager does not restore screen power"* bug documented in the release notes, and this does indeed occur when the laptop wakes up. However it should not be suspending in the first place. It's not clear if the "nothing" setting not working is related to the screen power problem. Anyone else experiencing this and have some insight?

---

### Post by Toz on 2014-04-18
This issue was fixed through the testing cycle (see: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021")) but seems to have resurfaced. I have created a new regression bug report (see: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1309551]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1309551")). Feel free to note in the bug report that it affects you as well.

A temporary workaround is to change:
> #HandleLidSwitch=suspend
...in /etc/systemd/logind.conf to read:
```
HandleLidSwitch=ignore
```
...to allow the xfce4-power-manager settings to take precedence. Reboot required.

---

### Post by cbraxton on 2014-04-18
Thanks for the info. I tried making the change to logind.conf and rebooting, but the problem persists. It's annoying, but I don't want to go back to 12.04 just because of this, will just have to just live with it until it's fixed.

---

### Post by Toz on 2014-04-18
> **cbraxton said:**
> Thanks for the info. I tried making the change to logind.conf and rebooting, but the problem persists. It's annoying, but I don't want to go back to 12.04 just because of this, will just have to just live with it until it's fixed.

Can you post back the contents of your /etc/systemd/logind.conf file?

---

### Post by cbraxton on 2014-04-18
> **Toz said:**
> Can you post back the contents of your /etc/systemd/logind.conf file?[

Sure, here it is:
```

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
Controllers=blkio cpu cpuacct cpuset devices freezer hugetlb memory perf_event
ResetControllers=
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
HandleLidSwitch=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleAction=ignore
#IdleActionSec=30min

```

I'm not 100% certain that the system is going into full suspend now when the lid is closed, it may just be turning off the monitor. (It seems to come back faster after opening the lid back up, but the monitor still turns off after entering the password.)

---

### Post by Toz on 2014-04-18
> I'm not 100% certain that the system is going into full suspend now when the lid is closed, 
To confirm whether the system goes into suspend or not, have a look at /var/log/pm-suspend.log. If there are no entries with a timestamp of when you closed the lid, then it did not suspend.
> but the monitor still turns off after entering the password.
This is another current bug with light-locker. See :[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1303736"). There is a workaround in the bug report involving mapping an xrandr command to a keyboard shortcut so it resets the display.

---

### Post by cbraxton on 2014-04-18
There is no /var/log/pm-suspend.log, only pm-powersave.log, so it looks like the system is not suspending, the monitor now is apparently just shutting off and the system asks for a password when the lid is opened back up, after which the monitor is turned off again. (Is there a setting to disable asking for the password?)

I used the keyboard shortcut approach in the link you provided and that works to turn the monitor back on. Then it is necessary to switch to a virtual console and back to get the mouse cursor working again. So at least there is a workaround, albeit a clumsy one. Hopefully this will be fixed soon as it is a pretty aggravating problem for laptop users.

Thanks for the help, it is much appreciated!

---

### Post by cbraxton on 2014-04-18
Found another interesting thing - if the screen saver (xscreensaver) kicks in, the problem doesn't happen. So I set up a keyboard shortcut to run "xscreensaver-command -activate" and just run this before closing the lid.

---

### Post by Toz on 2014-04-18
Yes, xscreensaver is not affected by the blank screen problem. If you've upgraded, you've probably got both xscreensaver and light-locker installed and running. You could disable light-locker:

1. Settings Manager -> Session and Startup -> Application Autostart, and uncheck the light-locker entry.
2. Then kill the light-locker process:
```
pkill light-locker
```
This way, only xscreensaver will work and it will run that command for you by default.

---

### Post by cbraxton on 2014-04-18
Excellent, having done that I can now just close and open the lid without having to take any manual action. Best workaround by far for this problem, thanks!

---

