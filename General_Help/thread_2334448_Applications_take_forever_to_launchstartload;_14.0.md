---
title: "Applications take forever to launch/start/load; 14.04, SSD, they were fine earlier."
date: 2016-08-19
forum: General Help
---

### Post by franciscoam on 2016-08-19
Hi, people,

From a couple days to now, my apps are taking forever to launch. After the slowness, they open and run fast as expected. This behaviour began a couple of days ago. The only stuff I remember to do were updating the system as always (by accepting Ubuntu regular updates) AND setting up a Windows virtual machine (qemu/kvm was already installed and launching app speed was fine before using the VM). 

What I already did to face the issue (and didn't work):
1. Changed my session from Unity to Gnome;
2. Uninstalled QEMU/KVM/Libvirt and made sure that no instances were running by executing
```
virsh -c qemu:///system list
```
3. Did a TRIM command to check if there was something to do with the SSD by running
```
sudo fstrim -v /
```

Nothing solved the issue. System monitor shows a long time of 100% CPU usage when launching an app. After half a minute, another CPU shows 100% usage (as if the application launcher was retrying the operation or changing context). 

My system specs:
Haswell quad-i7, 10GB RAM, 128GB SSD (~50GB free).

---

### Post by banceu_sergiu_ione on 2016-08-19
If you think that QEMU/KVM/Libvirt could had change somehow your system settings then start control it.

Use ' cpupower ' for the cpu ( it must be installed first ). Check the governor ( default is ondemand ) and frequency scale, see if boost is active if you have any boost state. The command must be run as admin otherwise you wont get all the info. 

```
 sudo apt install cpupower 
```
```
 sudo cpupower frequency-info 
```

to activate a governor run

```
 sudo cpupower frequency-set -g governor 
``` governor = ondemand or powersafe or performance 

run turbostat via terminal ( must be installed first ) would give you all instant info about frequency and usage of all the cpu cores

For your SSD

Check if system still recognize your SSD, output 0  and 1 for hdd

```
 grep . /sys/block/sd?/queue/rotational 
```

Check scheduler
```
 cat /sys/block/sdX/queue/scheduler 
``` deadline is set as default.

You could also check if the direct rendering is active
```
 glxinfo | grep direct 
```

As I said, just in case you think that something might had changed your system setting. It should be all on default if you didn't changed anything. So this may not help you at all.

---

### Post by franciscoam on 2016-08-22
```
 sudo cpupower frequency-info 
```
```
sudo cpupower frequency-info
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 800 MHz - 3.20 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 800 MHz and 3.20 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 2.23 GHz (asserted by call to hardware).
  boost state support:
    Supported: yes
    Active: yes

```


Since the currently driver is "intel_pstate", I can only choose between performance and powersave governors. None of them solved the issue. Regarding the command ```
grep . /sys/block/sda/queue/rotational
``` the answer was "0" (SSD). So it seems that it's other problem. It's like a strange very high latency time when launching an application. After that, everything works fine.

---

### Post by banceu_sergiu_ione on 2016-08-22
Try run top, iotop, turbostat and monitor a bit your system, see how its  go. 
With top running, look for  load average, %cpu; *wa ,a hight value  is not good ( check man top for more info ). 
iotop is for I/O disk,  monitor the speed in rw and it gives you the app name too, or you can  use vmstat if like more. 
turbostat to have in time info about cpu, boost  stat if its go. 
You can run this while you run in a new terminal '  openssl speed ' to stress your system a bit and gather more info of how  its act.

Also, have you thought that this might be related to the last kernel upgrade ?

---

