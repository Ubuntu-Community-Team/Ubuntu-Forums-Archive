---
title: "[SOLVED] /etc/rc.local not being read"
date: 2007-08-22
forum: General Help
---

### Post by legatek on 2007-08-22
Hello,

I am using a laptop to run Folding@Home and, as suggested by the [F@H Wiki link]("https://help.ubuntu.com/community/FoldingAtHome#head-353ddb49ec5a97223b3e0f1be7d8a7acfab7f59e")  I have modified my /etc/rc.local file to keep my cpu temperature down. The problem is, the fix is not working when I reboot my computer. If I enter the code at the command line my cpu responds immediately by cooling down, but it appears my rc.local is not being read during boot, and F@A clobbers my processor until I input the following line from my rc.local file:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
exit 0
```

The rc.local file is executable and (of course) owned by root. Have I done anything wrong?

---

### Post by ruibernardo on 2007-08-22
Hi legatek,

check if the boot process, and /etc/rc.local execution is completed with success and without any [Fail] message by pressing Alt+Ctrl+F8.

---

### Post by legatek on 2007-08-23
I get no fail messages, but the boot process is not completed. After

```
...
* Checking battery state [OK]
* Starting Folding@Home client 1 [OK]
* Running local boot scripts (/etc/rc.local) [OK]
```

it just hangs. I have to use Ctrl-Alt-Del to restart.

---

### Post by legatek on 2007-08-23
I managed to solve this issue by appending the following directly to the end of /etc/init.d/rc.local:

```
sleep 20 && echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
exit 0
```

previously I tried adding sleep 5 prior to the echo statement in /etc/rc.local, and that did nothing, nor did simply adding the echo statement to /etc/init.d/rc.local. It seems increasing the sleep time did the trick.

---

