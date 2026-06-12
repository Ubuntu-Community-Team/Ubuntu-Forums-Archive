---
title: "armhf issue with suspend"
date: 2013-08-15
forum: General Help
---

### Post by JoinTheRealms on 2013-08-15
Hey guys, Im running ubuntu 13.04 on my  Asus tf700 tablet

While everything is functioning correctly, we are having issues with suspend to ram.

The tablet appears to sleep and wake up with fine, the issue is the tablets screen stays blank (back light does come on)after waking the tablet up.  While an external display connected via hdmi wakes up fine? 

I really have no idea how to diagnose suspend issues, but i feel like this is something small. We are running the latest nivida drivers (linux for tegra)
heres /var/log/pm-suspend.log:
```
Initial commandline parameters: Sat Aug 10 14:54:18 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-hundsbuah-v3.2.0-oc+ #12 SMP PREEMPT Wed Aug 7 15:06:28 CST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
zram                    9656  4 
             total       used       free     shared    buffers     cached
Mem:        989080     764704     224376          0      26532     566728
-/+ buffers/cache:     171444     817636
Swap:       494528          0     494528


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
'SUSPEND' command timed out.


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_date: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/sys_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 225: ((: 0x10de ==  : syntax error: operand expected (error token is "==  ")
No quirk database entry for this system, using default.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
sysctl: cannot stat /proc/sys/kernel/acpi_video_flags: No such file or directory
vbetool not installed!
vbetool not installed!
vbetool not installed!
vbetool not installed!


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Aug 10 14:54:31 NZST 2013: performing suspend
Sat Aug 10 14:54:43 NZST 2013: Awake.
Sat Aug 10 14:54:43 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
vbetool not installed!
vbetool not installed!
vbetool not installed!
vbetool not installed!


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_date: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/sys_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
Saving last known working quirks: --quirk-vbe-post --quirk-dpms-on 
                            --quirk-dpms-suspend --quirk-vbestate-restore
                --quirk-vbemode-restore --quirk-vga-mode-3


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Aug 10 14:54:43 NZST 2013: Finished.
Initial commandline parameters: 
Sat Aug 10 15:07:21 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-hundsbuah-v3.2.0-oc+ #12 SMP PREEMPT Wed Aug 7 15:06:28 CST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
zram                    9656  4 
             total       used       free     shared    buffers     cached
Mem:        989080     766888     222192          0      26244     567820
-/+ buffers/cache:     172824     816256
Swap:       494528          0     494528


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/bios_date: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/sys_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/product_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_name: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_version: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 101: /sys/class/dmi/id/board_vendor: No such file or directory
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler: line 225: ((: 0x10de ==  : syntax error: operand expected (error token is "==  ")
Using last known working set of quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
sysctl: cannot stat /proc/sys/kernel/acpi_video_flags: No such file or directory
vbetool not installed!
vbetool not installed!
vbetool not installed!
vbetool not installed!


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Aug 10 15:07:23 NZST 2013: performing suspend
Sat Aug 10 15:07:24 NZST 2013: Awake.
Sat Aug 10 15:07:24 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
vbetool not installed!
vbetool not installed!
vbetool not installed!
vbetool not installed!


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Aug 10 15:07:25 NZST 2013: Finished.
Initial commandline parameters: 
Tue Aug 13 15:25:11 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-moreD-v0.9-Realms-kexec #9 SMP PREEMPT Tue Aug 13 14:40:33 NZST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
             total       used       free     shared    buffers     cached
Mem:        991128     954588      36540          0      43664     688048
-/+ buffers/cache:     222876     768252
Swap:            0          0          0


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Aug 13 15:25:12 NZST 2013: performing suspend
Tue Aug 13 15:25:30 NZST 2013: Awake.
Tue Aug 13 15:25:30 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Aug 13 15:25:30 NZST 2013: Finished.
Initial commandline parameters: 
Tue Aug 13 15:43:44 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-moreD-v0.9-Realms-kexec #9 SMP PREEMPT Tue Aug 13 14:40:33 NZST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
             total       used       free     shared    buffers     cached
Mem:        991128     603588     387540          0      21536     538584
-/+ buffers/cache:      43468     947660
Swap:            0          0          0


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Aug 13 15:43:44 NZST 2013: performing suspend
Tue Aug 13 15:45:08 NZST 2013: Awake.
Tue Aug 13 15:45:08 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Aug 13 15:45:09 NZST 2013: Finished.
Initial commandline parameters: --quick-vbe-post
Tue Aug 13 16:11:06 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-moreD-v0.9-Realms-kexec #9 SMP PREEMPT Tue Aug 13 14:40:33 NZST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
             total       used       free     shared    buffers     cached
Mem:        991128     941492      49636          0      40968     692124
-/+ buffers/cache:     208400     782728
Swap:            0          0          0


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Tue Aug 13 16:11:07 NZST 2013: performing suspend
Tue Aug 13 16:11:15 NZST 2013: Awake.
Tue Aug 13 16:11:15 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Aug 13 16:11:16 NZST 2013: Finished.
Initial commandline parameters: --quirk-dpms-on
Fri Aug 16 10:42:30 NZST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tf700 3.1.10-moreD-v0.9-Realms-kexec #9 SMP PREEMPT Tue Aug 13 14:40:33 NZST 2013 armv7l armv7l armv7l GNU/Linux
Module                  Size  Used by
             total       used       free     shared    buffers     cached
Mem:        991128     957976      33152          0      10044     507864
-/+ buffers/cache:     440068     551060
Swap:            0          0          0


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55wicd suspend suspend:
Unable to connect to wicd daemon - is it running?


/usr/lib/pm-utils/sleep.d/55wicd suspend suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Fri Aug 16 10:42:31 NZST 2013: performing suspend
Fri Aug 16 10:43:08 NZST 2013: Awake.
Fri Aug 16 10:43:08 NZST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55wicd resume suspend:
Unable to connect to wicd daemon - is it running?


/usr/lib/pm-utils/sleep.d/55wicd resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Aug 16 10:43:09 NZST 2013: Finished.
```

Any help is much appreciated!

---

