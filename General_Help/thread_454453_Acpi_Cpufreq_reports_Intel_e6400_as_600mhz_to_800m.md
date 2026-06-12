---
title: "Acpi_Cpufreq reports Intel e6400 as 600mhz to 800mhz."
date: 2007-05-25
forum: General Help
---

### Post by zekard on 2007-05-25
Any ideas how to fix this problem? The cores should be running at 2.13ghz max, but acpi_cpufreq reports them as 800mhz max.

Here is some information regarding this problem:

Arch: i386
Kernel: 2.6.20-15

Motherboard Asus P5N SLI

Also there is an unconfirmed bug on launchpad the details this exact problem. 
(Bug #106447 in 2.6.20)

I've attachedthe output of cat/proc/cpuinfo and the output of cpufreq-info.

(dmesg was too big to upload but can be found on launchpad)

Thanks

---

### Post by zekard on 2007-05-25
Problem solved! I figured out how to correct this problem and still keep scaling. 

Here is what i did:

**Step 1: Remove Userspace Scaling Software**
```
sudo apt-get remove powernowd
```

**Step 2: Restart**
Acpi_cpufreq should no longer be loaded on startup and the processor(s) should be clocked at their full speed but without scaling support.

**Step 3: Manually load your CPU module**
I did
```

sudo modprobe acpi-cpufreq
```

**Step 4: Load Scaling Modules**

I was only interested in ondemand, but load the one(s) you need.

```

sudo modprobe cpufreq_ondemand
```

(others)

```

sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace
```

**Step 5: Testing/Configuration**

Show Available Governors
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

Select the governor you desire like so
```
sudo -s
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

**Step 6: Load Modules at Boot**
Append your selected modules to the end of /etc/modules
```

[Step 3 module]
[Modules from Step 4]
```

Mine was
```

acpi-cpufreq
cpufreq_ondemand
```

**Step 7: Configure Modules at Boot**
This step needs to be done in order for the modules to retain your settings.
Make sure you have sysfsutils installed 
```
sudo apt-get install sysfsutils
```

Then add the following lines to /etc/sysfs.conf
```

devices/system/cpu/cpu0/cpufreq/scaling_governor=ondemand
devices/system/cpu/cpu1/cpufreq/scaling_governor=ondemand

```

(If you have only one cpu then only the first line would apply)

**Step 8: Reboot and enjoy**
Hopefully everything should work now.

---

