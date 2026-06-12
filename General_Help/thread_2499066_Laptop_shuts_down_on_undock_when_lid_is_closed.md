---
title: "Laptop shuts down on undock when lid is closed"
date: 2024-07-10
forum: General Help
---

### Post by asdfasdfasdf123 on 2024-07-10
Hello!
I've recently switched to Ubuntu 24.04 from Windows 11.

I'm experiencing a weird bug though: When undocking (usb-c dock) while the lid is closed, the computer shuts down (not hibernate, it really shuts down). 
At most, it should go to sleep since that's what it does if I close the lid while undocked.

If I close the lid while unplugged, it sleeps. If I close the lid  while on power but not docked, it sleeps. If I close the lid while on  power and docked (dock can't supply enough power through usb-c so I need  external power) it does nothing except turn of the internal screen.
So each individual state works, but the transition from docked to undocked with the lid closed for some reason causes a shutdown.

This behaviour was not present on Windows so I don't believe it's a hardware issue.

Laptop is a Lenovo Legion Slim 5, with AMD CPU+GPU and discrete Nvidia GPU. 
Ubuntu 24.04 LTS, kernel 6.8.0-36-generic.

The problem seems similar to this kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=108801](https://bugzilla.kernel.org/show_bug.cgi?id=108801)
But not quite identical.

I've tried looking at journalctl but it looks like it suspends properly and then suddenly boots:

```

jul 10 14:44:20 erik-Legion-Slim-5-16APH8 systemd[1]: nvidia-suspend.service: Deactivated successfully.
jul 10 14:44:20 erik-Legion-Slim-5-16APH8 systemd[1]: Finished nvidia-suspend.service - NVIDIA system suspend actions.
jul 10 14:44:20 erik-Legion-Slim-5-16APH8 systemd[1]: Starting systemd-suspend.service - System Suspend...
jul 10 14:44:20 erik-Legion-Slim-5-16APH8 systemd-sleep[56233]: Performing sleep operation 'suspend'...
jul 10 14:44:20 erik-Legion-Slim-5-16APH8 kernel: PM: suspend entry (s2idle)
-- Boot d7aa4d044bb24d76957b76979ee67141 --
jul 10 14:45:03 erik-Legion-Slim-5-16APH8 kernel: Linux version 6.8.0-36-generic (buildd@lcy02-amd64-077) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-23ubuntu4) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.42)>
jul 10 14:45:03 erik-Legion-Slim-5-16APH8 kernel: Command line: BOOT_IMAGE=/vmlinuz-6.8.0-36-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro quiet splash vt.handoff=7

```

Anyone seen anything similar or know where I should look?

---

### Post by 0f4d0335 on 2024-07-10
Have you tried changing your lid behavior? This thread could help: [https://ubuntuforums.org/showthread.php?t=2475520](https://ubuntuforums.org/showthread.php?t=2475520)

Modify this file: 

/etc/systemd/logind.conf

with nano or any editor.

I found this article very helpful: [https://fostips.com/lid-close-action-ubuntu-21-04-laptop/](https://fostips.com/lid-close-action-ubuntu-21-04-laptop/)

---

### Post by currentshaft on 2024-07-10
This script by Intel helps diagnose Linux sleep issues: [https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh)

---

### Post by asdfasdfasdf123 on 2024-07-10
> **0f4d0335 said:**
> Have you tried changing your lid behavior? This thread could help: [https://ubuntuforums.org/showthread.php?t=2475520](https://ubuntuforums.org/showthread.php?t=2475520)

Modify this file: 

/etc/systemd/logind.conf

with nano or any editor.

I found this article very helpful: [https://fostips.com/lid-close-action-ubuntu-21-04-laptop/](https://fostips.com/lid-close-action-ubuntu-21-04-laptop/)

I've tried that already. But as I said the individual states work fine already!
The laptop sleeps if I close the lid while undocked.
The laptop does nothing (except turn of the internal screen) if I close the lid when docked.

However, when going from docked to undocked with the lid closed causes it to shutdown. No setting in logind.conf says shutdown so I have no idea where it comes from.

---

### Post by asdfasdfasdf123 on 2024-07-10
> **currentshaft said:**
> This script by Intel helps diagnose Linux sleep issues: [https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh)

Is that supposed to work on AMD CPUs?

I get a bunch of errors that I'm unsure if they are because I don't have Intel or something else:

```

root@erik-Legion-Slim-5-16APH8:/tmp# ./sleeptest.sh -s

---Check S2idle path S0ix Residency---:

The system OS Kernel version is:
Linux erik-Legion-Slim-5-16APH8 6.8.0-36-generic #36-Ubuntu SMP PREEMPT_DYNAMIC Mon Jun 10 10:49:14 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

---Check whether your system supports S0ix or not---:

Low Power S0 Idle is:1
Your system supports low power S0 idle capability.



---Check whether intel_pmc_core sysfs files exit---:
ls: cannot access '/sys/kernel/debug/pmc_core': No such file or directory

The pmc_core debug sysfs file is empty on your system.
Isolation suggestions:     
Please check whether intel_pmc_core driver is loaded.


The intel_pmc_core sysfs missing will impact S0ix failure analyze.


---Judge PC10, S0ix residency available status---:
cat: /sys/kernel/debug/pmc_core/substate_residencies: No such file or directory
grep: /sys/kernel/debug/pmc_core/substate_residencies: No such file or directory
Test system does not support S0ix.y substate

The system failed to place S2idle entry command by turbostat,     
please check if the suspend is failed or turbostat tool version is old     
e.g. did you make turbostat tool executable or separately run S2idle command:     
rtcwake -m freeze -s 15


```

---

### Post by asdfasdfasdf123 on 2024-07-10
Okay, I got the Intel script to go further by symlinking turbostat to the local directory but I have no idea how to read the output.

There were no obvious errors at least. Am I looking for anything in particular?

---

