---
title: "Hibernate, 15.10, 16.04, Unity, systemd, tlp, wifi module reload, tuxonice"
date: 2016-02-24
forum: General Help
---

### Post by KarlHegbloom on 2016-02-24
I thought I should share this in case anyone else has the similar problem and wants to know how to solve it. With the new systemd configuration, the Unity menu's "hibernate" option does not call on pm-hibernate. It instead uses the hibernate and sleep service of logind / systemd. I'm using a tuxonice kernel, and the tlp power management setup on a thinkpad w520, running Ubuntu 16.04 (devel). I think this article is still relevant even if you don't have tlp or tuxonice, since it's systemd that changes how suspend and hibernate work.

When this laptop suspends or hibernates, sometimes the wifi stops working when it wakes back up. The solution is to unload the wifi device driver module prior to sleep, and then reload it upon resume, the way the "hibernate" script does, and "pm-hibernate" also did.

/etc/systemd/system/wifi-modules-unload-reload.service
8<------------------------------------------------------------------------->8
# Unload and reload the wifi modules over suspend / resume.

[Unit]
Description=WIFI modules unload/reload over suspend/resume
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/sbin/modprobe -r iwldvm
ExecStop=/sbin/modprobe iwldvm

[Install]
WantedBy=sleep.target
8<------------------------------------------------------------------------->8

The other problem I had was that, using tuxonice, the user ui program was not visible during the hibernation process. I fixed this with:

/etc/systemd/system/tuxonice-vtswitch.service
8<------------------------------------------------------------------------->8
# Switch vt for tuxonice UI

[Unit]
Description=Switch VT for tuxonice UI
Before=sleep.target
StopWhenUnneeded=yes

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/bin/chvt 63 ; /bin/sh -c "/bin/echo -ne '\033%@' > /dev/tty63"
ExecStop=/bin/chvt 7

[Install]
WantedBy=sleep.target
8<------------------------------------------------------------------------->8

Enable them with:

sudo systemctl enable wifi-modules-unload-reload.service
sudo systemctl enable tuxonice-vtswitch.service

---

### Post by xmbwd on 2016-04-26
I just upgraded from 15.10 (which should have had the same problem because it uses systemd) to 16.04.  Doing so deleted some of the wake scripts that used to work.  I followed your instructions for the unload-reload script, and that didn't quite do it.  Even after a reboot.  

However, for some reason, doing the following after a reboot and a wake from suspend that failed (i.e., I suspended, then woke and the wifi was down with a "device not ready" error) seems to have worked:

```
sudo service network-manager restart
```

And it has stuck after multiple reboots and suspends.  Not sure if it is an actual solution, but I wanted to post it in case others encounter the same thing.

---

### Post by mayo2000 on 2016-10-12
So what is the correct replacement for /etc/pm/config.d/ scripts. In Ubuntu 14.04 I had one script there with:

> SUSPEND_MODULES="ath5k r8169"

Apparently like said in first post in 16.04 those scripts are not called and everything is somehow managed by systemd.

What is proper replacement for SUSPEND_MODULES and where should I put, because resume from suspend hangs with those two modules.

EDIT: I've found man page related to this ```
man systemd-sleep
```

> 
       Immediately before entering system suspend and/or hibernation systemd-suspend.service (and the other mentioned units, respectively) will run all executables in
       /lib/systemd/system-sleep/ and pass two arguments to them. The first argument will be "pre", the second either "suspend", "hibernate", or "hybrid-sleep" depending on
       the chosen action. Immediately after leaving system suspend and/or hibernation the same executables are run, but the first argument is now "post". All executables in
       this directory are executed in parallel, and execution of the action is not continued until all executables have finished.


EDIT2: Also arch [Power_management]("https://wiki.archlinux.org/index.php/Power_management#Sleep_hooks") wiki is very helpful.

EDIT3: Need more testing, but [following solution]("https://bbs.archlinux.org/viewtopic.php?pid=1540125#p1540125") seems viable:

1. create file ```
/lib/systemd/system-sleep/suspend-modules
``` with content:

```

#!/bin/bash

case $1 in
    pre)
        for mod in $(</etc/suspend-modules.conf); do
            modprobe -r $mod
        done
    ;;
    post)
        for mod in $(</etc/suspend-modules.conf); do
            modprobe $mod
        done
    ;;
esac

```

2. add execute permission

```

sudo chmod a+x /lib/systemd/system-sleep/suspend-modules

```


3. Create file ```
/etc/suspend-modules.conf
``` with one module per line, that should unloaded on suspend
In my case:

```

ath5k
r8169

```

---

