---
title: "commands in scripts are not working"
date: 2013-02-25
forum: General Help
---

### Post by pacman401 on 2013-02-25
I want to save some watts during usage of my laptop so i read that i must use these commands:
```
echo 5 > /proc/sys/vm/laptop_mode
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 3000 > /proc/sys/vm/dirty_writeback_centisecs
cpufreq-set -c 0 -g powersave
cpufreq-set -c 1 -g powersave
ethtool -s eth0 wol d
```

I had put these commands in to /etc/rc.local (no effect), /etc/sysctl.conf (no effect)

every time I log in I have to "sudo su" in terminal and insert upper commands 

btw I have compilled newest stable kernerl with CONFIG_SND_HDA_POWER_SAVE_DEFAULT set to 1  but that desn't help too

---

### Post by Doug S on 2013-02-25
During power up or re-boot there is a 1 minute delay before the CPUs are set to ondemand mode. I suspect your script runs before this time delay, and so your powersave settings get overwritten. see: /etc/init.d/ondemand
Perhaps you could delay your script longer with a sleep.
I don't know about your other commands.

---

### Post by matt_symes on 2013-02-25
Hi

> **Doug S said:**
> During power up or re-boot there is a 1 minute delay before the CPUs are set to ondemand mode. I suspect your script runs before this time delay, and so your powersave settings get overwritten. see: /etc/init.d/ondemand
Perhaps you could delay your script longer with a sleep.
I don't know about your other commands.

Yep. Bang on the money.

Maybe use a cron job @reboot with a sleep statement for 2 mins. Let the system settle down.

Thats the way i would do it.

Kind regards

---

### Post by pacman401 on 2013-02-25
let's forget on setting cpu to powersave mode (i recompiled kernel with powersave governor option and it is working     ...for now)
#########################update
f***** was working , after rebot i have mode ondemand :/


what about rest commands

btw delaying script start don't delay also reboot by that time ?

---

### Post by schragge on 2013-02-25
> **pacman401 said:**
> btw delaying script start don't delay also reboot by that time ?Well, if you specify it as @reboot in a crontab then it means *at the time the cron daemon starts*. You can put something like ```
COMMAND | at now + 5 minutes
``` to make COMMAND be executed 5 minutes after that. See [at(1)](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1.html)

---

### Post by matt_symes on 2013-02-25
Hi

> btw delaying script start don't delay also reboot by that time ?Just to clarify i would have the sleep statement the script i would call from cron at reboot.

Kind regards

---

### Post by pacman401 on 2013-02-25
> **Doug S said:**
> During power up or re-boot there is a 1 minute delay before the CPUs are set to ondemand mode.
how to disable it / where is config to change that ondemand mode ?

---

### Post by Doug S on 2013-02-25
see [this.]("http://ubuntuforums.org/showpost.php?p=12306229&postcount=8")

---

### Post by pacman401 on 2013-02-27
solved by
sudo sh -c 'echo <num> > <cmd>'
[http://askubuntu.com/questions/50242/why-does-echoing-these-parameters-with-sudo-not-work]("http://askubuntu.com/questions/50242/why-does-echoing-these-parameters-with-sudo-not-work")
thx every one for trying help

---

