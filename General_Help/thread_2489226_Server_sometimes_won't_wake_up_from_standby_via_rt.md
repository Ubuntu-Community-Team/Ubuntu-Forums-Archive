---
title: "Server sometimes won't wake up from standby via rtcwake"
date: 2023-07-22
forum: General Help
---

### Post by pagano231 on 2023-07-22
Hello everyone,

I've got a bit of a problem with the standby mode on my ubuntu machine. I'm using the following crontab-entry to put the machine into standby and wake it up later on:

```

00 05 * * * sudo rtcwake -m mem -l -t $(date +\%s -d "today 13:30")

```  
The problem is that the system sometimes won't wake up properly. The machine is turning on, but the OS doesn't seem to start. All I'm getting is a black screen and it doesn't react to keyboard/mouse inputs. Connecting via SSH or xrdp didn't work either. I then have to press and hold the power button to shut the PC down.

After that, once the cron job is triggered again, the PC will go to standby & wake up at least once just fine. Then it's going back to black screens.

Anyone got an idea what the problem might be?

Some hardware specs:
CPU: AMD Ryzen 5600g
Mainboard: Gigabyte B450 AORUS M
RAM: 32GB Crucial Ballistix Sport LT

---

### Post by MAFoElffen on 2023-07-23
What is the value of these 2 queries?:
```

mafoelffen@opti-ubuntu:~$ grep . /sys/module/*_idle/parameters/max_cstate
9

mafoelffen@opti-ubuntu:~$ ls /sys/module/*_idle/parameters/max_cstate | awk -F "/" '{print $4}'
intel_idle

```
This is on my workstation with an AMD
```

mafoelffen@opti-ubuntu:~$ grep -i -m1 'name' /proc/cpuinfo
model name    : AMD Opteron(tm) Processor 6386 SE

```
I agree that it doesn't make sense that it says "intel_idle" in the sysfs, But it is what it is...

Here is the deal... The CPU has states that it can be set to, when it gets sent to hibernation or sleep. Your Ryzen can set set down to 9...

Look at this table:
[IMG]https://metebalci.com/img/blog/processor-ia-core-package-state-support-table-4-2.png[/IMG]
 
If, in the grub "GRUB_CMDLINE_LINUX_DEFAULT" boot line of /etc/default/grub, you add "intel_cstate.max_cstate=4"... Then do update-grub to pick up the changes...

Then it will limit how far it can go to sleep, without powering it down completely... Or rather too far to respond to wakeup.

That setting seems to help with wakeup problems.

---

### Post by pagano231 on 2023-07-24
> **MAFoElffen said:**
> What is the value of these 2 queries?:
```

mafoelffen@opti-ubuntu:~$ grep . /sys/module/*_idle/parameters/max_cstate
9

mafoelffen@opti-ubuntu:~$ ls /sys/module/*_idle/parameters/max_cstate | awk -F "/" '{print $4}'
intel_idle

```

Same as yours, "9" and "intel_idle".

> **MAFoElffen said:**
> 
I agree that it doesn't make sense that it says "intel_idle" in the sysfs, But it is what it is...

Here is the deal... The CPU has states that it can be set to, when it gets sent to hibernation or sleep. Your Ryzen can set set down to 9...

If, in the grub "GRUB_CMDLINE_LINUX_DEFAULT" boot line of /etc/default/grub, you add "intel_cstate.max_cstate=4"... Then do update-grub to pick up the changes...

Then it will limit how far it can go to sleep, without powering it down completely... Or rather too far to respond to wakeup.

That setting seems to help with wakeup problems.
I'll give it a try, thank you.

Though I still don't understand why this whole rtcwake-thing works perfectly fine the very first time after a cold boot, but the second time it somehow gets stuck during boot. 
cold boot -> sleep/hibernate via rtcwake -> waking up the first time -> no problems -> sleep/hibernate via rtcwake -> waking up, but unresponsive/black screen

---

