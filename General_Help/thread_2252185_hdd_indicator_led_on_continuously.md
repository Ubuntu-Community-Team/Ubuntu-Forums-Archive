---
title: "hdd indicator led on continuously"
date: 2014-11-09
forum: General Help
---

### Post by CyborgAlpha on 2014-11-09
System: Gateway laptop; ne51006u

Kubuntu 14.04 64bit

no real issues, except hdd indicator led on continuously 

ran iotop;

```
      TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                                                                                                      
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/0:0H]
    7 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_sched]
    8 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/0]
    9 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/1]
   10 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/2]
   11 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuos/3]
   12 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_bh]
   13 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/0]
   14 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/1]
   15 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/2]
   16 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcuob/3]
   17 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
   18 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
   19 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/1]
   20 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/1]
   21 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/1]
   22 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:0]
   23 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:0H]
   24 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/2]
   25 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/2]
   26 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/2]
   28 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/2:0H]
   29 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/3]
   30 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/3]
   31 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/3]
   32 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:0]
   33 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:0H]
   34 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   35 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kdevtmpfs]
   36 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   37 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [writeback]
   38 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd]
   39 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [bioset]
   41 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd]
   43 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata_sff]
```

any suggestions?

---

### Post by tgalati4 on 2014-11-09
Is it on solid or is it flickering as if the drive is being used?

Install htop and watch the CPU.  Perhaps there is an indexing process going on.  Is this a new install?

```
sudo apt-get install htop
htop
```

---

### Post by CyborgAlpha on 2014-11-10
on solid , new install
htop only shows a 3.2% cpu usage

Syslog points of interest; 

```
Nov 10 07:59:22 oh anacron[28960]: Job `cron.daily' terminated
Nov 10 07:59:22 oh anacron[28960]: Normal exit (1 job run)
Nov 10 08:17:01 oh CRON[29370]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 09:17:01 oh CRON[29462]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 10:17:01 oh CRON[29556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 11:17:02 oh CRON[29646]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 11:42:52 oh kernel: [70502.135939] usb 1-1: USB disconnect, device number 2
Nov 10 11:42:55 oh kernel: [70504.717045] hub 1-0:1.0: connect-debounce failed, port 1 disabled
```

goes into a loop;

```
Nov 10 11:42:57 oh kernel: [70507.278636] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:00 oh kernel: [70509.861137] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:03 oh kernel: [70512.443141] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:05 oh kernel: [70515.025176] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:08 oh kernel: [70517.607198] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:10 oh kernel: [70520.189153] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:13 oh kernel: [70522.771226] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:15 oh kernel: [70525.353201] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:18 oh kernel: [70527.935332] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:21 oh kernel: [70530.517273] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:23 oh kernel: [70533.103226] hub 1-0:1.0: connect-debounce failed, port 1 disabled
```

until

```
Nov 10 14:30:26 oh kernel: [80564.129756] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:29 oh kernel: [80566.711780] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:32 oh kernel: [80569.289748] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:34 oh kernel: [80571.867769] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:37 oh kernel: [80574.449798] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:39 oh kernel: [80577.027795] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:42 oh kernel: [80579.605837] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:44 oh kernel: [80582.187844] hub 1-0:1.0: connect-debounce failed, port 1 disabled
```

reboot [needed to use power button to turn off]

```
Nov 10 14:31:52 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="504" x-info="http://www.rsyslog.com"] start
Nov 10 14:31:52 oh rsyslogd: rsyslogd's groupid changed to 104
Nov 10 14:31:52 oh rsyslogd: rsyslogd's userid changed to 101
Nov 10 14:31:52 oh kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 10 14:31:52 oh kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 10 14:31:52 oh kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov 10 14:31:52 oh kernel: [    0.000000] Linux version 3.13.0-39-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 (Ubuntu 3.13.0-39.66-generic 3.13.11.8)
Nov 10 14:31:52 oh kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=c19faab6-6231-41ad-9909-7c1317fa2834 ro quiet splash vt.handoff=7
Nov 10 14:31:52 oh kernel: [    0.000000] KERNEL supported cpus:
Nov 10 14:31:52 oh kernel: [    0.000000]   Intel GenuineIntel
Nov 10 14:31:52 oh kernel: [    0.000000]   AMD AuthenticAMD
Nov 10 14:31:52 oh kernel: [    0.000000]   Centaur CentaurHauls
Nov 10 14:31:52 oh kernel: [    0.000000] e820: BIOS-provided physical RAM map:
```

here is the syslog file; [https://drive.google.com/file/d/0ByX5r7_fmbXKWEh3WDdjNGtuM0U/view?usp=sharing](https://drive.google.com/file/d/0ByX5r7_fmbXKWEh3WDdjNGtuM0U/view?usp=sharing)

---

### Post by pfeiffep on 2014-11-10
I'm using Ubuntu 14.04 LTS so I'm not certain how to add the **system monitor** in Kubuntu. This monitor displays 3 tabs (processes, resources, & file systems) - I've added it to my top panel using alt-right click on the panel. I use gnome-flash back / metacity. I believe it's in the Software Center if not pre-installed in Kubuntu.

---

### Post by CyborgAlpha on 2014-11-10
I have had system monitor running; with tabs [All process ; System load ; HDD monitor (I/O ; Total accesses ; total reads)] .
Nothing seems abnormal.

moved 30 gb of data across the network - no issues
rendered a 30min video (clip mts format) to mp4 a 5 hour process - no issues

yet from the black screen (with kubuntu on it) at boot-up until I shut it down (or reboot) the light stays on -- solid.

---

### Post by pfeiffep on 2014-11-11
> **CyborgAlpha said:**
> I have had system monitor running; with tabs [All process ; System load ; HDD monitor (I/O ; Total accesses ; total reads)] .
Nothing seems abnormal.

moved 30 gb of data across the network - no issues
rendered a 30min video (clip mts format) to mp4 a 5 hour process - no issues

yet from the black screen (with kubuntu on it) at boot-up until I shut it down (or reboot) the light stays on -- solid.Possibly a LED circuit hardware malfunction.

---

### Post by CyborgAlpha on 2014-11-11
> **pfeiffep said:**
> Possibly a LED circuit hardware malfunction.

I was think of this, but if that were the case, the LED would be on [solid] from boot BIOS post until shutdown. However, the light is normal on boot, prior to the appearance of the kubuntu black start screen. The system is no longer shutting down normally. As said, it's fine doing work - but when sitting idle it goes into an infinite loop;

[from the syslog]
```
Nov 11 07:47:20 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="770" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Nov 11 07:47:20 oh kernel: [61331.303584] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:23 oh kernel: [61333.885268] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:26 oh kernel: [61336.455328] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:28 oh kernel: [61339.033429] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:31 oh kernel: [61341.612016] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:33 oh kernel: [61344.189468] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:36 oh kernel: [61346.767468] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:38 oh kernel: [61349.345504] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:41 oh kernel: [61351.919752] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:44 oh kernel: [61354.501229] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 07:47:44 oh anacron[10499]: Job `cron.daily' terminated
Nov 11 07:47:44 oh anacron[10499]: Normal exit (1 job run)
Nov 11 07:47:46 oh kernel: [61357.075815] hub 1-0:1.0: connect-debounce failed, port 1 disabled
```

loops for 7 hours

```
Nov 11 14:47:00 oh kernel: [86530.112474] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:02 oh kernel: [86532.694753] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:05 oh kernel: [86535.276761] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:07 oh kernel: [86537.862139] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:10 oh kernel: [86540.444896] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:12 oh kernel: [86543.026899] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:15 oh kernel: [86545.608165] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:18 oh kernel: [86548.194966] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:20 oh kernel: [86550.776665] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:23 oh kernel: [86553.362734] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:25 oh kernel: [86555.944873] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:28 oh kernel: [86558.527045] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:31 oh kernel: [86561.112262] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:33 oh kernel: [86563.695143] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:36 oh kernel: [86566.277078] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:38 oh kernel: [86568.862742] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:41 oh kernel: [86571.448607] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:43 oh kernel: [86574.034237] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:44 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="770" x-info="http://www.rsyslog.com"] exiting on signal 15.
Nov 11 14:48:39 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="730" x-info="http://www.rsyslog.com"] start
```

When the mouse (on usb port) is touched the system freezes and has to shutdown via the power button.

I'm now in the process of looking for abnormalities in the syslog.

---

### Post by tgalati4 on 2014-11-11
You appear to have a shorted USB controller.  The hub is not working because it is shorted.  Connect-debounce allows a momentary short when connecting a device, but if the chip has failed then it stays shorted and that may be causing your hard disk light to stay on.  Did you spill anything on the computer?

---

### Post by CyborgAlpha on 2014-11-11
> **tgalati4 said:**
> You appear to have a shorted USB controller.  The hub is not working because it is shorted.  Connect-debounce allows a momentary short when connecting a device, but if the chip has failed then it stays shorted and that may be causing your hard disk light to stay on.  Did you spill anything on the computer?

no

I'm running one more test on the usb port. I'm only using the mouse when needed and then unplugging it. If tomorrow @ ~ 2:50pm it hasn't crashed , then the issue is the mouse.
The light is still on solid.

---

### Post by CyborgAlpha on 2014-11-12
> **tgalati4 said:**
> You appear to have a shorted USB controller.  The hub is not working because it is shorted.  Connect-debounce allows a momentary short when connecting a device, but if the chip has failed then it stays shorted and that may be causing your hard disk light to stay on.  Did you spill anything on the computer?

So far no issues with the mouse disconnected. I'll post a syslog around 5pm EST.

A look at a previous syslog (attached to the first post)

```
Nov 10 07:59:22 oh anacron[28960]: Job `cron.daily' terminated
Nov 10 07:59:22 oh anacron[28960]: Normal exit (1 job run)
Nov 10 08:17:01 oh CRON[29370]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 09:17:01 oh CRON[29462]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 10:17:01 oh CRON[29556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 11:17:02 oh CRON[29646]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 11:42:52 oh kernel: [70502.135939] usb 1-1: USB disconnect, device number 2
Nov 10 11:42:55 oh kernel: [70504.717045] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:42:57 oh kernel: [70507.278636] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:00 oh kernel: [70509.861137] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:03 oh kernel: [70512.443141] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:05 oh kernel: [70515.025176] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:08 oh kernel: [70517.607198] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:10 oh kernel: [70520.189153] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:13 oh kernel: [70522.771226] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:15 oh kernel: [70525.353201] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:18 oh kernel: [70527.935332] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:21 oh kernel: [70530.517273] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 11:43:23 oh kernel: [70533.103226] hub 1-0:1.0: connect-debounce failed, port 1 disabled
```
usb hub loop
```
Nov 10 14:30:39 oh kernel: [80577.027795] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:42 oh kernel: [80579.605837] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 10 14:30:44 oh kernel: [80582.187844] hub 1-0:1.0: connect-debounce failed, port 1 disabled

```
We see from 8am to 11:17am cron jobs being run with no usb hub issues.
The usb hub loop doesn't start until 11:45am, then runs (loops) every 2 to 3 seconds for just about 3 hours, it freezes and I reboot it.

A shorted usb hub or mouse, would show a continuous defect, not only when sitting idle.

---

### Post by CyborgAlpha on 2014-11-12
> **tgalati4 said:**
> You appear to have a shorted USB controller.  The hub is not working because it is shorted.  Connect-debounce allows a momentary short when connecting a device, but if the chip has failed then it stays shorted and that may be causing your hard disk light to stay on.  Did you spill anything on the computer?

As promised the debug work continues!

If you look at the date and time this is after reboot.
The first line is me disconnecting the usb mouse
```
Nov 11 15:10:47 oh kernel: [ 1347.042421] usb 1-1: USB disconnect, device number 2
Nov 11 15:17:01 oh CRON[2361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 16:17:01 oh CRON[2460]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 17:17:01 oh CRON[2558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 18:17:01 oh CRON[2653]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 19:17:01 oh CRON[2748]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 20:17:01 oh CRON[2841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 21:17:01 oh CRON[2934]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 22:17:01 oh CRON[3029]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 23:17:01 oh CRON[3124]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 00:17:01 oh CRON[3219]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 01:17:01 oh CRON[3314]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 02:17:01 oh CRON[3410]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 03:17:01 oh CRON[3503]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 04:17:01 oh CRON[3596]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 05:17:01 oh CRON[3687]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 06:17:01 oh CRON[3781]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 06:25:01 oh CRON[3797]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Nov 12 07:17:01 oh CRON[3878]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 12 07:30:02 oh CRON[3902]: (root) CMD (start -q anacron || :)
Nov 12 07:30:02 oh anacron[3905]: Anacron 2.3 started on 2014-11-12
Nov 12 07:30:02 oh anacron[3905]: Will run job `cron.daily' in 5 min.
Nov 12 07:30:02 oh anacron[3905]: Jobs will be executed sequentially
Nov 12 07:35:02 oh anacron[3905]: Job `cron.daily' started
Nov 12 07:35:02 oh anacron[3919]: Updated timestamp for job `cron.daily' to 2014-11-12
Nov 12 07:59:06 oh cracklib: no dictionary update necessary.
Nov 12 07:59:06 oh kernel: [61893.783049] type=1400 audit(1415797146.889:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4354 comm="apparmor_parser"
Nov 12 07:59:06 oh kernel: [61893.783067] type=1400 audit(1415797146.889:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4354 comm="apparmor_parser"
Nov 12 07:59:06 oh kernel: [61893.784204] type=1400 audit(1415797146.893:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4354 comm="apparmor_parser"
```

hourly cron from 15:17 to 6:17
daily cron until ~8am

no more usb loop! no short circuit!

hdd led still solid!

---

### Post by tgalati4 on 2014-11-12
Does the mouse work on other computers?  If so, then the mouse is OK and there is something wrong with either the 5VDC power supply or the USB controller or the motherboard has developed an internal short that is causing those symptoms and the hard disk light.

Can you boot into Windows and determine if the hard disk light works OK?

---

### Post by CyborgAlpha on 2014-11-13
> **tgalati4 said:**
> Does the mouse work on other computers?  If so, then the mouse is OK and there is something wrong with either the 5VDC power supply or the USB controller or the motherboard has developed an internal short that is causing those symptoms and the hard disk light.

Can you boot into Windows and determine if the hard disk light works OK?

1. The mouse works when plugged in and unplugged when no longer needed. In other words, the short* only appears when the system has been idle for a period of time.
2. I don't use dual boot, I've moved completely to linux. When I get refurbished systems, I have Kubuntu use the entire disk. I'm not a fan of Windows.

I'm beginning to think that this is a bug, because there is a battery led bug listed in the syslog.
I have about 12 systems here 32bit and 64bit, both 64bit have led bug issues.
The battery led issue indicates a discharging battery (when plugged-in), but the battery never runs out. It stays at 99% .
Both 64bit systems are Gateway/Acer .
And there are no real performance issues.

---

### Post by tgalati4 on 2014-11-13
Perhaps post the LED bug that you saw in syslog.  I did not see it in any of the logs that you have posted so far.

---

### Post by CyborgAlpha on 2014-11-13
> **tgalati4 said:**
> Perhaps post the LED bug that you saw in syslog.  I did not see it in any of the logs that you have posted so far.

I plan to do that.

---

### Post by CyborgAlpha on 2014-11-13
syslog bug;

```
Nov 11 14:48:39 oh kernel: [    1.511242] ACPI: acpi_idle registered with cpuidle
Nov 11 14:48:39 oh kernel: [    1.514153] [Firmware Bug]: No valid trip found
```

syslog {last reboot}

```

Nov 11 14:47:43 oh kernel: [86574.034237] hub 1-0:1.0: connect-debounce failed, port 1 disabled
Nov 11 14:47:44 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="770" x-info="http://www.rsyslog.com"] exiting on signal 15.
Nov 11 14:48:39 oh rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="730" x-info="http://www.rsyslog.com"] start
Nov 11 14:48:39 oh rsyslogd: rsyslogd's groupid changed to 104
Nov 11 14:48:39 oh rsyslogd: rsyslogd's userid changed to 101
Nov 11 14:48:39 oh kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 11 14:48:39 oh kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 11 14:48:39 oh kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov 11 14:48:39 oh kernel: [    0.000000] Linux version 3.13.0-39-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 (Ubuntu 3.13.0-39.66-generic 3.13.11.8)
Nov 11 14:48:39 oh kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=c19faab6-6231-41ad-9909-7c1317fa2834 ro quiet splash vt.handoff=7
Nov 11 14:48:39 oh kernel: [    0.000000] KERNEL supported cpus:
Nov 11 14:48:39 oh kernel: [    0.000000]   Intel GenuineIntel
Nov 11 14:48:39 oh kernel: [    0.000000]   AMD AuthenticAMD
Nov 11 14:48:39 oh kernel: [    0.000000]   Centaur CentaurHauls
Nov 11 14:48:39 oh kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] ACPI NVS
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000000070000-0x000000000009dfff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000020100000-0x00000000781bffff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000781c0000-0x0000000078434fff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000078435000-0x00000000784c4fff] type 20
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000784c5000-0x0000000078ac4fff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000078ac5000-0x0000000078bc4fff] ACPI NVS
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000078bc5000-0x0000000078c04fff] ACPI data
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000078c05000-0x00000000796eefff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000796ef000-0x0000000079feefff] ACPI NVS
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000079fef000-0x0000000079ffffff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffd00000-0x00000000ffffffff] reserved
Nov 11 14:48:39 oh kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000017fffffff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 11 14:48:39 oh kernel: [    0.000000] efi: EFI v2.31 by INSYDE Corp.
Nov 11 14:48:39 oh kernel: [    0.000000] efi:  ACPI 2.0=0x78c04014  SMBIOS=0x78ac4000 
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x000000000006f000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem01: type=10, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000070000-0x000000000009e000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001503000) (20MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem05: type=7, attr=0xf, range=[0x0000000001503000-0x0000000002000000) (10MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003403000) (20MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000003403000-0x0000000020000000) (459MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem08: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020100000) (1MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000020100000-0x0000000034b5e000) (330MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000034b5e000-0x00000000365a7000) (26MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem11: type=7, attr=0xf, range=[0x00000000365a7000-0x00000000526b1000) (449MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem12: type=2, attr=0xf, range=[0x00000000526b1000-0x0000000070000000) (473MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem13: type=4, attr=0xf, range=[0x0000000070000000-0x0000000070020000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000070020000-0x0000000075097000) (80MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem15: type=2, attr=0xf, range=[0x0000000075097000-0x0000000075181000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem16: type=1, attr=0xf, range=[0x0000000075181000-0x00000000752b5000) (1MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem17: type=7, attr=0xf, range=[0x00000000752b5000-0x00000000763ab000) (16MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem18: type=4, attr=0xf, range=[0x00000000763ab000-0x00000000777b5000) (20MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem19: type=7, attr=0xf, range=[0x00000000777b5000-0x0000000077c6b000) (4MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem20: type=3, attr=0xf, range=[0x0000000077c6b000-0x0000000077fb5000) (3MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem21: type=7, attr=0xf, range=[0x0000000077fb5000-0x0000000077fc9000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem22: type=2, attr=0xf, range=[0x0000000077fc9000-0x00000000780b5000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem23: type=7, attr=0xf, range=[0x00000000780b5000-0x00000000781b6000) (1MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem24: type=2, attr=0xf, range=[0x00000000781b6000-0x00000000781c0000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem25: type=6, attr=0x800000000000000f, range=[0x00000000781c0000-0x0000000078435000) (2MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem26: type=5, attr=0x800000000000000f, range=[0x0000000078435000-0x00000000784c5000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem27: type=0, attr=0xf, range=[0x00000000784c5000-0x0000000078ac5000) (6MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem28: type=10, attr=0xf, range=[0x0000000078ac5000-0x0000000078bc5000) (1MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem29: type=9, attr=0xf, range=[0x0000000078bc5000-0x0000000078c05000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem30: type=4, attr=0xf, range=[0x0000000078c05000-0x00000000796ef000) (10MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem31: type=10, attr=0xf, range=[0x00000000796ef000-0x0000000079fef000) (9MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem32: type=4, attr=0xf, range=[0x0000000079fef000-0x000000007a000000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem33: type=7, attr=0xf, range=[0x0000000100000000-0x0000000180000000) (2048MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem34: type=11, attr=0x8000000000000001, range=[0x00000000e00f8000-0x00000000e00f9000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem35: type=11, attr=0x8000000000000000, range=[0x00000000fed01000-0x00000000fed02000) (0MB)
Nov 11 14:48:39 oh kernel: [    0.000000] efi: mem36: type=11, attr=0x8000000000000000, range=[0x00000000ffd00000-0x0000000100000000) (3MB)
Nov 11 14:48:39 oh kernel: [    0.000000] SMBIOS 2.7 present.
Nov 11 14:48:39 oh kernel: [    0.000000] DMI: Gateway NE510/NE510, BIOS V2.05 12/25/2013
Nov 11 14:48:39 oh kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 11 14:48:39 oh kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 11 14:48:39 oh kernel: [    0.000000] No AGP bridge found
Nov 11 14:48:39 oh kernel: [    0.000000] e820: last_pfn = 0x180000 max_arch_pfn = 0x400000000
Nov 11 14:48:39 oh kernel: [    0.000000] MTRR default type: uncachable
Nov 11 14:48:39 oh kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 11 14:48:39 oh kernel: [    0.000000]   00000-9FFFF write-back
Nov 11 14:48:39 oh kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 11 14:48:39 oh kernel: [    0.000000]   C0000-FFFFF write-protect
Nov 11 14:48:39 oh kernel: [    0.000000] MTRR variable ranges enabled:
Nov 11 14:48:39 oh kernel: [    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
Nov 11 14:48:39 oh kernel: [    0.000000]   1 base 0FFD00000 mask FFFF00000 write-protect
Nov 11 14:48:39 oh kernel: [    0.000000]   2 base 000000000 mask F80000000 write-back
Nov 11 14:48:39 oh kernel: [    0.000000]   3 base 07C000000 mask FFC000000 uncachable
Nov 11 14:48:39 oh kernel: [    0.000000]   4 base 07B000000 mask FFF000000 uncachable
Nov 11 14:48:39 oh kernel: [    0.000000]   5 base 07AE00000 mask FFFE00000 uncachable
Nov 11 14:48:39 oh kernel: [    0.000000]   6 base 100000000 mask F80000000 write-back
Nov 11 14:48:39 oh kernel: [    0.000000]   7 disabled
Nov 11 14:48:39 oh kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 11 14:48:39 oh kernel: [    0.000000] e820: last_pfn = 0x7a000 max_arch_pfn = 0x400000000
Nov 11 14:48:39 oh kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 11 14:48:39 oh kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe3000, 0x02fe3fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x17fe00000-0x17fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x17fe00000-0x17fffffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe4000, 0x02fe4fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x17c000000-0x17fdfffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x17c000000-0x17fdfffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17bffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x100000000-0x17bffffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe5000, 0x02fe5fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x20100000-0x781bffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x20100000-0x201fffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x20200000-0x77ffffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x78000000-0x781bffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000] BRK [0x02fe6000, 0x02fe6fff] PGTABLE
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x78c05000-0x796eefff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x78c05000-0x78dfffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x78e00000-0x795fffff] page 2M
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x79600000-0x796eefff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000] init_memory_mapping: [mem 0x79fef000-0x79ffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [mem 0x79fef000-0x79ffffff] page 4k
Nov 11 14:48:39 oh kernel: [    0.000000] RAMDISK: [mem 0x34b5e000-0x365a6fff]
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: RSDP 0000000078c04014 000024 (v02 ACRSYS)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: XSDT 0000000078c04120 00009C (v01 ACRSYS ACRPRDCT 00000003      01000013)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: FACP 0000000078c01000 00010C (v05 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: DSDT 0000000078bf0000 00C804 (v02 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: FACS 0000000078b7d000 000040
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: UEFI 0000000078c03000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: MSDM 0000000078c02000 000055 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: HPET 0000000078c00000 000038 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LPIT 0000000078bff000 000104 (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: APIC 0000000078bfe000 000084 (v03 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: MCFG 0000000078bfd000 00003C (v01 ACRSYS ACRPRDCT 00000003 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: SSDT 0000000078bee000 000763 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: SSDT 0000000078bed000 000290 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: SSDT 0000000078bec000 00017A (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: UEFI 0000000078beb000 000042 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: SSDT 0000000078be8000 002D14 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: SSDT 0000000078be7000 0003E6 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: FPDT 0000000078be6000 000044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: BGRT 0000000078bef000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 11 14:48:39 oh kernel: [    0.000000] No NUMA configuration found
Nov 11 14:48:39 oh kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000017fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x17fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   NODE_DATA [mem 0x17fff6000-0x17fffafff]
Nov 11 14:48:39 oh kernel: [    0.000000]  [ffffea0000000000-ffffea0005ffffff] PMD -> [ffff88017b600000-ffff88017f5fffff] on node 0
Nov 11 14:48:39 oh kernel: [    0.000000] Zone ranges:
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   Normal   [mem 0x100000000-0x17fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000] Movable zone start for each node
Nov 11 14:48:39 oh kernel: [    0.000000] Early memory node ranges
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x00001000-0x0006efff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x00070000-0x0009dfff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x20100000-0x781bffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x78c05000-0x796eefff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x79fef000-0x79ffffff]
Nov 11 14:48:39 oh kernel: [    0.000000]   node   0: [mem 0x100000000-0x17fffffff]
Nov 11 14:48:39 oh kernel: [    0.000000] On node 0 totalpages: 1018711
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA zone: 22 pages reserved
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA32 zone: 7663 pages used for memmap
Nov 11 14:48:39 oh kernel: [    0.000000]   DMA32 zone: 490427 pages, LIFO batch:31
Nov 11 14:48:39 oh kernel: [    0.000000]   Normal zone: 8192 pages used for memmap
Nov 11 14:48:39 oh kernel: [    0.000000]   Normal zone: 524288 pages, LIFO batch:31
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1])
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high level lint[0x1])
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high level lint[0x1])
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high level lint[0x1])
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 11 14:48:39 oh kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-86
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 11 14:48:39 oh kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 11 14:48:39 oh kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 11 14:48:39 oh kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Nov 11 14:48:39 oh kernel: [    0.000000] nr_irqs_gsi: 103
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0006f000-0x0006ffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x200fffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x781c0000-0x78434fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x78435000-0x784c4fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x784c5000-0x78ac4fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x78ac5000-0x78bc4fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x78bc5000-0x78c04fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x796ef000-0x79feefff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7a000000-0x7affffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7b000000-0x7effffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7f000000-0xe00f7fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xffcfffff]
Nov 11 14:48:39 oh kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffd00000-0xffffffff]
Nov 11 14:48:39 oh kernel: [    0.000000] e820: [mem 0x7f000000-0xe00f7fff] available for PCI devices
Nov 11 14:48:39 oh kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 11 14:48:39 oh kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Nov 11 14:48:39 oh kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88017fc00000 s86400 r8192 d24192 u524288
Nov 11 14:48:39 oh kernel: [    0.000000] pcpu-alloc: s86400 r8192 d24192 u524288 alloc=1*2097152
Nov 11 14:48:39 oh kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Nov 11 14:48:39 oh kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1002770
Nov 11 14:48:39 oh kernel: [    0.000000] Policy zone: Normal
Nov 11 14:48:39 oh kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=c19faab6-6231-41ad-9909-7c1317fa2834 ro quiet splash vt.handoff=7
Nov 11 14:48:39 oh kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 11 14:48:39 oh kernel: [    0.000000] Checking aperture...
Nov 11 14:48:39 oh kernel: [    0.000000] No AGP bridge found
Nov 11 14:48:39 oh kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 11 14:48:39 oh kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov 11 14:48:39 oh kernel: [    0.000000] Memory: 3863952K/4074844K available (7375K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1444K bss, 210892K reserved)
Nov 11 14:48:39 oh kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Nov 11 14:48:39 oh kernel: [    0.000000] Hierarchical RCU implementation.
Nov 11 14:48:39 oh kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 11 14:48:39 oh kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Nov 11 14:48:39 oh kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Nov 11 14:48:39 oh kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Nov 11 14:48:39 oh kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1024 16
Nov 11 14:48:39 oh kernel: [    0.000000] Console: colour dummy device 80x25
Nov 11 14:48:39 oh kernel: [    0.000000] console [tty0] enabled
Nov 11 14:48:39 oh kernel: [    0.000000] allocated 16777216 bytes of page_cgroup
Nov 11 14:48:39 oh kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 11 14:48:39 oh kernel: [    0.000000] hpet clockevent registered
Nov 11 14:48:39 oh kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Nov 11 14:48:39 oh kernel: [    0.004000] tsc: Detected 1866.742 MHz processor
Nov 11 14:48:39 oh kernel: [    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3733.48 BogoMIPS (lpj=7466968)
Nov 11 14:48:39 oh kernel: [    0.000010] pid_max: default: 32768 minimum: 301
Nov 11 14:48:39 oh kernel: [    0.001211] Security Framework initialized
Nov 11 14:48:39 oh kernel: [    0.001243] AppArmor: AppArmor initialized
Nov 11 14:48:39 oh kernel: [    0.001246] Yama: becoming mindful.
Nov 11 14:48:39 oh kernel: [    0.001823] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 11 14:48:39 oh kernel: [    0.003878] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 11 14:48:39 oh kernel: [    0.004805] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
Nov 11 14:48:39 oh kernel: [    0.004821] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
Nov 11 14:48:39 oh kernel: [    0.005223] Initializing cgroup subsys memory
Nov 11 14:48:39 oh kernel: [    0.005238] Initializing cgroup subsys devices
Nov 11 14:48:39 oh kernel: [    0.005242] Initializing cgroup subsys freezer
Nov 11 14:48:39 oh kernel: [    0.005246] Initializing cgroup subsys blkio
Nov 11 14:48:39 oh kernel: [    0.005250] Initializing cgroup subsys perf_event
Nov 11 14:48:39 oh kernel: [    0.005256] Initializing cgroup subsys hugetlb
Nov 11 14:48:39 oh kernel: [    0.005287] CPU: Physical Processor ID: 0
Nov 11 14:48:39 oh kernel: [    0.005290] CPU: Processor Core ID: 0
Nov 11 14:48:39 oh kernel: [    0.005297] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Nov 11 14:48:39 oh kernel: [    0.005297] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Nov 11 14:48:39 oh kernel: [    0.011218] mce: CPU supports 6 MCE banks
Nov 11 14:48:39 oh kernel: [    0.011229] CPU0: Thermal monitoring handled by SMI
Nov 11 14:48:39 oh kernel: [    0.011240] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
Nov 11 14:48:39 oh kernel: [    0.011240] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 0
Nov 11 14:48:39 oh kernel: [    0.011240] tlb_flushall_shift: 6
Nov 11 14:48:39 oh kernel: [    0.011399] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Nov 11 14:48:39 oh kernel: [    0.012850] ACPI: Core revision 20131115
Nov 11 14:48:39 oh kernel: [    0.030365] ACPI: All ACPI Tables successfully acquired
Nov 11 14:48:39 oh kernel: [    0.032987] ftrace: allocating 28541 entries in 112 pages
Nov 11 14:48:39 oh kernel: [    0.051235] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 11 14:48:39 oh kernel: [    0.090959] smpboot: CPU0: Intel(R) Celeron(R) CPU  N2920  @ 1.86GHz (fam: 06, model: 37, stepping: 03)
Nov 11 14:48:39 oh kernel: [    0.090975] TSC deadline timer enabled
Nov 11 14:48:39 oh kernel: [    0.090994] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
Nov 11 14:48:39 oh kernel: [    0.091007] ... version:                3
Nov 11 14:48:39 oh kernel: [    0.091010] ... bit width:              40
Nov 11 14:48:39 oh kernel: [    0.091012] ... generic registers:      2
Nov 11 14:48:39 oh kernel: [    0.091014] ... value mask:             000000ffffffffff
Nov 11 14:48:39 oh kernel: [    0.091017] ... max period:             000000ffffffffff
Nov 11 14:48:39 oh kernel: [    0.091019] ... fixed-purpose events:   3
Nov 11 14:48:39 oh kernel: [    0.091021] ... event mask:             0000000700000003
Nov 11 14:48:39 oh kernel: [    0.094361] x86: Booting SMP configuration:
Nov 11 14:48:39 oh kernel: [    0.111205] CPU1: Thermal monitoring handled by SMI
Nov 11 14:48:39 oh kernel: [    0.113459] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Nov 11 14:48:39 oh kernel: [    0.130511] CPU2: Thermal monitoring handled by SMI
Nov 11 14:48:39 oh kernel: [    0.149653] CPU3: Thermal monitoring handled by SMI
Nov 11 14:48:39 oh kernel: [    0.094368] .... node  #0, CPUs:      #1 #2 #3
Nov 11 14:48:39 oh kernel: [    0.151780] x86: Booted up 1 node, 4 CPUs
Nov 11 14:48:39 oh kernel: [    0.151787] smpboot: Total of 4 processors activated (14933.93 BogoMIPS)
Nov 11 14:48:39 oh kernel: [    0.152928] devtmpfs: initialized
Nov 11 14:48:39 oh kernel: [    0.160310] EVM: security.selinux
Nov 11 14:48:39 oh kernel: [    0.160314] EVM: security.SMACK64
Nov 11 14:48:39 oh kernel: [    0.160316] EVM: security.ima
Nov 11 14:48:39 oh kernel: [    0.160318] EVM: security.capability
Nov 11 14:48:39 oh kernel: [    0.160424] PM: Registering ACPI NVS region [mem 0x0006f000-0x0006ffff] (4096 bytes)
Nov 11 14:48:39 oh kernel: [    0.160429] PM: Registering ACPI NVS region [mem 0x78ac5000-0x78bc4fff] (1048576 bytes)
Nov 11 14:48:39 oh kernel: [    0.160467] PM: Registering ACPI NVS region [mem 0x796ef000-0x79feefff] (9437184 bytes)
Nov 11 14:48:39 oh kernel: [    0.162617] pinctrl core: initialized pinctrl subsystem
Nov 11 14:48:39 oh kernel: [    0.162757] regulator-dummy: no parameters
Nov 11 14:48:39 oh kernel: [    0.162798] RTC time: 14:48:22, date: 11/11/14
Nov 11 14:48:39 oh kernel: [    0.162876] NET: Registered protocol family 16
Nov 11 14:48:39 oh kernel: [    0.163119] cpuidle: using governor ladder
Nov 11 14:48:39 oh kernel: [    0.163123] cpuidle: using governor menu
Nov 11 14:48:39 oh kernel: [    0.163233] ACPI: bus type PCI registered
Nov 11 14:48:39 oh kernel: [    0.163238] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Nov 11 14:48:39 oh kernel: [    0.163357] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Nov 11 14:48:39 oh kernel: [    0.163363] PCI: not using MMCONFIG
Nov 11 14:48:39 oh kernel: [    0.163366] PCI: Using configuration type 1 for base access
Nov 11 14:48:39 oh kernel: [    0.165459] bio: create slab <bio-0> at 0
Nov 11 14:48:39 oh kernel: [    0.165826] ACPI: Added _OSI(Module Device)
Nov 11 14:48:39 oh kernel: [    0.165831] ACPI: Added _OSI(Processor Device)
Nov 11 14:48:39 oh kernel: [    0.165834] ACPI: Added _OSI(3.0 _SCP Extensions)
Nov 11 14:48:39 oh kernel: [    0.165837] ACPI: Added _OSI(Processor Aggregator Device)
Nov 11 14:48:39 oh kernel: [    0.185630] ACPI: SSDT 0000000078ab1a18 00045B (v01  PmRef  Cpu0Ist 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.186621] ACPI: Dynamic OEM Table Load:
Nov 11 14:48:39 oh kernel: [    0.186626] ACPI: SSDT           (null) 00045B (v01  PmRef  Cpu0Ist 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.186836] ACPI: SSDT 0000000078a88918 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.187809] ACPI: Dynamic OEM Table Load:
Nov 11 14:48:39 oh kernel: [    0.187814] ACPI: SSDT           (null) 000433 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.193235] ACPI: SSDT 0000000078ab3e18 00015F (v01  PmRef    ApIst 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.194255] ACPI: Dynamic OEM Table Load:
Nov 11 14:48:39 oh kernel: [    0.194260] ACPI: SSDT           (null) 00015F (v01  PmRef    ApIst 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.196913] ACPI: SSDT 0000000078ab2f18 00008D (v01  PmRef    ApCst 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.197892] ACPI: Dynamic OEM Table Load:
Nov 11 14:48:39 oh kernel: [    0.197897] ACPI: SSDT           (null) 00008D (v01  PmRef    ApCst 00003000 INTL 20120711)
Nov 11 14:48:39 oh kernel: [    0.204882] ACPI: Interpreter enabled
Nov 11 14:48:39 oh kernel: [    0.204897] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
Nov 11 14:48:39 oh kernel: [    0.204906] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
Nov 11 14:48:39 oh kernel: [    0.204936] ACPI: (supports S0 S3 S4 S5)
Nov 11 14:48:39 oh kernel: [    0.204940] ACPI: Using IOAPIC for interrupt routing
Nov 11 14:48:39 oh kernel: [    0.204984] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Nov 11 14:48:39 oh kernel: [    0.205928] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
Nov 11 14:48:39 oh kernel: [    0.214305] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 11 14:48:39 oh kernel: [    0.214757] ACPI: No dock devices found.
Nov 11 14:48:39 oh kernel: [    0.378040] ACPI: Power Resource [USBC] (on)
Nov 11 14:48:39 oh kernel: [    0.382413] ACPI: Power Resource [FN00] (off)
Nov 11 14:48:39 oh kernel: [    0.383476] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov 11 14:48:39 oh kernel: [    0.383488] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Nov 11 14:48:39 oh kernel: [    0.383576] \_SB_.PCI0:_OSC invalid UUID
Nov 11 14:48:39 oh kernel: [    0.383579] _OSC request data:1 1f 0 
Nov 11 14:48:39 oh kernel: [    0.383588] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
Nov 11 14:48:39 oh kernel: [    0.384090] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
Nov 11 14:48:39 oh kernel: [    0.384449] PCI host bridge to bus 0000:00
Nov 11 14:48:39 oh kernel: [    0.384456] pci_bus 0000:00: root bus resource [bus 00-ff]
Nov 11 14:48:39 oh kernel: [    0.384461] pci_bus 0000:00: root bus resource [io  0x0000-0x006f]
Nov 11 14:48:39 oh kernel: [    0.384465] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7]
Nov 11 14:48:39 oh kernel: [    0.384469] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Nov 11 14:48:39 oh kernel: [    0.384474] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Nov 11 14:48:39 oh kernel: [    0.384478] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Nov 11 14:48:39 oh kernel: [    0.384482] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff]
Nov 11 14:48:39 oh kernel: [    0.384486] pci_bus 0000:00: root bus resource [mem 0x80000000-0x909ffffe]
Nov 11 14:48:39 oh kernel: [    0.384500] pci 0000:00:00.0: [8086:0f00] type 00 class 0x060000
Nov 11 14:48:39 oh kernel: [    0.384662] pci 0000:00:02.0: [8086:0f31] type 00 class 0x030000
Nov 11 14:48:39 oh kernel: [    0.384681] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x903fffff]
Nov 11 14:48:39 oh kernel: [    0.384696] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff pref]
Nov 11 14:48:39 oh kernel: [    0.384710] pci 0000:00:02.0: reg 0x20: [io  0x2050-0x2057]
Nov 11 14:48:39 oh kernel: [    0.384890] pci 0000:00:13.0: [8086:0f23] type 00 class 0x010601
Nov 11 14:48:39 oh kernel: [    0.384915] pci 0000:00:13.0: reg 0x10: [io  0x2048-0x204f]
Nov 11 14:48:39 oh kernel: [    0.384927] pci 0000:00:13.0: reg 0x14: [io  0x205c-0x205f]
Nov 11 14:48:39 oh kernel: [    0.384939] pci 0000:00:13.0: reg 0x18: [io  0x2040-0x2047]
Nov 11 14:48:39 oh kernel: [    0.384951] pci 0000:00:13.0: reg 0x1c: [io  0x2058-0x205b]
Nov 11 14:48:39 oh kernel: [    0.384963] pci 0000:00:13.0: reg 0x20: [io  0x2020-0x203f]
Nov 11 14:48:39 oh kernel: [    0.384975] pci 0000:00:13.0: reg 0x24: [mem 0x90917000-0x909177ff]
Nov 11 14:48:39 oh kernel: [    0.385029] pci 0000:00:13.0: PME# supported from D3hot
Nov 11 14:48:39 oh kernel: [    0.385179] pci 0000:00:14.0: [8086:0f35] type 00 class 0x0c0330
Nov 11 14:48:39 oh kernel: [    0.385204] pci 0000:00:14.0: reg 0x10: [mem 0x90900000-0x9090ffff 64bit]
Nov 11 14:48:39 oh kernel: [    0.385272] pci 0000:00:14.0: PME# supported from D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.385356] pci 0000:00:14.0: System wakeup disabled by ACPI
Nov 11 14:48:39 oh kernel: [    0.385424] pci 0000:00:1a.0: [8086:0f18] type 00 class 0x108000
Nov 11 14:48:39 oh kernel: [    0.385447] pci 0000:00:1a.0: reg 0x10: [mem 0x90800000-0x908fffff]
Nov 11 14:48:39 oh kernel: [    0.385460] pci 0000:00:1a.0: reg 0x14: [mem 0x90700000-0x907fffff]
Nov 11 14:48:39 oh kernel: [    0.385537] pci 0000:00:1a.0: PME# supported from D0 D3hot
Nov 11 14:48:39 oh kernel: [    0.385675] pci 0000:00:1b.0: [8086:0f04] type 00 class 0x040300
Nov 11 14:48:39 oh kernel: [    0.385703] pci 0000:00:1b.0: reg 0x10: [mem 0x90910000-0x90913fff 64bit]
Nov 11 14:48:39 oh kernel: [    0.385784] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.385917] pci 0000:00:1c.0: [8086:0f48] type 01 class 0x060400
Nov 11 14:48:39 oh kernel: [    0.385987] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.386074] pci 0000:00:1c.0: System wakeup disabled by ACPI
Nov 11 14:48:39 oh kernel: [    0.386134] pci 0000:00:1c.1: [8086:0f4a] type 01 class 0x060400
Nov 11 14:48:39 oh kernel: [    0.386204] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.386289] pci 0000:00:1c.1: System wakeup disabled by ACPI
Nov 11 14:48:39 oh kernel: [    0.386361] pci 0000:00:1f.0: [8086:0f1c] type 00 class 0x060100
Nov 11 14:48:39 oh kernel: [    0.386569] pci 0000:00:1f.3: [8086:0f12] type 00 class 0x0c0500
Nov 11 14:48:39 oh kernel: [    0.386609] pci 0000:00:1f.3: reg 0x10: [mem 0x90914000-0x9091401f]
Nov 11 14:48:39 oh kernel: [    0.386685] pci 0000:00:1f.3: reg 0x20: [io  0x2000-0x201f]
Nov 11 14:48:39 oh kernel: [    0.387019] pci 0000:01:00.0: [10ec:5289] type 00 class 0xff0000
Nov 11 14:48:39 oh kernel: [    0.387053] pci 0000:01:00.0: reg 0x10: [mem 0x90600000-0x9060ffff]
Nov 11 14:48:39 oh kernel: [    0.387198] pci 0000:01:00.0: supports D1 D2
Nov 11 14:48:39 oh kernel: [    0.387202] pci 0000:01:00.0: PME# supported from D1 D2 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.387270] pci 0000:01:00.0: System wakeup disabled by ACPI
Nov 11 14:48:39 oh kernel: [    0.387355] pci 0000:01:00.2: [10ec:8168] type 00 class 0x020000
Nov 11 14:48:39 oh kernel: [    0.387389] pci 0000:01:00.2: reg 0x10: [io  0x1000-0x10ff]
Nov 11 14:48:39 oh kernel: [    0.387429] pci 0000:01:00.2: reg 0x18: [mem 0x90610000-0x90610fff 64bit]
Nov 11 14:48:39 oh kernel: [    0.387454] pci 0000:01:00.2: reg 0x20: [mem 0x90400000-0x90403fff 64bit pref]
Nov 11 14:48:39 oh kernel: [    0.387547] pci 0000:01:00.2: supports D1 D2
Nov 11 14:48:39 oh kernel: [    0.387551] pci 0000:01:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.393127] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 11 14:48:39 oh kernel: [    0.393135] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Nov 11 14:48:39 oh kernel: [    0.393141] pci 0000:00:1c.0:   bridge window [mem 0x90600000-0x906fffff]
Nov 11 14:48:39 oh kernel: [    0.393149] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
Nov 11 14:48:39 oh kernel: [    0.393262] pci 0000:02:00.0: [168c:0036] type 00 class 0x028000
Nov 11 14:48:39 oh kernel: [    0.393290] pci 0000:02:00.0: reg 0x10: [mem 0x90500000-0x9057ffff 64bit]
Nov 11 14:48:39 oh kernel: [    0.393346] pci 0000:02:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
Nov 11 14:48:39 oh kernel: [    0.393404] pci 0000:02:00.0: supports D1 D2
Nov 11 14:48:39 oh kernel: [    0.393408] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 11 14:48:39 oh kernel: [    0.393453] pci 0000:02:00.0: System wakeup disabled by ACPI
Nov 11 14:48:39 oh kernel: [    0.401105] pci 0000:00:1c.1: PCI bridge to [bus 02]
Nov 11 14:48:39 oh kernel: [    0.401114] pci 0000:00:1c.1:   bridge window [mem 0x90500000-0x905fffff]
Nov 11 14:48:39 oh kernel: [    0.454237] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.454375] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.454512] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.454648] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.454789] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.454926] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.455063] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.455199] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Nov 11 14:48:39 oh kernel: [    0.457344] ACPI: Enabled 6 GPEs in block 00 to 3F
Nov 11 14:48:39 oh kernel: [    0.457417] ACPI: \_SB_.PCI0: notify handler is installed
Nov 11 14:48:39 oh kernel: [    0.457562] Found 1 acpi root devices
Nov 11 14:48:39 oh kernel: [    0.457796] ACPI : EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Nov 11 14:48:39 oh kernel: [    0.458051] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 11 14:48:39 oh kernel: [    0.458062] vgaarb: loaded
Nov 11 14:48:39 oh kernel: [    0.458064] vgaarb: bridge control possible 0000:00:02.0
Nov 11 14:48:39 oh kernel: [    0.458447] SCSI subsystem initialized
Nov 11 14:48:39 oh kernel: [    0.458541] libata version 3.00 loaded.
Nov 11 14:48:39 oh kernel: [    0.458581] ACPI: bus type USB registered
Nov 11 14:48:39 oh kernel: [    0.458616] usbcore: registered new interface driver usbfs
Nov 11 14:48:39 oh kernel: [    0.458637] usbcore: registered new interface driver hub
Nov 11 14:48:39 oh kernel: [    0.458696] usbcore: registered new device driver usb
Nov 11 14:48:39 oh kernel: [    0.458943] PCI: Using ACPI for IRQ routing
Nov 11 14:48:39 oh kernel: [    0.460542] PCI: pci_cache_line_size set to 64 bytes
Nov 11 14:48:39 oh kernel: [    0.460595] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
Nov 11 14:48:39 oh kernel: [    0.460599] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
Nov 11 14:48:39 oh kernel: [    0.460602] e820: reserve RAM buffer [mem 0x781c0000-0x7bffffff]
Nov 11 14:48:39 oh kernel: [    0.460605] e820: reserve RAM buffer [mem 0x796ef000-0x7bffffff]
Nov 11 14:48:39 oh kernel: [    0.460608] e820: reserve RAM buffer [mem 0x7a000000-0x7bffffff]
Nov 11 14:48:39 oh kernel: [    0.460770] NetLabel: Initializing
Nov 11 14:48:39 oh kernel: [    0.460774] NetLabel:  domain hash size = 128
Nov 11 14:48:39 oh kernel: [    0.460776] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 11 14:48:39 oh kernel: [    0.460802] NetLabel:  unlabeled traffic allowed by default
Nov 11 14:48:39 oh kernel: [    0.460922] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 11 14:48:39 oh kernel: [    0.460930] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov 11 14:48:39 oh kernel: [    0.462994] Switched to clocksource hpet
Nov 11 14:48:39 oh kernel: [    0.472217] AppArmor: AppArmor Filesystem Enabled
Nov 11 14:48:39 oh kernel: [    0.472279] pnp: PnP ACPI init
Nov 11 14:48:39 oh kernel: [    0.472305] ACPI: bus type PNP registered
Nov 11 14:48:39 oh kernel: [    0.472398] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
Nov 11 14:48:39 oh kernel: [    0.472527] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
Nov 11 14:48:39 oh kernel: [    0.523155] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Nov 11 14:48:39 oh kernel: [    0.523213] pnp 00:03: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.0 BAR 13 [io  0x1000-0x1fff]
Nov 11 14:48:39 oh kernel: [    0.523272] system 00:03: [io  0x0680-0x069f] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523278] system 00:03: [io  0x0400-0x047f] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523283] system 00:03: [io  0x0500-0x05fe] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523288] system 00:03: [io  0x0600-0x061f] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523293] system 00:03: [io  0xfd60-0xfd63] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523299] system 00:03: [mem 0xfed40000-0xfed44fff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.523306] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 11 14:48:39 oh kernel: [    0.523475] pnp 00:04: Plug and Play ACPI device, IDs MSF0001 PNP0303 (active)
Nov 11 14:48:39 oh kernel: [    0.523656] pnp 00:05: Plug and Play ACPI device, IDs ETD0509 PNP0f13 (active)
Nov 11 14:48:39 oh kernel: [    0.524165] system 00:06: [mem 0xe0000000-0xefffffff] could not be reserved
Nov 11 14:48:39 oh kernel: [    0.524172] system 00:06: [mem 0xfed01000-0xfed01fff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524177] system 00:06: [mem 0xfed03000-0xfed03fff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524181] system 00:06: [mem 0xfed04000-0xfed04fff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524186] system 00:06: [mem 0xfed0c000-0xfed0ffff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524191] system 00:06: [mem 0xfed08000-0xfed08fff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524196] system 00:06: [mem 0xfed1c000-0xfed1cfff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524201] system 00:06: [mem 0xfee00000-0xfeefffff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524205] system 00:06: [mem 0xfef00000-0xfeffffff] has been reserved
Nov 11 14:48:39 oh kernel: [    0.524211] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Nov 11 14:48:39 oh kernel: [    0.526101] pnp: PnP ACPI: found 7 devices
Nov 11 14:48:39 oh kernel: [    0.526106] ACPI: bus type PNP unregistered
Nov 11 14:48:39 oh kernel: [    0.534846] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Nov 11 14:48:39 oh kernel: [    0.534875] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
Nov 11 14:48:39 oh kernel: [    0.534882] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x001fffff pref] to [bus 02] add_size 200000
Nov 11 14:48:39 oh kernel: [    0.534892] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x001fffff pref] get_res_add_size add_size 200000
Nov 11 14:48:39 oh kernel: [    0.534897] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Nov 11 14:48:39 oh kernel: [    0.534907] pci 0000:00:1c.1: BAR 15: can't assign mem pref (size 0x300000)
Nov 11 14:48:39 oh kernel: [    0.534914] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
Nov 11 14:48:39 oh kernel: [    0.534922] pci 0000:00:1c.1: BAR 15: can't assign mem pref (size 0x100000)
Nov 11 14:48:39 oh kernel: [    0.534928] pci 0000:00:1c.0: PCI bridge to [bus 01]
Nov 11 14:48:39 oh kernel: [    0.534933] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
Nov 11 14:48:39 oh kernel: [    0.534941] pci 0000:00:1c.0:   bridge window [mem 0x90600000-0x906fffff]
Nov 11 14:48:39 oh kernel: [    0.534947] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x904fffff 64bit pref]
Nov 11 14:48:39 oh kernel: [    0.534956] pci 0000:02:00.0: BAR 6: assigned [mem 0x90580000-0x9058ffff pref]
Nov 11 14:48:39 oh kernel: [    0.534961] pci 0000:00:1c.1: PCI bridge to [bus 02]
Nov 11 14:48:39 oh kernel: [    0.534966] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
Nov 11 14:48:39 oh kernel: [    0.534973] pci 0000:00:1c.1:   bridge window [mem 0x90500000-0x905fffff]
Nov 11 14:48:39 oh kernel: [    0.534982] pci_bus 0000:00: Some PCI device resources are unassigned, try booting with pci=realloc
Nov 11 14:48:39 oh kernel: [    0.534987] pci_bus 0000:00: resource 4 [io  0x0000-0x006f]
Nov 11 14:48:39 oh kernel: [    0.534991] pci_bus 0000:00: resource 5 [io  0x0078-0x0cf7]
Nov 11 14:48:39 oh kernel: [    0.534995] pci_bus 0000:00: resource 6 [io  0x0d00-0xffff]
Nov 11 14:48:39 oh kernel: [    0.534999] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
Nov 11 14:48:39 oh kernel: [    0.535003] pci_bus 0000:00: resource 8 [mem 0x000c0000-0x000dffff]
Nov 11 14:48:39 oh kernel: [    0.535007] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000fffff]
Nov 11 14:48:39 oh kernel: [    0.535012] pci_bus 0000:00: resource 10 [mem 0x80000000-0x909ffffe]
Nov 11 14:48:39 oh kernel: [    0.535016] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
Nov 11 14:48:39 oh kernel: [    0.535020] pci_bus 0000:01: resource 1 [mem 0x90600000-0x906fffff]
Nov 11 14:48:39 oh kernel: [    0.535024] pci_bus 0000:01: resource 2 [mem 0x90400000-0x904fffff 64bit pref]
Nov 11 14:48:39 oh kernel: [    0.535029] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
Nov 11 14:48:39 oh kernel: [    0.535033] pci_bus 0000:02: resource 1 [mem 0x90500000-0x905fffff]
Nov 11 14:48:39 oh kernel: [    0.535107] NET: Registered protocol family 2
Nov 11 14:48:39 oh kernel: [    0.535526] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Nov 11 14:48:39 oh kernel: [    0.535690] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
Nov 11 14:48:39 oh kernel: [    0.535862] TCP: Hash tables configured (established 32768 bind 32768)
Nov 11 14:48:39 oh kernel: [    0.535921] TCP: reno registered
Nov 11 14:48:39 oh kernel: [    0.535940] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Nov 11 14:48:39 oh kernel: [    0.535987] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Nov 11 14:48:39 oh kernel: [    0.536150] NET: Registered protocol family 1
Nov 11 14:48:39 oh kernel: [    0.536178] pci 0000:00:02.0: Boot video device
Nov 11 14:48:39 oh kernel: [    0.536543] PCI: CLS 64 bytes, default 64
Nov 11 14:48:39 oh kernel: [    0.536684] Trying to unpack rootfs image as initramfs...
Nov 11 14:48:39 oh kernel: [    1.295502] Freeing initrd memory: 26916K (ffff880034b5e000 - ffff8800365a7000)
Nov 11 14:48:39 oh kernel: [    1.295513] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Nov 11 14:48:39 oh kernel: [    1.295518] software IO TLB [mem 0x723ab000-0x763ab000] (64MB) mapped at [ffff8800723ab000-ffff8800763aafff]
Nov 11 14:48:39 oh kernel: [    1.295918] microcode: CPU0 sig=0x30673, pf=0x8, revision=0x31a
Nov 11 14:48:39 oh kernel: [    1.295932] microcode: CPU1 sig=0x30673, pf=0x8, revision=0x31a
Nov 11 14:48:39 oh kernel: [    1.295948] microcode: CPU2 sig=0x30673, pf=0x8, revision=0x31a
Nov 11 14:48:39 oh kernel: [    1.295961] microcode: CPU3 sig=0x30673, pf=0x8, revision=0x31a
Nov 11 14:48:39 oh kernel: [    1.296074] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Nov 11 14:48:39 oh kernel: [    1.296078] Scanning for low memory corruption every 60 seconds
Nov 11 14:48:39 oh kernel: [    1.296578] Initialise system trusted keyring
Nov 11 14:48:39 oh kernel: [    1.296664] audit: initializing netlink socket (disabled)
Nov 11 14:48:39 oh kernel: [    1.296683] type=2000 audit(1415717303.296:1): initialized
Nov 11 14:48:39 oh kernel: [    1.343247] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 11 14:48:39 oh kernel: [    1.345657] zbud: loaded
Nov 11 14:48:39 oh kernel: [    1.345910] VFS: Disk quotas dquot_6.5.2
Nov 11 14:48:39 oh kernel: [    1.346001] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 11 14:48:39 oh kernel: [    1.346937] fuse init (API version 7.22)
Nov 11 14:48:39 oh kernel: [    1.347091] msgmni has been set to 7668
Nov 11 14:48:39 oh kernel: [    1.347194] Key type big_key registered
Nov 11 14:48:39 oh kernel: [    1.348186] Key type asymmetric registered
Nov 11 14:48:39 oh kernel: [    1.348190] Asymmetric key parser 'x509' registered
Nov 11 14:48:39 oh kernel: [    1.348258] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Nov 11 14:48:39 oh kernel: [    1.348340] io scheduler noop registered
Nov 11 14:48:39 oh kernel: [    1.348344] io scheduler deadline registered (default)
Nov 11 14:48:39 oh kernel: [    1.348395] io scheduler cfq registered
Nov 11 14:48:39 oh kernel: [    1.348925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 11 14:48:39 oh kernel: [    1.348953] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 11 14:48:39 oh kernel: [    1.349035] efifb: probing for efifb
Nov 11 14:48:39 oh kernel: [    1.349704] efifb: framebuffer at 0x80000000, mapped to 0xffffc90004780000, using 4160k, total 4160k
Nov 11 14:48:39 oh kernel: [    1.349709] efifb: mode is 1366x768x32, linelength=5504, pages=1
Nov 11 14:48:39 oh kernel: [    1.349711] efifb: scrolling: redraw
Nov 11 14:48:39 oh kernel: [    1.349714] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Nov 11 14:48:39 oh kernel: [    1.357187] Console: switching to colour frame buffer device 170x48
Nov 11 14:48:39 oh kernel: [    1.364443] fb0: EFI VGA frame buffer device
Nov 11 14:48:39 oh kernel: [    1.364467] intel_idle: does not run on family 6 model 55
Nov 11 14:48:39 oh kernel: [    1.364480] ipmi message handler version 39.2
Nov 11 14:48:39 oh kernel: [    1.435780] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Nov 11 14:48:39 oh kernel: [    1.507849] ACPI: AC Adapter [ACAD] (on-line)
Nov 11 14:48:39 oh kernel: [    1.508075] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Nov 11 14:48:39 oh kernel: [    1.508113] ACPI: Lid Switch [LID0]
Nov 11 14:48:39 oh kernel: [    1.508182] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Nov 11 14:48:39 oh kernel: [    1.508191] ACPI: Power Button [PWRB]
Nov 11 14:48:39 oh kernel: [    1.508270] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Nov 11 14:48:39 oh kernel: [    1.508277] ACPI: Sleep Button [SLPB]
Nov 11 14:48:39 oh kernel: [    1.508344] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Nov 11 14:48:39 oh kernel: [    1.508350] ACPI: Power Button [PWRF]
Nov 11 14:48:39 oh kernel: [    1.508457] ACPI: Fan [FAN0] (off)
Nov 11 14:48:39 oh kernel: [    1.511150] Monitor-Mwait will be used to enter C-1 state
Nov 11 14:48:39 oh kernel: [    1.511204] Monitor-Mwait will be used to enter C-3 state
Nov 11 14:48:39 oh kernel: [    1.511242] ACPI: acpi_idle registered with cpuidle
Nov 11 14:48:39 oh kernel: [    1.514153] [Firmware Bug]: No valid trip found
Nov 11 14:48:39 oh kernel: [    1.514204] GHES: HEST is not enabled!
Nov 11 14:48:39 oh kernel: [    1.514382] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Nov 11 14:48:39 oh kernel: [    1.534600] serial8250: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Nov 11 14:48:39 oh kernel: [    1.538951] Linux agpgart interface v0.103
Nov 11 14:48:39 oh kernel: [    1.542551] brd: module loaded
Nov 11 14:48:39 oh kernel: [    1.544065] loop: module loaded
Nov 11 14:48:39 oh kernel: [    1.544779] libphy: Fixed MDIO Bus: probed
Nov 11 14:48:39 oh kernel: [    1.544960] tun: Universal TUN/TAP device driver, 1.6
Nov 11 14:48:39 oh kernel: [    1.544964] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 11 14:48:39 oh kernel: [    1.545063] PPP generic driver version 2.4.2
Nov 11 14:48:39 oh kernel: [    1.545152] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 11 14:48:39 oh kernel: [    1.545161] ehci-pci: EHCI PCI platform driver
Nov 11 14:48:39 oh kernel: [    1.545181] ehci-platform: EHCI generic platform driver
Nov 11 14:48:39 oh kernel: [    1.545195] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 11 14:48:39 oh kernel: [    1.545198] ohci-pci: OHCI PCI platform driver
Nov 11 14:48:39 oh kernel: [    1.545214] ohci-platform: OHCI generic platform driver
Nov 11 14:48:39 oh kernel: [    1.545226] uhci_hcd: USB Universal Host Controller Interface driver
Nov 11 14:48:39 oh kernel: [    1.545469] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 11 14:48:39 oh kernel: [    1.545486] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Nov 11 14:48:39 oh kernel: [    1.545898] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Nov 11 14:48:39 oh kernel: [    1.545936] xhci_hcd 0000:00:14.0: irq 103 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [    1.546057] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Nov 11 14:48:39 oh kernel: [    1.546062] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 11 14:48:39 oh kernel: [    1.546066] usb usb1: Product: xHCI Host Controller
Nov 11 14:48:39 oh kernel: [    1.546070] usb usb1: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
Nov 11 14:48:39 oh kernel: [    1.546074] usb usb1: SerialNumber: 0000:00:14.0
Nov 11 14:48:39 oh kernel: [    1.546281] hub 1-0:1.0: USB hub found
Nov 11 14:48:39 oh kernel: [    1.546301] hub 1-0:1.0: 6 ports detected
Nov 11 14:48:39 oh kernel: [    1.547051] xhci_hcd 0000:00:14.0: xHCI Host Controller
Nov 11 14:48:39 oh kernel: [    1.547059] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Nov 11 14:48:39 oh kernel: [    1.547132] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Nov 11 14:48:39 oh kernel: [    1.547137] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Nov 11 14:48:39 oh kernel: [    1.547141] usb usb2: Product: xHCI Host Controller
Nov 11 14:48:39 oh kernel: [    1.547145] usb usb2: Manufacturer: Linux 3.13.0-39-generic xhci_hcd
Nov 11 14:48:39 oh kernel: [    1.547149] usb usb2: SerialNumber: 0000:00:14.0
Nov 11 14:48:39 oh kernel: [    1.547342] hub 2-0:1.0: USB hub found
Nov 11 14:48:39 oh kernel: [    1.547359] hub 2-0:1.0: 1 port detected
Nov 11 14:48:39 oh kernel: [    1.552452] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS1] at 0x60,0x64 irq 1,12
Nov 11 14:48:39 oh kernel: [    1.561043] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 11 14:48:39 oh kernel: [    1.561056] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 11 14:48:39 oh kernel: [    1.561411] mousedev: PS/2 mouse device common for all mice
Nov 11 14:48:39 oh kernel: [    1.561978] rtc_cmos 00:00: RTC can wake from S4
Nov 11 14:48:39 oh kernel: [    1.562135] rtc_cmos 00:00: rtc core: registered rtc_cmos as rtc0
Nov 11 14:48:39 oh kernel: [    1.562171] rtc_cmos 00:00: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov 11 14:48:39 oh kernel: [    1.562309] device-mapper: uevent: version 1.0.3
Nov 11 14:48:39 oh kernel: [    1.562438] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Nov 11 14:48:39 oh kernel: [    1.562450] ledtrig-cpu: registered to indicate activity on CPUs
Nov 11 14:48:39 oh kernel: [    1.562453] EFI Variables Facility v0.08 2004-May-17
Nov 11 14:48:39 oh kernel: [    1.571897] TCP: cubic registered
Nov 11 14:48:39 oh kernel: [    1.572099] NET: Registered protocol family 10
Nov 11 14:48:39 oh kernel: [    1.572413] NET: Registered protocol family 17
Nov 11 14:48:39 oh kernel: [    1.572452] Key type dns_resolver registered
Nov 11 14:48:39 oh kernel: [    1.573106] Loading compiled-in X.509 certificates
Nov 11 14:48:39 oh kernel: [    1.575076] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Nov 11 14:48:39 oh kernel: [    1.575828] Loaded X.509 cert 'Magrathea: Glacier signing key: e3c165d0891e3ceeb6dd5c18c7e1993cd24956b0'
Nov 11 14:48:39 oh kernel: [    1.575851] registered taskstats version 1
Nov 11 14:48:39 oh kernel: [    1.580582] Key type trusted registered
Nov 11 14:48:39 oh kernel: [    1.584758] Key type encrypted registered
Nov 11 14:48:39 oh kernel: [    1.588720] AppArmor: AppArmor sha1 policy hashing enabled
Nov 11 14:48:39 oh kernel: [    1.588725] IMA: No TPM chip found, activating TPM-bypass!
Nov 11 14:48:39 oh kernel: [    1.589097] regulator-dummy: disabling
Nov 11 14:48:39 oh kernel: [    1.589330]   Magic number: 6:130:839
Nov 11 14:48:39 oh kernel: [    1.589594] rtc_cmos 00:00: setting system clock to 2014-11-11 14:48:24 UTC (1415717304)
Nov 11 14:48:39 oh kernel: [    1.592017] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 11 14:48:39 oh kernel: [    1.592021] EDD information not available.
Nov 11 14:48:39 oh kernel: [    1.592101] PM: Hibernation image not present or could not be loaded.
Nov 11 14:48:39 oh kernel: [    1.595937] [Firmware Bug]: battery: (dis)charge rate invalid.
Nov 11 14:48:39 oh kernel: [    1.595989] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Nov 11 14:48:39 oh kernel: [    1.596000] ACPI: Battery Slot [BAT1] (battery present)
Nov 11 14:48:39 oh kernel: [    1.598141] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
Nov 11 14:48:39 oh kernel: [    1.598149] Write protecting the kernel read-only data: 12288k
Nov 11 14:48:39 oh kernel: [    1.603060] Freeing unused kernel memory: 804K (ffff880002737000 - ffff880002800000)
Nov 11 14:48:39 oh kernel: [    1.606837] Freeing unused kernel memory: 692K (ffff880002b53000 - ffff880002c00000)
Nov 11 14:48:39 oh kernel: [    1.632941] systemd-udevd[119]: starting version 204
Nov 11 14:48:39 oh kernel: [    1.658584] wmi: Mapper loaded
Nov 11 14:48:39 oh kernel: [    1.749495] ahci 0000:00:13.0: version 3.0
Nov 11 14:48:39 oh kernel: [    1.749727] ahci 0000:00:13.0: irq 104 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [    1.754368] [drm] Initialized drm 1.1.0 20060810
Nov 11 14:48:39 oh kernel: [    1.755126] rtsx_pci 0000:01:00.0: irq 105 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [    1.755155] rtsx_pci 0000:01:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 105
Nov 11 14:48:39 oh kernel: [    1.757689] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 11 14:48:39 oh kernel: [    1.757716] r8169 0000:01:00.2: can't disable ASPM; OS doesn't have ASPM control
Nov 11 14:48:39 oh kernel: [    1.758019] r8169 0000:01:00.2: irq 106 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [    1.758365] r8169 0000:01:00.2 eth0: RTL8411 at 0xffffc90000664000, f8:a9:63:07:c2:2d, XID 08800800 IRQ 106
Nov 11 14:48:39 oh kernel: [    1.758370] r8169 0000:01:00.2 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Nov 11 14:48:39 oh kernel: [    1.764200] ahci 0000:00:13.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x1 impl SATA mode
Nov 11 14:48:39 oh kernel: [    1.764211] ahci 0000:00:13.0: flags: 64bit ncq pm led clo pio slum part deso sadm sds 
Nov 11 14:48:39 oh kernel: [    1.764932] scsi0 : ahci
Nov 11 14:48:39 oh kernel: [    1.765113] scsi1 : ahci
Nov 11 14:48:39 oh kernel: [    1.765201] ata1: SATA max UDMA/133 abar m2048@0x90917000 port 0x90917100 irq 104
Nov 11 14:48:39 oh kernel: [    1.765204] ata2: DUMMY
Nov 11 14:48:39 oh kernel: [    1.789968] [drm] Memory usable by graphics device = 2048M
Nov 11 14:48:39 oh kernel: [    1.789977] checking generic (80000000 410000) vs hw (80000000 10000000)
Nov 11 14:48:39 oh kernel: [    1.789981] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
Nov 11 14:48:39 oh kernel: [    1.790014] Console: switching to colour dummy device 80x25
Nov 11 14:48:39 oh kernel: [    1.844954] i915 0000:00:02.0: irq 107 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [    1.844972] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Nov 11 14:48:39 oh kernel: [    1.844975] [drm] Driver supports precise vblank timestamp query.
Nov 11 14:48:39 oh kernel: [    1.845083] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Nov 11 14:48:39 oh kernel: [    1.856135] usb 1-1: new low-speed USB device number 2 using xhci_hcd
Nov 11 14:48:39 oh kernel: [    1.875419] usb 1-1: New USB device found, idVendor=0000, idProduct=0538
Nov 11 14:48:39 oh kernel: [    1.875426] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Nov 11 14:48:39 oh kernel: [    1.875431] usb 1-1: Product:  USB OPTICAL MOUSE
Nov 11 14:48:39 oh kernel: [    1.875605] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Nov 11 14:48:39 oh kernel: [    1.924028] fbcon: inteldrmfb (fb0) is primary device
Nov 11 14:48:39 oh kernel: [    1.988457] usb 1-2: new high-speed USB device number 3 using xhci_hcd
Nov 11 14:48:39 oh kernel: [    2.004811] usb 1-2: New USB device found, idVendor=1a40, idProduct=0101
Nov 11 14:48:39 oh kernel: [    2.004814] usb 1-2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Nov 11 14:48:39 oh kernel: [    2.004816] usb 1-2: Product: USB 2.0 Hub
Nov 11 14:48:39 oh kernel: [    2.005346] hub 1-2:1.0: USB hub found
Nov 11 14:48:39 oh kernel: [    2.005379] hub 1-2:1.0: 4 ports detected
Nov 11 14:48:39 oh kernel: [    2.084455] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 11 14:48:39 oh kernel: [    2.085250] ata1.00: ATA-9: WDC WD5000LPVX-22V0TT0, 01.01A01, max UDMA/133
Nov 11 14:48:39 oh kernel: [    2.085253] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
Nov 11 14:48:39 oh kernel: [    2.086255] ata1.00: configured for UDMA/133
Nov 11 14:48:39 oh kernel: [    2.086641] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000LPVX-2 01.0 PQ: 0 ANSI: 5
Nov 11 14:48:39 oh kernel: [    2.086998] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Nov 11 14:48:39 oh kernel: [    2.087001] sd 0:0:0:0: [sda] 4096-byte physical blocks
Nov 11 14:48:39 oh kernel: [    2.087245] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 11 14:48:39 oh kernel: [    2.087349] sd 0:0:0:0: [sda] Write Protect is off
Nov 11 14:48:39 oh kernel: [    2.087353] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 11 14:48:39 oh kernel: [    2.087610] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 14:48:39 oh kernel: [    2.172387] usb 1-4: new high-speed USB device number 4 using xhci_hcd
Nov 11 14:48:39 oh kernel: [    2.176488]  sda: sda1 sda2 sda3
Nov 11 14:48:39 oh kernel: [    2.177433] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 11 14:48:39 oh kernel: [    2.250658] usb 1-4: New USB device found, idVendor=04f2, idProduct=b3d6
Nov 11 14:48:39 oh kernel: [    2.250661] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 11 14:48:39 oh kernel: [    2.250664] usb 1-4: Product: HD WebCam
Nov 11 14:48:39 oh kernel: [    2.250666] usb 1-4: Manufacturer: SunplusIT INC.
Nov 11 14:48:39 oh kernel: [    2.296443] tsc: Refined TSC clocksource calibration: 1866.667 MHz
Nov 11 14:48:39 oh kernel: [    2.328289] hidraw: raw HID events driver (C) Jiri Kosina
Nov 11 14:48:39 oh kernel: [    2.333935] usbcore: registered new interface driver usbhid
Nov 11 14:48:39 oh kernel: [    2.333936] usbhid: USB HID core driver
Nov 11 14:48:39 oh kernel: [    2.337381] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input8
Nov 11 14:48:39 oh kernel: [    2.338257] hid-generic 0003:0000:0538.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:14.0-1/input0
Nov 11 14:48:39 oh kernel: [    2.408566] usb 1-2.1: new full-speed USB device number 5 using xhci_hcd
Nov 11 14:48:39 oh kernel: [    2.425928] usb 1-2.1: New USB device found, idVendor=0489, idProduct=e078
Nov 11 14:48:39 oh kernel: [    2.425931] usb 1-2.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Nov 11 14:48:39 oh kernel: [    2.449174] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x454f00)
Nov 11 14:48:39 oh kernel: [    2.469891] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x16, 0x0c.
Nov 11 14:48:39 oh kernel: [    2.570696] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
Nov 11 14:48:39 oh kernel: [    3.297706] Switched to clocksource tsc
Nov 11 14:48:39 oh kernel: [    3.649695] Console: switching to colour frame buffer device 170x48
Nov 11 14:48:39 oh kernel: [    3.656632] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Nov 11 14:48:39 oh kernel: [    3.656636] i915 0000:00:02.0: registered panic notifier
Nov 11 14:48:39 oh kernel: [    3.658361] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Nov 11 14:48:39 oh kernel: [    3.659123] acpi device:25: registered as cooling_device5
Nov 11 14:48:39 oh kernel: [    3.659275] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
Nov 11 14:48:39 oh kernel: [    3.659731] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 11 14:48:39 oh kernel: [    3.781832] [drm] Enabling RC6 states: RC6 off, RC6p off, RC6pp off
Nov 11 14:48:39 oh kernel: [    4.054151] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Nov 11 14:48:39 oh kernel: [    4.882006] random: nonblocking pool is initialized
Nov 11 14:48:39 oh kernel: [   12.781709] Adding 4074492k swap on /dev/sda3.  Priority:-1 extents:1 across:4074492k FS
Nov 11 14:48:39 oh kernel: [   12.981666] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 11 14:48:39 oh kernel: [   13.102150] systemd-udevd[320]: starting version 204
Nov 11 14:48:39 oh kernel: [   13.459417] lp: driver loaded but no devices found
Nov 11 14:48:39 oh kernel: [   13.471208] ppdev: user-space parallel port driver
Nov 11 14:48:39 oh kernel: [   13.662252] cfg80211: Calling CRDA to update world regulatory domain
Nov 11 14:48:39 oh kernel: [   13.676322] Bluetooth: Core ver 2.17
Nov 11 14:48:39 oh kernel: [   13.676370] NET: Registered protocol family 31
Nov 11 14:48:39 oh kernel: [   13.676374] Bluetooth: HCI device and connection manager initialized
Nov 11 14:48:39 oh kernel: [   13.676392] Bluetooth: HCI socket layer initialized
Nov 11 14:48:39 oh kernel: [   13.676397] Bluetooth: L2CAP socket layer initialized
Nov 11 14:48:39 oh kernel: [   13.676407] Bluetooth: SCO socket layer initialized
Nov 11 14:48:39 oh kernel: [   13.690039] usbcore: registered new interface driver btusb
Nov 11 14:48:39 oh kernel: [   13.735328] ath: phy0: Set BT/WLAN RX diversity capability
Nov 11 14:48:39 oh kernel: [   13.742479] ath: phy0: Enable LNA combining
Nov 11 14:48:39 oh kernel: [   13.776877] ath: phy0: ASPM enabled: 0x42
Nov 11 14:48:39 oh kernel: [   13.776885] ath: EEPROM regdomain: 0x6c
Nov 11 14:48:39 oh kernel: [   13.776888] ath: EEPROM indicates we should expect a direct regpair map
Nov 11 14:48:39 oh kernel: [   13.776892] ath: Country alpha2 being used: 00
Nov 11 14:48:39 oh kernel: [   13.776894] ath: Regpair used: 0x6c
Nov 11 14:48:39 oh kernel: [   13.822760] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Nov 11 14:48:39 oh kernel: [   13.823512] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc90004a80000, irq=17
Nov 11 14:48:39 oh kernel: [   13.833681] type=1400 audit(1415735316.732:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.833695] type=1400 audit(1415735316.732:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.833704] type=1400 audit(1415735316.732:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.835600] type=1400 audit(1415735316.732:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.835618] type=1400 audit(1415735316.732:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.836319] type=1400 audit(1415735316.732:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=395 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   13.971500] acer_wmi: Acer Laptop ACPI-WMI Extras
Nov 11 14:48:39 oh kernel: [   13.971605] acer_wmi: Function bitmap for Communication Button: 0x801
Nov 11 14:48:39 oh kernel: [   13.971617] acer_wmi: Brightness must be controlled by acpi video driver
Nov 11 14:48:39 oh kernel: [   13.999856] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
Nov 11 14:48:39 oh kernel: [   13.999956] snd_hda_intel 0000:00:1b.0: irq 108 for MSI/MSI-X
Nov 11 14:48:39 oh kernel: [   13.999987] input: Acer WMI hotkeys as /devices/virtual/input/input10
Nov 11 14:48:39 oh kernel: [   14.001644] input: Acer BMA150 accelerometer as /devices/virtual/input/input11
Nov 11 14:48:39 oh kernel: [   14.004287] acer_wmi: Get 0x1 Device Status failed: 0xe2 - 0x0
Nov 11 14:48:39 oh kernel: [   14.006413] acer_wmi: Get 0x800 Device Status failed: 0xe2 - 0x0
Nov 11 14:48:39 oh kernel: [   14.047300] SKU: Nid=0x1d sku_cfg=0x40589b2d
Nov 11 14:48:39 oh kernel: [   14.047307] SKU: port_connectivity=0x1
Nov 11 14:48:39 oh kernel: [   14.047309] SKU: enable_pcbeep=0x1
Nov 11 14:48:39 oh kernel: [   14.047311] SKU: check_sum=0x00000008
Nov 11 14:48:39 oh kernel: [   14.047313] SKU: customization=0x0000009b
Nov 11 14:48:39 oh kernel: [   14.047315] SKU: external_amp=0x5
Nov 11 14:48:39 oh kernel: [   14.047317] SKU: platform_type=0x1
Nov 11 14:48:39 oh kernel: [   14.047319] SKU: swap=0x0
Nov 11 14:48:39 oh kernel: [   14.047321] SKU: override=0x1
Nov 11 14:48:39 oh kernel: [   14.047885] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Nov 11 14:48:39 oh kernel: [   14.047888]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Nov 11 14:48:39 oh kernel: [   14.047891]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Nov 11 14:48:39 oh kernel: [   14.047893]    mono: mono_out=0x0
Nov 11 14:48:39 oh kernel: [   14.047895]    inputs:
Nov 11 14:48:39 oh kernel: [   14.047898]      Mic=0x1b
Nov 11 14:48:39 oh kernel: [   14.047901] realtek: No valid SSID, checking pincfg 0x40589b2d for NID 0x1d
Nov 11 14:48:39 oh kernel: [   14.047903] realtek: Enabling init ASM_ID=0x9b2d CODEC_ID=10ec0282
Nov 11 14:48:39 oh kernel: [   14.083223] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Nov 11 14:48:39 oh kernel: [   14.083483] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Nov 11 14:48:39 oh kernel: [   14.105968] cfg80211: World regulatory domain updated:
Nov 11 14:48:39 oh kernel: [   14.105976] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 11 14:48:39 oh kernel: [   14.105980] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 11 14:48:39 oh kernel: [   14.105983] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 11 14:48:39 oh kernel: [   14.105986] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 11 14:48:39 oh kernel: [   14.105989] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 11 14:48:39 oh kernel: [   14.105992] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 11 14:48:39 oh kernel: [   14.728071] Linux video capture interface: v2.00
Nov 11 14:48:39 oh kernel: [   14.741547] uvcvideo: Found UVC 1.00 device HD WebCam (04f2:b3d6)
Nov 11 14:48:39 oh kernel: [   14.750333] input: HD WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input14
Nov 11 14:48:39 oh kernel: [   14.750495] usbcore: registered new interface driver uvcvideo
Nov 11 14:48:39 oh kernel: [   14.750499] USB Video Class driver (1.1.1)
Nov 11 14:48:39 oh kernel: [   16.021490] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Nov 11 14:48:39 oh kernel: [   16.573255] init: failsafe main process (667) killed by TERM signal
Nov 11 14:48:39 oh ntpdate[725]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Nov 11 14:48:39 oh ntpdate[725]: no servers can be used, exiting
Nov 11 14:48:39 oh bluetoothd[756]: Bluetooth daemon 4.101
Nov 11 14:48:39 oh bluetoothd[756]: Starting SDP server
Nov 11 14:48:39 oh bluetoothd[756]: DIS cannot start: GATT is disabled
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init deviceinfo plugin
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init proximity plugin
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init time plugin
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init alert plugin
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init thermometer plugin
Nov 11 14:48:39 oh bluetoothd[756]: Failed to init gatt_example plugin
Nov 11 14:48:39 oh bluetoothd[756]: Bluetooth Management interface initialized
Nov 11 14:48:39 oh kernel: [   16.826605] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 11 14:48:39 oh kernel: [   16.826612] Bluetooth: BNEP filters: protocol multicast
Nov 11 14:48:39 oh kernel: [   16.826627] Bluetooth: BNEP socket layer initialized
Nov 11 14:48:39 oh kernel: [   16.827857] Bluetooth: RFCOMM TTY layer initialized
Nov 11 14:48:39 oh kernel: [   16.827879] Bluetooth: RFCOMM socket layer initialized
Nov 11 14:48:39 oh kernel: [   16.827898] Bluetooth: RFCOMM ver 1.11
Nov 11 14:48:39 oh kernel: [   16.867132] type=1400 audit(1415735319.760:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=772 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   16.867148] type=1400 audit(1415735319.760:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=772 comm="apparmor_parser"
Nov 11 14:48:39 oh kernel: [   16.868262] type=1400 audit(1415735319.764:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=772 comm="apparmor_parser"
Nov 11 14:48:39 oh rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Nov 11 14:48:39 oh bluetoothd[756]: Unknown command complete for opcode 19
Nov 11 14:48:40 oh bluetoothd[756]: Adapter /org/bluez/756/hci0 has been enabled
Nov 11 14:48:40 oh kernel: [   17.321928] init: cups main process (773) killed by HUP signal
Nov 11 14:48:40 oh kernel: [   17.321955] init: cups main process ended, respawning
Nov 11 14:48:40 oh avahi-daemon[780]: Found user 'avahi' (UID 110) and group 'avahi' (GID 117).
Nov 11 14:48:40 oh avahi-daemon[780]: Successfully dropped root privileges.
Nov 11 14:48:40 oh avahi-daemon[780]: avahi-daemon 0.6.31 starting up.
Nov 11 14:48:40 oh avahi-daemon[780]: Successfully called chroot().
Nov 11 14:48:40 oh avahi-daemon[780]: Successfully dropped remaining capabilities.
Nov 11 14:48:40 oh avahi-daemon[780]: No service file found in /etc/avahi/services.
Nov 11 14:48:40 oh kernel: [   17.520727] type=1400 audit(1415735320.416:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=834 comm="apparmor_parser"
Nov 11 14:48:40 oh avahi-daemon[780]: Network interface enumeration completed.
Nov 11 14:48:40 oh avahi-daemon[780]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 11 14:48:40 oh avahi-daemon[780]: Server startup complete. Host name is oh.local. Local service cookie is 759667040.
Nov 11 14:48:40 oh ModemManager[747]: <info>  ModemManager (version 1.0.0) starting...
Nov 11 14:48:41 oh NetworkManager[894]: <info> NetworkManager (version 0.9.8.8) is starting...
Nov 11 14:48:41 oh NetworkManager[894]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Nov 11 14:48:41 oh NetworkManager[894]: <info> WEXT support is enabled
Nov 11 14:48:41 oh NetworkManager[894]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Nov 11 14:48:41 oh NetworkManager[894]: <info> DNS: loaded plugin dnsmasq
Nov 11 14:48:41 oh dbus[708]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Nov 11 14:48:41 oh anacron[964]: Anacron 2.3 started on 2014-11-11
Nov 11 14:48:41 oh cron[912]: (CRON) INFO (pidfile fd = 3)
Nov 11 14:48:41 oh cron[990]: (CRON) STARTUP (fork ok)
Nov 11 14:48:41 oh kernel: [   18.639794] init: kdm main process (919) killed by TERM signal
Nov 11 14:48:41 oh kernel: [   18.667749] init: gdm main process (965) killed by TERM signal
Nov 11 14:48:41 oh cron[990]: (CRON) INFO (Running @reboot jobs)
Nov 11 14:48:41 oh acpid: starting up with netlink and the input layer
Nov 11 14:48:41 oh anacron[964]: Normal exit (0 jobs run)
Nov 11 14:48:41 oh polkitd[907]: started daemon version 0.105 using authority implementation `local' version `0.105'
Nov 11 14:48:41 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: init!
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: update_system_hostname
Nov 11 14:48:41 oh NetworkManager[894]:       interface-parser: parsing file /etc/network/interfaces
Nov 11 14:48:41 oh NetworkManager[894]:       interface-parser: finished parsing file /etc/network/interfaces
Nov 11 14:48:41 oh NetworkManager[894]:    SCPluginIfupdown: management mode: unmanaged
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2/net/eth0, iface: eth0)
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: end _init.
Nov 11 14:48:41 oh NetworkManager[894]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 11 14:48:41 oh NetworkManager[894]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ofono: init!
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ofono: end _init.
Nov 11 14:48:41 oh NetworkManager[894]: <info> Loaded plugin (null): (null)
Nov 11 14:48:41 oh NetworkManager[894]:    Ifupdown: get unmanaged devices count: 0
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: (30708496) ... get_connections.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ifupdown: (30708496) ... get_connections (managed=false): return empty list.
Nov 11 14:48:41 oh NetworkManager[894]:    keyfile: parsing cyborg_alpha01 ... 
Nov 11 14:48:41 oh NetworkManager[894]:    keyfile:     read connection 'cyborg_alpha01'
Nov 11 14:48:41 oh NetworkManager[894]:    keyfile: parsing Wired connection 1 ... 
Nov 11 14:48:41 oh NetworkManager[894]: keyfile: ipv4.address1: address 192.168.2.8/24 gateway 192.168.2.1
Nov 11 14:48:41 oh NetworkManager[894]:    keyfile:     read connection 'Wired connection 1'
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ofono: (1073758496) ... get_connections.
Nov 11 14:48:41 oh NetworkManager[894]:    SCPlugin-Ofono: (1073758496) connections count: 0
Nov 11 14:48:41 oh NetworkManager[894]:    Ifupdown: get unmanaged devices count: 0
Nov 11 14:48:41 oh NetworkManager[894]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 11 14:48:41 oh NetworkManager[894]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill1) (driver ath9k)
Nov 11 14:48:41 oh NetworkManager[894]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/platform/acer-wmi/rfkill/rfkill2) (platform driver acer-wmi)
Nov 11 14:48:41 oh NetworkManager[894]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 11 14:48:41 oh NetworkManager[894]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 11 14:48:41 oh NetworkManager[894]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 11 14:48:41 oh NetworkManager[894]: <info> Networking is enabled by state file
Nov 11 14:48:41 oh NetworkManager[894]: <warn> failed to allocate link cache: (-12) Object not found
Nov 11 14:48:41 oh NetworkManager[894]: <info> (eth0): carrier is OFF
Nov 11 14:48:41 oh NetworkManager[894]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 11 14:48:41 oh NetworkManager[894]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 11 14:48:41 oh NetworkManager[894]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 11 14:48:41 oh NetworkManager[894]: <info> (eth0): bringing up device.
Nov 11 14:48:41 oh whoopsie[949]: whoopsie 0.2.24.6 starting up.
Nov 11 14:48:42 oh acpid: 9 rules loaded
Nov 11 14:48:42 oh acpid: waiting for events: event logging is off
Nov 11 14:48:42 oh kernel: [   19.280646] r8169 0000:01:00.2 eth0: link down
Nov 11 14:48:42 oh kernel: [   19.280669] r8169 0000:01:00.2 eth0: link down
Nov 11 14:48:42 oh kernel: [   19.280731] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 11 14:48:42 oh NetworkManager[894]: <info> (eth0): preparing device.
Nov 11 14:48:42 oh NetworkManager[894]: <info> (eth0): deactivating device (reason 'managed') [2]
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): using nl80211 for WiFi device control
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): driver supports Access Point (AP) mode
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): bringing up device.
Nov 11 14:48:42 oh kernel: [   19.281972] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 11 14:48:42 oh kernel: [   19.299502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): preparing device.
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 11 14:48:42 oh NetworkManager[894]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Nov 11 14:48:42 oh kernel: [   19.302974] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 11 14:48:42 oh dbus[708]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Nov 11 14:48:42 oh whoopsie[949]: Using lock path: /var/lock/whoopsie/lock
Nov 11 14:48:42 oh NetworkManager[894]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Nov 11 14:48:42 oh NetworkManager[894]: <info> urfkill disappeared from the bus
Nov 11 14:48:42 oh whoopsie[1081]: offline
Nov 11 14:48:42 oh NetworkManager[894]: <info> ModemManager available in the bus
Nov 11 14:48:42 oh dbus[708]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Nov 11 14:48:42 oh NetworkManager[894]: <info> wpa_supplicant started
Nov 11 14:48:42 oh wpa_supplicant[1079]: Successfully initialized wpa_supplicant
Nov 11 14:48:42 oh xinetd[943]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Nov 11 14:48:42 oh xinetd[943]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Nov 11 14:48:42 oh xinetd[943]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Nov 11 14:48:42 oh xinetd[943]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Nov 11 14:48:42 oh xinetd[943]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Nov 11 14:48:42 oh xinetd[943]: removing chargen
Nov 11 14:48:42 oh xinetd[943]: removing chargen
Nov 11 14:48:42 oh xinetd[943]: removing daytime
Nov 11 14:48:42 oh xinetd[943]: removing daytime
Nov 11 14:48:42 oh xinetd[943]: removing discard
Nov 11 14:48:42 oh xinetd[943]: removing discard
Nov 11 14:48:42 oh xinetd[943]: removing echo
Nov 11 14:48:42 oh xinetd[943]: removing echo
Nov 11 14:48:42 oh xinetd[943]: removing time
Nov 11 14:48:42 oh xinetd[943]: removing time
Nov 11 14:48:42 oh xinetd[943]: xinetd Version 2.3.15 started with libwrap loadavg options compiled in.
Nov 11 14:48:42 oh xinetd[943]: Started working: 0 available services
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0) supports 4 scan SSIDs
Nov 11 14:48:42 oh NetworkManager[894]: <warn> Trying to remove a non-existant call id.
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0): supplicant interface state: ready -> disconnected
Nov 11 14:48:42 oh NetworkManager[894]: <info> (wlan0) supports 4 scan SSIDs
Nov 11 14:48:42 oh wpa_supplicant[1119]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 11 14:48:42 oh kernel: [   20.025572] init: samba-ad-dc main process (1027) terminated with status 1
Nov 11 14:48:43 oh NetworkManager[894]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Nov 11 14:48:43 oh ModemManager[747]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.2': not supported by any plugin
Nov 11 14:48:43 oh ModemManager[747]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0': not supported by any plugin
Nov 11 14:48:44 oh kernel: [   21.537880] r8169 0000:01:00.2 eth0: link up
Nov 11 14:48:44 oh kernel: [   21.537895] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 11 14:48:44 oh NetworkManager[894]: <info> (eth0): carrier now ON (device state 20)
Nov 11 14:48:44 oh NetworkManager[894]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov 11 14:48:44 oh NetworkManager[894]: <info> Auto-activating connection 'Wired connection 1'.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) starting connection 'Wired connection 1'
Nov 11 14:48:44 oh NetworkManager[894]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 11 14:48:44 oh NetworkManager[894]: <info> NetworkManager state is now CONNECTING
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 11 14:48:44 oh NetworkManager[894]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 11 14:48:44 oh NetworkManager[894]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Beginning IP6 addrconf.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 11 14:48:44 oh NetworkManager[894]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Nov 11 14:48:44 oh avahi-daemon[780]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.8.
Nov 11 14:48:44 oh avahi-daemon[780]: New relevant interface eth0.IPv4 for mDNS.
Nov 11 14:48:44 oh avahi-daemon[780]: Registering new address record for 192.168.2.8 on eth0.IPv4.
Nov 11 14:48:45 oh NetworkManager[894]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Nov 11 14:48:45 oh NetworkManager[894]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 11 14:48:45 oh NetworkManager[894]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Nov 11 14:48:45 oh avahi-daemon[780]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::faa9:63ff:fe07:c22d.
Nov 11 14:48:45 oh avahi-daemon[780]: New relevant interface eth0.IPv6 for mDNS.
Nov 11 14:48:45 oh avahi-daemon[780]: Registering new address record for fe80::faa9:63ff:fe07:c22d on eth0.*.
Nov 11 14:48:46 oh NetworkManager[894]: <info> NetworkManager state is now CONNECTED_GLOBAL
Nov 11 14:48:46 oh NetworkManager[894]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 11 14:48:46 oh NetworkManager[894]: <info> DNS: starting dnsmasq...
Nov 11 14:48:46 oh NetworkManager[894]: <warn> dnsmasq not available on the bus, can't update servers.
Nov 11 14:48:46 oh NetworkManager[894]: <error> [1415735326.248129] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Nov 11 14:48:46 oh NetworkManager[894]: <warn> DNS: plugin dnsmasq update failed
Nov 11 14:48:46 oh NetworkManager[894]: <info> Writing DNS information to /sbin/resolvconf
Nov 11 14:48:46 oh dnsmasq[1249]: started, version 2.68 cache disabled
Nov 11 14:48:46 oh dnsmasq[1249]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Nov 11 14:48:46 oh dnsmasq[1249]: DBus support enabled: connected to system bus
Nov 11 14:48:46 oh dnsmasq[1249]: warning: no upstream servers configured
Nov 11 14:48:47 oh NetworkManager[894]: <info> Activation (eth0) successful, device activated.
Nov 11 14:48:47 oh dbus[708]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 11 14:48:47 oh NetworkManager[894]: <warn> dnsmasq appeared on DBus: :1.11
Nov 11 14:48:47 oh NetworkManager[894]: <info> Writing DNS information to /sbin/resolvconf
Nov 11 14:48:47 oh dnsmasq[1249]: setting upstream servers from DBus
Nov 11 14:48:47 oh dnsmasq[1249]: using nameserver 8.8.8.8#53
Nov 11 14:48:47 oh dnsmasq[1249]: using nameserver 4.2.2.3#53
Nov 11 14:48:47 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 11 14:48:47 oh whoopsie[1081]: message repeated 2 times: [ offline]
Nov 11 14:48:47 oh whoopsie[1081]: online
Nov 11 14:48:48 oh dbus[708]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Nov 11 14:48:48 oh accounts-daemon[1436]: started daemon version 0.6.35
Nov 11 14:48:48 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.Accounts'
Nov 11 14:48:48 oh acpid: client connected from 1433[0:0]
Nov 11 14:48:48 oh acpid: 1 client rule loaded
Nov 11 14:48:49 oh kernel: [   26.195546] init: plymouth-upstart-bridge main process ended, respawning
Nov 11 14:48:49 oh kernel: [   26.206767] init: plymouth-upstart-bridge main process ended, respawning
Nov 11 14:48:51 oh NetworkManager[894]: <info> WiFi hardware radio set enabled
Nov 11 14:48:52 oh ntpdate[1358]: step time server 91.189.89.199 offset -1.466013 sec
Nov 11 14:48:53 oh dbus[708]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Nov 11 14:48:53 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.UPower'
Nov 11 14:48:54 oh dbus[708]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Nov 11 14:48:54 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Nov 11 14:48:54 oh anacron[1648]: Anacron 2.3 started on 2014-11-11
Nov 11 14:48:54 oh anacron[1648]: Normal exit (0 jobs run)
Nov 11 14:49:03 oh NetworkManager[894]: <info> (eth0): IP6 addrconf timed out or failed.
Nov 11 14:49:03 oh NetworkManager[894]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 11 14:49:03 oh NetworkManager[894]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 11 14:49:03 oh NetworkManager[894]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 11 14:49:08 oh kernel: [   47.043804] audit_printk_skb: 96 callbacks suppressed
Nov 11 14:49:08 oh kernel: [   47.043811] type=1400 audit(1415735348.450:44): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1748 comm="apparmor_parser"
Nov 11 14:49:08 oh kernel: [   47.043825] type=1400 audit(1415735348.450:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1748 comm="apparmor_parser"
Nov 11 14:49:08 oh kernel: [   47.044917] type=1400 audit(1415735348.450:46): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1748 comm="apparmor_parser"
Nov 11 14:49:29 oh dbus[708]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Nov 11 14:49:29 oh udisksd[1970]: udisks daemon version 2.1.3 starting
Nov 11 14:49:29 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Nov 11 14:49:29 oh udisksd[1970]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Nov 11 14:49:33 oh dbus[708]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Nov 11 14:49:33 oh colord: Using config file /etc/colord.conf
Nov 11 14:49:33 oh colord: Using mapping database file /var/lib/colord/mapping.db
Nov 11 14:49:33 oh colord: Using device database file /var/lib/colord/storage.db
Nov 11 14:49:33 oh colord: loaded plugin libcd_plugin_camera.so
Nov 11 14:49:33 oh colord: loaded plugin libcd_plugin_scanner.so
Nov 11 14:49:33 oh colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Nov 11 14:49:33 oh colord: Daemon ready for requests
Nov 11 14:49:34 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Nov 11 14:49:34 oh colord: Profile added: icc-ec2d29cf6e9f9409e9606a26dac39698
Nov 11 14:49:34 oh dbus[708]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Nov 11 14:49:34 oh dbus[708]: [system] Successfully activated service 'org.freedesktop.systemd1'
Nov 11 14:49:34 oh colord: Profile added: icc-a392a74919c54455cf25f7400b2319ac
Nov 11 14:49:34 oh colord: Profile added: icc-b0ddeb99aea00b3e6527017fe5b73803
Nov 11 14:49:34 oh colord: Profile added: icc-f3e0aad931efae878c9eba9125dc758f
Nov 11 14:49:34 oh colord: Profile added: icc-7fb30d688bf82d32a0e748daf3dba95d
Nov 11 14:49:34 oh colord: Profile added: icc-40e2a2d10e23e2777853990e7c80dbd6
Nov 11 14:49:34 oh colord: Profile added: icc-79e56e42bf930a269bb6a0421eb80753
Nov 11 14:49:34 oh colord: Profile added: icc-10080b14e236a5c33088e1d3404db83c
Nov 11 14:49:34 oh colord: Profile added: icc-d0f2748c6e21eee954827c71e1e81c12
Nov 11 14:49:34 oh colord: Profile added: icc-7cfad1a392b1ed7aaf7bd4cb60faaae4
Nov 11 14:49:34 oh colord: Profile added: icc-296f10aadb0eba217aa824dc712c8a07
Nov 11 14:49:34 oh colord: Profile added: icc-c90203802db7875c010cf0875c3ecac1
Nov 11 14:49:34 oh colord: Profile added: icc-186b88621ed8da652865e3e84836f85b
Nov 11 14:49:34 oh colord: Profile added: icc-14c5ddbb0abd000deb198c68bb185dc3
Nov 11 14:49:35 oh colord: Profile added: icc-71190e50549b40fd8fd2c1b6d407f0a9
Nov 11 14:49:35 oh colord: Profile added: icc-781f6f71344167d3526631689139f109
Nov 11 14:49:35 oh colord: Profile added: icc-e729b445abc89051fe8ba7c6d8e9b127
Nov 11 14:49:35 oh colord: Profile added: icc-1a00a956a836388ae20968e84f57d211
Nov 11 14:49:35 oh colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Nov 11 14:49:35 oh colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Nov 11 14:49:35 oh colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Nov 11 14:49:35 oh colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Nov 11 14:49:35 oh colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Nov 11 14:49:35 oh colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Nov 11 14:49:35 oh colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Nov 11 14:49:35 oh colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Nov 11 14:49:35 oh colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Nov 11 14:49:35 oh colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Nov 11 14:49:35 oh colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Nov 11 14:49:35 oh colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Nov 11 14:49:35 oh colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Nov 11 14:49:35 oh colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Nov 11 14:49:35 oh colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Nov 11 14:49:35 oh colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Nov 11 14:49:35 oh colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Nov 11 14:49:35 oh colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Nov 11 14:49:35 oh colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Nov 11 14:49:35 oh colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Nov 11 14:49:35 oh colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Nov 11 14:49:35 oh colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Nov 11 14:49:35 oh colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Nov 11 14:49:35 oh colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Nov 11 14:49:35 oh colord: Profile added: icc-07000710072007300740075007600770
Nov 11 14:49:35 oh colord: Profile added: icc-a71f743c68b0bf74d37a601835ca05cf
Nov 11 14:49:36 oh colord: Profile added: icc-aaafa3414484eb7d6a63b27b9d77223c
Nov 11 14:49:36 oh colord: Device added: xrandr-AU Optronics
Nov 11 14:50:20 oh dbus[708]: [system] Activating service name='org.debian.AptXapianIndex' (using servicehelper)
Nov 11 14:50:21 oh dbus[708]: [system] Successfully activated service 'org.debian.AptXapianIndex'

```

---

### Post by tgalati4 on 2014-11-13
Here's a patch that provides that warning.   [http://www.serverphorums.com/read.php?12,828165](http://www.serverphorums.com/read.php?12,828165)

GHES is sort of explained:  [https://bbs.archlinux.org/viewtopic.php?id=143064](https://bbs.archlinux.org/viewtopic.php?id=143064)

General Hardware Error Support (GHES)--it's possible that your board has a problem and the kernel doesn't know how to express it.

---

### Post by CyborgAlpha on 2014-11-13
Thanks
I think it's going to be slow going from here on out. Basically, if the system performs well, these are minor issues that will be noted and added to the work schedule.

---

### Post by tgalati4 on 2014-11-14
Cover the LED with electrical tape.

Perhaps more helpful:  look at the SATA options in BIOS.  Try different options to see if the LED light behavior changes.

---

