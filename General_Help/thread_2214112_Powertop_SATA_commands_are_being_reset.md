---
title: "Powertop SATA commands are being reset"
date: 2014-03-30
forum: General Help
---

### Post by necbot on 2014-03-30
I am trying to make the tuning settings on powertop permenant.  My /etc/pm/power.d/power script looks like this...
```

#!/bin/bash
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
echo min_power > /sys/class/scsi_host/host3/link_power_management_policy
echo min_power > /sys/class/scsi_host/host4/link_power_management_policy
echo min_power > /sys/class/scsi_host/host5/link_power_management_policy
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 0 > /proc/sys/kernel/nmi_watchdog
echo auto > /sys/bus/pci/devices/0000:00:1a.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:01.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:1d.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:1b.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:1f.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:1f.2/power/control
echo auto > /sys/bus/pci/devices/0000:00:16.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:14.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:00.0/power/control
echo auto > /sys/bus/pci/devices/0000:00:1f.3/power/control
echo auto > /sys/bus/pci/devices/0000:01:00.0/power/control
echo auto > /sys/bus/pci/devices/0000:01:00.1/power/control
```


All of these commands work fine except for the ones that set my SATA settings to min_power.  These commands are...

```
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
echo min_power > /sys/class/scsi_host/host3/link_power_management_policy
echo min_power > /sys/class/scsi_host/host4/link_power_management_policy
echo min_power > /sys/class/scsi_host/host5/link_power_management_policy
```

Whenever I restart my computer all the commands in the power script change the appropriate powertop tunings except for these six commands.  The only way I can get these commands to work is login, open a command prompt, and type...

```
sudo /etc/pm/power.d/power
```

Then the six commands do work and my SATA settings read "good" instead of "bad" in powertop.  This indicates to me that the script runs fine, but that somehow the SATA settings are either not working when this script is run automatically at startup, or that the script is run properly duing startup, but that something else downstream from this script resets the SATA settings.  Any ideas how I can fix this?   Thanks.

---

