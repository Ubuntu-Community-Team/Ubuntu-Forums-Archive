---
title: "kjournald high cpu &amp; md disappearing"
date: 2008-05-18
forum: General Help
---

### Post by wiz561 on 2008-05-18
Hi!

I'm having a problem with my ubuntu installation.  I've been running 8.04 now for a month or two.  Fairly recently, I've noticed a lot of disk activity for no apprent reason.  Doing a 'top' shows kjournald running with a rather high cpu utilization...

--------
top - 20:07:30 up 6 min,  2 users,  load average: 2.00, 1.67, 0.85
Tasks:  91 total,   2 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us, 12.6%sy,  0.0%ni, 50.0%id, 35.1%wa,  0.0%hi,  1.1%si,  0.0%st
Mem:   1028508k total,   444728k used,   583780k free,   137568k buffers
Swap:  3132624k total,        0k used,  3132624k free,   172432k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                   
 2622 root      15  -5     0    0    0 D   18  0.0   1:08.51 kjournald 
----------

During a reboot, syslog shows this...

---
May 18 20:01:13 scooby mdadm: DeviceDisappeared event detected on md device /dev/md1, component device Wrong-Level
May 18 20:01:13 scooby mdadm: DeviceDisappeared event detected on md device /dev/md0, component device Wrong-Level
---

I am running raid0, btw.  

Just wondering what in the world is going on with my box.  I've saw a few postings about kjournald and doing something with the niceness of it.  But I'm a little leary about making changes to it if there's something else going on with it.


Thanks in advance...

---

