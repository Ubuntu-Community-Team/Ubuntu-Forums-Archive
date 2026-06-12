---
title: "Blank screen after closing and opening laptop lid"
date: 2014-10-29
forum: General Help
---

### Post by DiscoDave95 on 2014-10-29
Every now and then (often  after sitting for a while with the lid close), after closing and reopening the laptop lid the screen is all black. If I use the keyboard shorcuts to switch to another workspace and close/open the lid again it will return back to the desktop as normal. I am using Xubuntu 14.04. I have uninstalled Light-Locker, and in the xfce-power-manager I have it marked to do nothing when lid is closed in on both AC and battery.

My /etc/systemd/logind.conf

```
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# See logind.conf(5) for details

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
Controllers=blkio cpu cpuacct cpuset devices freezer hugetlb memory perf_event net_cls net_prio
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

I have also tried exiting the power manager and running this code.
```
 xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/logind-handle-lid-switch -s true


```

However this did not fix my problem. Anyone with any insight on how I may fix this, would be lovely.
Thanks in advanced to anyone that can help.

---

### Post by jhay2 on 2014-10-29
i actually fix my problem with this by changing lightdm-gtk-greeter to lightdm-webkit-greeter . it might work also with you .. :)

---

### Post by DiscoDave95 on 2014-10-29
I was able to replace lightdm-gtk-greeter with lightdm-webkit-dm, and as of now it seems to be working. Hopefully it stays working

Thanks a lot mate.

---

### Post by jhay2 on 2014-10-31
im glad that its working too for you :)

it seems that lightdm-gtk-greeter has an issue on buntu's 14.04 disto

---

