---
title: "Lubuntu / VBox Frezes"
date: 2015-06-23
forum: General Help
---

### Post by n-david-2 on 2015-06-23
When I try to login at my Lubuntu 14 VM it freezes. When I "power off" and start again it displays the recovery menu. If I run the recovery and "mount -o remount rw, /" I can start but when I "power off" I must go through the same process again.

RAM - 2048Mb
Video - 128Mb

```
less /var/logs/syslog returns

Jun 23 07:46:30 VBoxLub1 anacron[18504]: Job `cron.daily' terminated
Jun 23 07:46:30 VBoxLub1 anacron[18504]: Normal exit (1 job run)
Jun 23 08:17:01 VBoxLub1 CRON[18793]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 09:17:01 VBoxLub1 CRON[18910]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 10:17:01 VBoxLub1 CRON[19023]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 11:17:02 VBoxLub1 CRON[19139]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 12:17:01 VBoxLub1 CRON[19252]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 13:17:01 VBoxLub1 CRON[19364]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 23 13:34:14 VBoxLub1 kernel: [346330.080127] EXT4-fs (sda1): error count since last fsck: 1
Jun 23 13:34:14 VBoxLub1 kernel: [346330.080140] EXT4-fs (sda1): initial error at time 1434678824: ext4_reserve_inode_write:4897
Jun 23 13:34:14 VBoxLub1 kernel: [346330.080147] EXT4-fs (sda1): last error at time 1434678824: ext4_reserve_inode_write:4897
Jun 23 15:01:14 VBoxLub1 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1041" x-info="http://www.rsyslog.com"] start
Jun 23 15:01:14 VBoxLub1 rsyslogd: rsyslogd's groupid changed to 103
Jun 23 15:01:14 VBoxLub1 rsyslogd: rsyslogd's userid changed to 100
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] Linux version 3.16.0-39-generic (buildd@phianna) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #53-Ubuntu SMP Tue May 26 09:38:21 UTC 2015 (Ubuntu 3.16.0-39.53-generic 3.16.7-ckt11)
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-39-generic root=UUID=7b0557f6-74da-44cf-9a25-3e6c6771f068 ro recovery nomodeset
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] KERNEL supported cpus:
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000]   Intel GenuineIntel
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000]   AMD AuthenticAMD
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000]   Centaur CentaurHauls
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffeffff] usable
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x000000007fff0000-0x000000007fffffff] ACPI data
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] SMBIOS 2.5 present.
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] DMI: innotek GmbH VirtualBox/VirtualBox, BIOS VirtualBox 12/01/2006
Jun 23 15:01:14 VBoxLub1 kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved

```
Thanks,

DT

---

### Post by wildmanne39 on 2015-06-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

