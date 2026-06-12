---
title: "computer reboots by itself for no reason"
date: 2016-11-07
forum: General Help
---

### Post by Shobuz99 on 2016-11-07
Briefly, my Dell Inspiron 1525 with Ubuntu 14.04 LTS reboots  by itself for no reason.
Every day when I power on the laptop, it boots normally and then arrives at the login screen.
But it doesn't sit there long. I hear a click or "pop" sound and then it reboots as though from a cold start.
Sometimes if I don't touch it, it will go through 3 cycles of boot, finish and restart in the space of 5 minutes.
However, if I intervene, and enter my login password and get to the desktop screen, it doesn't re-boot again.
Why?

I have checked out the hardware. I've run Dell diagnostics and everything passes flawlessly.
I've shutdown, removed power and removed the battery several times. No change.
I've removed the keyboard and the top section that covers the power button and circuitry underneath.
Nothing is out of the ordinary, except one thing: 
The indicator light for the Scroll Lock goes on and off when I open or close the laptop. 
I can't control the Scroll Lock to make it stay off.
But the Scroll Lock feature doesn't seem to work at all, anyway.

I've run Clamscan several times and found nothing. No infections at all.

I didn't know what section of this forum to post this, because I'm not sure what it applies to most. 
If anyone has any suggestions or has seen this occur with Ubuntu 14.04 LTS I'd like to hear from you.

Thank you for your help.
Rick (Shobuz99)

---

### Post by ian-weisser on 2016-11-08
There is _no_ way to trigger an Ubuntu reboot without logging the action in /var/log/syslog.
So note the exact time of a reboot, and look in that logfile for clues.

If there are no clues in that logfile, then your 'hardware diagnostics' are incomplete or incorrect - you have some kind of hardware failure.

---

### Post by Shobuz99 on 2016-11-08
Thank you Ian-weisser. 
I have also looked at /var/log/syslog for clues and was able to find the time of the re-boot. 
But I didn't really know what to look for, in terms of a message that gave me a specific statement that the machine rebooted.
If it was there, what would be the possible "wording" of the message technically?

If it's not software, then I agree that it must be a hardware issue.
I'll reply with my investigation results from the /var/log/syslog the next time it re-boots by itself.
thanks again.

Rick

---

### Post by ian-weisser on 2016-11-08
The log would say something like "System going down for reboot" or "Reboot signal sent by Frobozz", or something similar.
Indeed, there should be all-kinds of pre-shutdown or pre-reboot messages. Try a deliberate shutdown or reboot and see the difference in the logfiles,

---

### Post by Shobuz99 on 2016-11-09
> **ian-weisser said:**
> The log would say something like "System going down for reboot" or "Reboot signal sent by Frobozz", or something similar.
Indeed, there should be all-kinds of pre-shutdown or pre-reboot messages. Try a deliberate shutdown or reboot and see the difference in the logfiles,

Thank you. That's a great idea. I will try it. 
But I think going through a shutdown-restart from the top right, will not really simulate what's happening...will it?

In the meantime I did have a reboot occur when I was typing in my password this morning following the first cold boot.
I remembered the time that it happened (8:40am) and have found the syslog file with the exact time that it occurred.
I put the section of the log file that appears to show the difference here:

```

[COLOR="#0000CD"]Nov  9 00:05:38 robotics1949-Inspiron-1525 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="823" x-info="http://www.rsyslog.com"] exiting on signal 15.[/COLOR]
[COLOR="#B22222"]Nov  9 08:39:41 robotics1949-Inspiron-1525 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="838" x-info="http://www.rsyslog.com"] start
Nov  9 08:39:41 robotics1949-Inspiron-1525 rsyslogd: rsyslogd's groupid changed to 104
Nov  9 08:39:41 robotics1949-Inspiron-1525 rsyslogd: rsyslogd's userid changed to 101
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] Linux version 4.4.0-45-generic (buildd@lgw01-30) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) ) #66~14.04.1-Ubuntu SMP Wed Oct 19 15:07:39 UTC 2016 (Ubuntu 4.4.0-45.66~14.04.1-generic 4.4.21)
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] KERNEL supported cpus:
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   Intel GenuineIntel
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   AMD AuthenticAMD
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   NSC Geode by NSC
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   Cyrix CyrixInstead
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   Centaur CentaurHauls
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   Transmeta GenuineTMx86
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   Transmeta TransmetaCPU
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000]   UMC UMC UMC UMC
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] x86/fpu: Legacy x87 FPU detected.
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf66d7ff] usable
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000bf66d800-0x00000000bfffffff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed1bfff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed8ffff] reserved
Nov  9 08:39:41 robotics1949-Inspiron-1525 kernel: [    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000fedaNov  9 08:40:38 robotics1949-Inspiron-1525 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="824" x-info="http://www.rsyslog.com"] start [/COLOR]
[COLOR="#008000"]Nov  9 08:40:38 robotics1949-Inspiron-1525 rsyslogd: rsyslogd's groupid changed to 104
Nov  9 08:40:38 robotics1949-Inspiron-1525 rsyslogd: rsyslogd's userid changed to 101
Nov  9 08:40:38 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  9 08:40:38 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  9 08:40:38 robotics1949-Inspiron-1525 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  9 08:40:38 robotics1949-Inspiron-1525 kernel: [    0.000000] Linux version 4.4.0-45-generic (buildd@lgw01-30) (gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) ) #66~14.04.1-Ubuntu SMP Wed Oct 19 15:07:39 UTC 2016 (Ubuntu 4.4.0-45.66~14.04.1-generic 4.4.21)[/COLOR] 
```

The line in [COLOR="#0000CD"]Blue[/COLOR] is the last line before shutdown after midnight..
The lines in [COLOR="#B22222"]Red[/COLOR] begin the first boot at 8:39:41 this morning when I started it up.
The lines in [COLOR="#008000"]Green[/COLOR] represent about a minute difference between the last red line and then the re-boot,I assume.

I don't see any real signs of the reboot being logged. 
Let me know what you think and if it changes your recommendation.

Again, thank you kindly..

Rick

---

### Post by ian-weisser on 2016-11-09
You clearly have faulty hardware.

---

### Post by Shobuz99 on 2016-11-10
> **ian-weisser said:**
> You clearly have faulty hardware.

I agree, now. Thank you. I'll mark this solved.

Rick (Shobuz99)

---

