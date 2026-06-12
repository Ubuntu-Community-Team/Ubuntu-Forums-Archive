---
title: "systemd code=? status=? help"
date: 2018-04-04
forum: General Help
---

### Post by mstjohn1974 on 2018-04-04
Hello,

I am having an issue with one of my servers and I cannot find and answer to it. I have a service which looks to me like it is crashing but I cannot confirm it. Here is the log snippet:
Apr  4 06:58:05 myserver systemd[1]: kerio-connect.service: Main process exited, code=killed, status=6/ABRT
Apr  4 06:58:06 myserver systemd[1]: kerio-connect.service: Unit entered failed state.
Apr  4 06:58:06 myserver systemd[1]: kerio-connect.service: Failed with result 'signal'.
Apr  4 06:58:06 myserver systemd[1]: kerio-connect.service: Service hold-off time over, scheduling restart.
Apr  4 06:58:06 myserver systemd[1]: Stopped Kerio Connect.
Apr  4 06:58:06 myserver systemd[1]: Starting Kerio Connect...
Apr  4 06:58:06 myserver systemd[1]: kerio-connect.service: PID file /var/run/kms.pid not readable (yet?) after start: No such file or directory
Apr  4 06:58:25 myserver systemd[1]: Started Kerio Connect.
Apr  4 06:58:26 myserver kernel: [156128.041138] sysctl_ibrs_enabled = 0, sysctl_ibpb_enabled = 0
Apr  4 06:58:26 myserver kernel: [156128.041141] use_ibrs = 4, use_ibpb = 4
Apr  4 06:58:26 myserver kernel: [156128.041142] read cpu 0 ibrs val 0
Apr  4 06:58:26 myserver kernel: [156128.041144] sysctl_ibrs_enabled = 0, sysctl_ibpb_enabled = 0
Apr  4 06:58:26 myserver kernel: [156128.041145] use_ibrs = 4, use_ibpb = 4
Apr  4 06:58:26 myserver kernel: [156128.041146] read cpu 0 ibrs val 0

In the first line where it says Main process exited, code=killed, status=6/ABRT does that actually mean it crashed or that someone or something initiated the service to stop? I tried to find a source on the internet that could explain those codes and statuses to me and what could cause it but I was unsuccessful. 

Anybody have an idea how to go about this issue? Any help is highly appreciated. Thank you

---

### Post by dino99 on 2018-04-04
if a crash have happended, then a crash file is logged into /var/crash/
you can grab warnings/errors via 'journalctl -b' to better understand the problem

Should be helpful to know about the kernel/DE  used

---

### Post by mstjohn1974 on 2018-04-04
Thank you Dino99,

the journalctl I already ran, thats where I got the log snippet from but thanks for the location of the crash dumps...I indeed found one from a few days ago. I'll see if it makes some sense to me.

---

