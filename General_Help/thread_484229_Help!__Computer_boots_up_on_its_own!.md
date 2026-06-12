---
title: "Help!  Computer boots up on its own!"
date: 2007-06-25
forum: General Help
---

### Post by rygar on 2007-06-25
Recently I have been having a major issue with Ubuntu on my laptop and I don't know why.

If I turn my laptop off, after about 5 minutes, the computer reboots on its own!
This happens regardless of whether it is plugged into the AC or not.  It also happens regardless of what method I use to turn it off--hibernate, shut down, close lid, etc.

I literally cannot shut down from Ubuntu and leave my computer off unless I take out the battery, or let it drain completely.  If I boot up into Windows (I use GRUB), and shut down from there, it remains off.

I don't even know how the computer can tell itself to turn on when it is completely off with no AC power!

HELP! :(

Thanks,
Jeff

---

### Post by Metacarpal on 2007-06-25
Did the computer just recently start doing this?  Have you made any changes to your system, such as installing new software?

If the computer is powering on, on its own, from a completely shut-down state, that sounds like it may have more to do with your BIOS than your operating system...

---

### Post by eggdeng on 2007-06-25
Try adding
```
apm power_off=1
```
to the /etc/modules file.

---

### Post by rygar on 2007-06-25
Yes, it started happening recently...  But to be honest I haven't been using my laptop much recently, so I don't really know what I installed that could be causing the problem.

It's not the BIOS, or else the same thing would happen when I shut down from Windows.

Will try adding that line to my modules file and let you know the results.

Thanks!
Jeff

---

### Post by rygar on 2007-06-25
it probably has something to do with the "omnibook" module i installed.  i just noticed when i went to edit /etc/modules, the file consisted of one line that says "omnibook"

i installed it so that i could change the brightness on my lcd when its running on battery power.  and i just noticed, its not working anymore.

---

### Post by rygar on 2007-07-01
i tried adding that line to my modules file and it didnt help

i also removed the omnibook module from loading and that didn't help either.

if it helps, i noticed that sometimes when i try to start up my computer it hibernates immediately, and i have to boot it up again.

any other ideas?

---

### Post by eggdeng on 2007-07-01
I think this has got to be a power management problem. Try disabling it by following the instructions at
[http://ubuntuforums.org/showthread.php?t=187967](http://ubuntuforums.org/showthread.php?t=187967)

---

### Post by rygar on 2007-07-01
i installed boot-up manager.  neat application, but it doesn't list ACPI or APM or anything (even though ACPI does start with my computer)

ideally, id like to keep ACPI running so i can continue to hibernate.

i think it has something to do with /boot/config-2.6.20-16-generic file

here are part of the contents that i think may be relevant, i was hoping maybe someone would know what i should change or what shouldnt be there?  or maybe post your file so i can compare?

thanks!

```
#
# Power management options (ACPI, APM)
#
CONFIG_PM=y
CONFIG_PM_LEGACY=y
CONFIG_PM_DEBUG=y
# CONFIG_DISABLE_CONSOLE_SUSPEND is not set
CONFIG_PM_TRACE=y
CONFIG_PM_SYSFS_DEPRECATED=y
CONFIG_PM_DISABLE_CONSOLE=y
CONFIG_SOFTWARE_SUSPEND=y
CONFIG_PM_STD_PARTITION=""
CONFIG_SUSPEND_SMP=y

#
# ACPI (Advanced Configuration and Power Interface) Support
#
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_SLEEP_PROC_FS=y
CONFIG_ACPI_SLEEP_PROC_SLEEP=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_HOTKEY=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_DOCK=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_IBM=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_CUSTOM_DSDT_INITRD=y
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=m
CONFIG_ACPI_SBS=m

#
# APM (Advanced Power Management) BIOS Support
#
CONFIG_APM=m
# CONFIG_APM_IGNORE_USER_SUSPEND is not set
# CONFIG_APM_DO_ENABLE is not set
# CONFIG_APM_CPU_IDLE is not set
# CONFIG_APM_DISPLAY_BLANK is not set
# CONFIG_APM_RTC_IS_GMT is not set
# CONFIG_APM_ALLOW_INTS is not set
# CONFIG_APM_REAL_MODE_POWER_OFF is not set

```

---

### Post by eggdeng on 2007-07-01
```
i installed boot-up manager. neat application, but it doesn't list ACPI or APM or anything
```
Suspect this is because acpid is not running. Try  ```
ps -A | grep acpid
``` If you get no output (you should see something like
 ```
  16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpid-work-0
 4337 ?        00:00:00 acpid
```
), then it's not running. Dunno, maybe you should download the latest version from [https://sourceforge.net/project/showfiles.php?group_id=33140](https://sourceforge.net/project/showfiles.php?group_id=33140)
I'm not running the same kernel as you but I've compared your boot.config file with versions on two different boxes and I can't see any significant differences.

---

### Post by rygar on 2007-07-02
actually, acpid is already installed :(

```
   31 ?        00:00:00 kacpid
 4476 ?        00:00:00 acpid

```

thanks for trying to help, i do appreciate it

any other ideas though?

---

### Post by vmikalinis on 2007-07-02
Could it be some kind of wake on lan thing?

---

