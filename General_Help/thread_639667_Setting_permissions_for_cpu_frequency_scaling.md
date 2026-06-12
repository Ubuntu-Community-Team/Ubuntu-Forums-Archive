---
title: "Setting permissions for cpu frequency scaling"
date: 2007-12-13
forum: General Help
---

### Post by akudewan on 2007-12-13
Hello,

I'm trying to (unsuccessfully) set permissions for allowing me (as normal user "akudewan") to set cpu frequency scaling.

I have 2 scripts with me: setondemand.sh and setperformance.sh. I have created a group called "cpufreqs". "akudewan" and root belong to this group. I changed the group of setondemand.sh and setperformance.sh to "cpufreqs"
```

akudewan@ranjan404:~ $ ls -lh /usr/local/bin/setondemand.sh && cat /usr/local/bin/setondemand.sh
-rwxr-xr-x 1 root cpufreqs 84 2007-12-13 22:50 /usr/local/bin/setondemand.sh
#!/bin/sh
echo ondemand | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor


akudewan@ranjan404:~ $ ls -lh /usr/local/bin/setperformance.sh && cat /usr/local/bin/setperformance.sh
-rwxr-xr-x 1 root cpufreqs 87 2007-12-13 22:49 /usr/local/bin/setperformance.sh
#!/bin/sh
echo performance | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

I've also changed the group of all files in /sys/devices/system/cpu/cpu0/cpufreq to cpufreqs, (with write access wherever root had it)
```


akudewan@ranjan404:/sys/devices/system/cpu/cpu0/cpufreq $ ls -lhR
.:
total 0
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 affected_cpus
-r-------- 1 root cpufreqs 4.0K 2007-12-13 23:09 cpuinfo_cur_freq
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 cpuinfo_max_freq
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 cpuinfo_min_freq
drwxr-xr-x 2 root cpufreqs    0 2007-12-13 23:27 ondemand
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_available_frequencies
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_available_governors
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_cur_freq
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_driver
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 22:49 scaling_governor
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_max_freq
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 scaling_min_freq
drwxr-xr-x 2 root cpufreqs    0 2007-12-13 23:09 stats

./ondemand:
total 0
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 ignore_nice_load
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 powersave_bias
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 sampling_rate
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 sampling_rate_max
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 sampling_rate_min
-rw-rw-r-- 1 root cpufreqs 4.0K 2007-12-13 23:27 up_threshold

./stats:
total 0
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 time_in_state
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 total_trans
-r--r--r-- 1 root cpufreqs 4.0K 2007-12-13 23:09 trans_table

```

Inspite of this, when I run any of the two scripts, I get:
```

tee: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied
ondemand (or performance)

```

Am I doing something wrong? Do I need to do something else ?

Thanks!

---

### Post by bingoUV on 2007-12-13
Give permissions to the user to run a specific command as root without password by editing your /etc/sudoers file. Like this [http://ubuntuforums.org/showpost.php?p=3768173&postcount=7](http://ubuntuforums.org/showpost.php?p=3768173&postcount=7)

---

### Post by akudewan on 2007-12-14
Thanks, will look into that

---

### Post by dagnabit dang doohickey on 2007-12-14
cpufreq-set may be the command which you want to give sudo permissions.
```
cpufreq-set -g ondemand
cpufreq-set -g performance
```

---

