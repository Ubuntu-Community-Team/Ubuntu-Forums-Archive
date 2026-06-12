---
title: "GUI freezes, can't restart lightdm"
date: 2015-03-23
forum: General Help
---

### Post by RayDeCampo on 2015-03-23
I am having an issue, I imagine with the graphics driver, where the GUI will simply freeze up.  None of the Ctrl+Alt+ usual X shortcuts do anything.  However I can ssh into the box and issue commands.  I try to restart lightdm in this circumstance but that does not help.

What I would like to know is what can be done at that point to get the GUI working again short of restarting the system?

The following is in syslog:

```

Mar 23 08:20:04 eddie kernel: [51324.174571] chrome[11202]: segfault at 3b0 ip 00007fe09bcb1bd9 sp 00007fff7d114c70 error 4 in libnvidia-glcore.so.304.125[7fe09a9cf000+19d0000]
Mar 23 09:17:01 eddie CRON[12221]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 23 10:17:01 eddie CRON[12668]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 23 10:36:07 eddie dbus[601]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Mar 23 10:36:07 eddie dbus[601]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Mar 23 11:17:01 eddie CRON[13492]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 23 11:31:25 eddie kernel: [62814.211240] chrome[11650]: segfault at 3b0 ip 00007fee4b0fbbd9 sp 00007fffea476be0 error 4 in libnvidia-glcore.so.304.125[7fee49e19000+19d0000]
Mar 23 11:55:37 eddie kernel: [64267.796040] chrome[13658]: segfault at 3b0 ip 00007f15adfd0bd9 sp 00007fff9adf70a0 error 4 in libnvidia-glcore.so.304.125[7f15accee000+19d0000]
Mar 23 11:57:01 eddie colord: device removed: xrandr-Acer Technologies-P235H-LGU0C0194050
Mar 23 11:57:01 eddie colord: Profile removed: icc-b2ce5dcb7e1c5ddf44138b1fec076070
Mar 23 11:58:30 eddie kernel: [64440.852999] init: lightdm main process (1277) killed by KILL signal
Mar 23 11:58:31 eddie kernel: [64441.909646] init: nvidia-prime main process (14030) terminated with status 127
Mar 23 11:58:35 eddie kernel: [64445.414578] init: lightdm main process (14064) terminated with status 1
Mar 23 11:58:52 eddie rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="692" x-info="http://www.rsyslog.com"] exiting on signal 15.
Mar 23 11:59:42 eddie rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="710" x-info="http://www.rsyslog.com"] start
Mar 23 11:59:42 eddie rsyslogd: rsyslogd's groupid changed to 103
Mar 23 11:59:42 eddie rsyslogd: rsyslogd's userid changed to 101

```


The lines around 11:58:30 are probably from when I issued "service lightdm restart".  The segfaults from the NVIDIA driver are probably the proximate cause.

---

### Post by Portaro on 2015-03-23
Is a problem with your x config caused by the Nvidia driver module - [ftp://download.nvidia.com/XFree86/Linux-x86/304.125/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/304.125/README/README.txt) , I suggest to you to try edit config manually the x file step 6B , or try to see if your kernel is compatible with your kernel version.

To stop start lightdm you need  move to a text tty and isert you login and pass and then 

sudo service lightdm stop

edit your x config 

sudo service lightdm start

---

