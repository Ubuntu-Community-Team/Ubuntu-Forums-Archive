---
title: "Ubuntu 16.04 rebooted last night, how to determine the reason?"
date: 2017-08-21
forum: General Help
---

### Post by cleaf on 2017-08-21
I left office at 10 o'clock last night and this morning I find the Ubuntu 16.04 rebooted. 

Using the command "last reboot", I get some messages:

reboot   system boot  4.4.0-21-generic Mon Aug 21 23:39   still running
reboot   system boot  4.4.0-21-generic Tue Aug 15 11:28   still running
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:40 - 11:27 (12+23:46)
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:39 - 11:40  (00:00)
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:29 - 11:40  (00:10)
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:22 - 11:40  (00:17)
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:16 - 11:40  (00:23)
reboot   system boot  4.4.0-21-generic Wed Aug  2 11:12 - 11:15  (00:03)

The system rebooted at Aug 21 23:39.

I also attached the messages happened at Aug 21 23:39 in /var/log/auth.log:

Aug 21 23:39:42 ye-X10SRA-F systemd-logind[896]: New seat seat0.
Aug 21 23:39:42 ye-X10SRA-F systemd-logind[896]: Watching system buttons on /dev/input/event1 (Power Button)
Aug 21 23:39:42 ye-X10SRA-F systemd-logind[896]: Watching system buttons on /dev/input/event0 (Power Button)
Aug 21 23:39:42 ye-X10SRA-F lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Aug 21 23:39:42 ye-X10SRA-F lightdm: PAM adding faulty module: pam_kwallet.so
Aug 21 23:39:42 ye-X10SRA-F lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Aug 21 23:39:42 ye-X10SRA-F lightdm: PAM adding faulty module: pam_kwallet5.so
Aug 21 23:39:42 ye-X10SRA-F lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Aug 21 23:39:42 ye-X10SRA-F systemd-logind[896]: New session c1 of user lightdm.
Aug 21 23:39:42 ye-X10SRA-F systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Aug 21 23:39:43 ye-X10SRA-F lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Aug 21 23:39:43 ye-X10SRA-F lightdm: PAM adding faulty module: pam_kwallet.so
Aug 21 23:39:43 ye-X10SRA-F lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Aug 21 23:39:43 ye-X10SRA-F lightdm: PAM adding faulty module: pam_kwallet5.so
Aug 21 23:39:43 ye-X10SRA-F lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ycao"

Please advise me how to know the reboot reason?

If the messages are not enough, which log should be further checked?

Thanks!

---

### Post by ajgreeny on 2017-08-22
Was it rebooted and logged in to a user, and does the OS usually use autologin?  MIght you have used the restart button instead of shutdown?

Could it be a WOL that caused the system to restart?  WOL is not something I know anything about in terms of how it actually works, so I can not offer any more suggestions...... unless, of course, somebody else restarted the machine in your absence; is that possible?

---

### Post by cleaf on 2017-08-22
Last night, the system rebooted at nearly the same time (22 Aug, 23:43; 21 Aug, 23:39). I really want to know the reason.

How can I know which user account rebooted the system?

Would you please give me some advice:

I attached some lines starting from 22 Aug, 23:43 in syslog:

```
Aug 22 23:43:32 ye-X10SRA-F rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="864" x-info="http://www.rsyslog.com"] start
Aug 22 23:43:32 ye-X10SRA-F rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try [http://www.rsyslog.com/e/2222](http://www.rsyslog.com/e/2222) ]
Aug 22 23:43:32 ye-X10SRA-F rsyslogd: rsyslogd's groupid changed to 108
Aug 22 23:43:32 ye-X10SRA-F rsyslogd: rsyslogd's userid changed to 104
Aug 22 23:43:32 ye-X10SRA-F systemd-modules-load[336]: Inserted module 'lp'
Aug 22 23:43:32 ye-X10SRA-F systemd-modules-load[336]: Inserted module 'ppdev'
Aug 22 23:43:32 ye-X10SRA-F systemd-modules-load[336]: Inserted module 'parport_pc'
Aug 22 23:43:32 ye-X10SRA-F systemd-modules-load[336]: Inserted module 'coretemp'
Aug 22 23:43:32 ye-X10SRA-F systemd-modules-load[336]: Inserted module 'nct6775'
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Braille Device Support.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started udev Kernel Device Manager.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Starting Remount Root and Kernel File Systems...
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Remount Root and Kernel File Systems.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Reached target Local File Systems (Pre).
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Starting Load/Save Random Seed...
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Starting Flush Journal to Persistent Storage...
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Starting udev Coldplug all Devices...
Aug 22 23:43:32 ye-X10SRA-F rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Load/Save Random Seed.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Flush Journal to Persistent Storage.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started udev Coldplug all Devices.
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Starting Show Plymouth Boot Screen...
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 23:43:32 ye-X10SRA-F rsyslogd-2007: action 'action 10' suspended, next retry is Tue Aug 22 23:44:02 2017 [v8.16.0 try [http://www.rsyslog.com/e/2007](http://www.rsyslog.com/e/2007) ]
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Show Plymouth Boot Screen.
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] Initializing cgroup subsys cpuacct
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] Linux version 4.4.0-21-generic (buildd@lgw01-21) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 (Ubuntu 4.4.0-21.37-generic 4.4.6)
Aug 22 23:43:32 ye-X10SRA-F systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.4.0-21-generic root=UUID=c6995ee7-1cd3-4852-885a-137b4193af95 ro quiet splash vt.handoff=7
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] KERNEL supported cpus:
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000]   Intel GenuineIntel
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: checking bus 3, device 5: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-12/3-12.3"
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000]   AMD AuthenticAMD
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000]   Centaur CentaurHauls
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-11"
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: bus: 3, device: 2 was not an MTP device
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] x86/fpu: Using 'eager' FPU context switches.
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: bus: 3, device: 5 was not an MTP device
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000099bff] usable
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x0000000000099c00-0x000000000009ffff] reserved
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: checking bus 3, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14.1"
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000077663fff] usable
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x0000000077664000-0x0000000078414fff] reserved
Aug 22 23:43:32 ye-X10SRA-F mtp-probe: bus: 3, device: 6 was not an MTP device
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x0000000078415000-0x00000000786b6fff] usable
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x00000000786b7000-0x00000000792c2fff] ACPI NVS
Aug 22 23:43:32 ye-X10SRA-F systemd-udevd[483]: Process '/lib/udev/hdparm' failed with exit code 5.
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x00000000792c3000-0x000000007b263fff] reserved
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x000000007b264000-0x000000007b264fff] usable
Aug 22 23:43:32 ye-X10SRA-F kernel: [    0.000000] BIOS-e820: [mem 0x000000007b265000-0x000000007b2eafff] reserved
```

The message from syslog looks the same with last reboot message, so I guess the same reason causes reboot. 

> **ajgreeny said:**
> Was it rebooted and logged in to a user, and does the OS usually use autologin?  MIght you have used the restart button instead of shutdown?

Could it be a WOL that caused the system to restart?  WOL is not something I know anything about in terms of how it actually works, so I can not offer any more suggestions...... unless, of course, somebody else restarted the machine in your absence; is that possible?

---

### Post by ajgreeny on 2017-08-23
Open a terminal and use command **who** which will show you the current user, the login time of the session and the current time.

The terminal prompt, if still set as the system default will also show you the user in the form of **[COLOR="#FF0000"]user[/COLOR]@hostname**

---

