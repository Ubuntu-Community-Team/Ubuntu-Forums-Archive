---
title: "System random freezes"
date: 2018-07-08
forum: General Help
---

### Post by autumnsky on 2018-07-08
Hi everyone,

I'm facing an issue with my PC which freezes randomly. I have no idea what causes it.
I'm under Ubuntu Studio 16.04, I don't want to upgrade because I have no  problem other than that, I just want to keep my settings without new  issues.

It freezes when I use various audio programs. I think it's audio  related, because when I don't do any audio during a whole day, there is  nothing wrong happening. It can be while I record music using Ardour +  Jack ; sometimes it's only with audacity (after a certain time) ; or  when I'm streaming to Youtube using OBS software with a webcam + a mic.  CPU and memory don't overload.

When it happens : the mouse stops, time display freezes and so does the  screen (no black screen or else). Magic keys (activated) have no effect.  I'm simply obliged to use the reset button.

It's frustrating because when I restart the computer and read the system  logs, there is nothing written down. See below, yesterday it freezes at  16:23.

Any idea ?
Thank you for helping me :smile:

Jul  7 15:50:57 aurelien-MS-7641 kernel: [24429.004001] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
Jul  7 15:50:58 aurelien-MS-7641 kernel: [24430.234164] input: UVC  Camera (046d:081b) as  /devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/input/input9
Jul  7 15:50:58 aurelien-MS-7641 kernel: [24430.234776] usbcore: registered new interface driver uvcvideo
Jul  7 15:50:58 aurelien-MS-7641 kernel: [24430.234777] USB Video Class driver (1.1.1)
Jul  7 15:50:58 aurelien-MS-7641 pulseaudio[2194]: [pulseaudio] source.c: Default and alternate sample rates are the same.
Jul  7 15:51:02 aurelien-MS-7641 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jul  7 15:51:23 aurelien-MS-7641 kernel: [24454.800846] usb 1-1: reset high-speed USB device number 5 using ehci-pci
Jul  7 15:51:02 aurelien-MS-7641 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jul  7 16:04:10 aurelien-MS-7641 smartd[896]: Device: /dev/sda [SAT],  SMART Usage Attribute: 195 Hardware_ECC_Recovered changed from 50 to 49
Jul  7 16:17:01 aurelien-MS-7641 CRON[10396]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  7 16:30:13 aurelien-MS-7641 rsyslogd: [origin software="rsyslogd"  swVersion="8.16.0" x-pid="1117" x-info="http://www.rsyslog.com"] start
Jul  7 16:30:13 aurelien-MS-7641 rsyslogd-2222: command  'KLogPermitNonKernelFacility' is currently not permitted - did you  already set it via a RainerScript command (v6+ config)? [v8.16.0 try [http://www.rsyslog.com/e/2222](http://www.rsyslog.com/e/2222) ]
Jul  7 16:30:13 aurelien-MS-7641 rsyslogd: rsyslogd's groupid changed to 108
Jul  7 16:30:13 aurelien-MS-7641 rsyslogd: rsyslogd's userid changed to 104
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000] Linux version  4.4.0-130-lowlatency (buildd@lgw01-amd64-037) (gcc version 5.4.0  20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.9) ) #156-Ubuntu SMP PREEMPT Thu  Jun 14 09:45:55 UTC 2018 (Ubuntu 4.4.0-130.156-lowlatency 4.4.134)
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000] KERNEL supported cpus:
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   Intel GenuineIntel
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   AMD AuthenticAMD
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   NSC Geode by NSC
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   Cyrix CyrixInstead
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   Centaur CentaurHauls
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   Transmeta GenuineTMx86
Jul  7 16:30:13 aurelien-MS-7641 kernel: [    0.000000]   Transmeta TransmetaCPU

---

