---
title: "CPU Scaling problem"
date: 2007-04-23
forum: General Help
---

### Post by hormati on 2007-04-23
Hi all,
I just updated from edgy to feisty. I had cpu frequency scaling all set up in edgy. I had added 
echo -n "conservative" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
in my bootmisc.sh. So, after boot "conservative" was my scaling governor. In fiesty my problem is that whatever I do my scaling governor reverts to "ondemand". I can change it by hand to "conservative" but after reboot, or after I unplug or plug the AC, it just goes back to "ondemand". 

I do not have powernow or cpudyn installed. I have laptop mode(it is enabled in acpi-support), and I changed the following lines:
CONTROL_CPU_FREQUENCY=1

BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=conservative
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=conservative
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=conservative

So, there is nothing in there about ondemand. I am completely clueless. I do not know what is changing my scaling governor to ondemand. Any ideas?

one more thing, my laptop-mode status says that my laptop-mode is started and running.
Thanks,
Amir

---

### Post by mhansen on 2007-04-23
I'm far from an expert on SysV init scripts, having used Slackware exclusively for the past 12 years, but looking through my system, I saw no symlink in /etc/rc2.d that pointed to /etc/init.d/bootmisc.sh.  Unless you made this link on your system, that script is never being run, therefore the change you want is never being made.  So you can either make the symlink yourself, sudo ln -s /etc/init.d/bootmisc.sh /etc/rc2.d/S50bootmisc, for example, or just edit the /etc/rc.local file and place the command you wish to run in it (my personal preference).



Regards,
Mike

---

