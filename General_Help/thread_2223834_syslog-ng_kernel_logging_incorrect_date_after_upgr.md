---
title: "syslog-ng kernel logging incorrect date after upgrade to 14.04"
date: 2014-05-13
forum: General Help
---

### Post by RoryH on 2014-05-13
So I had a 12.04 (precise) server which I decided to upgrade to 14.04 (trusty)... After the update and getting syslog-ng back up and running, I'm seeing some strange behaviour in the logs. Basically any log messages from the kernel have completely the wrong date, It's out by about 23 days! ...so I guess it's not a timezone issue.

For reference, here's my server time:

```
$ date
Tue May 13 08:54:30 UTC 2014
```

Here's a sample of my logs from yesterday... you can see the entries for "May 12" (correct), but messages from my kernel have the date "Jun 5" (vastly incorrect):

```
May 12 14:41:29 XXX-server syslog-ng[6060]: syslog-ng starting up; version='3.5.3'May 12 14:41:29 XXX-server syslog-ng[6060]: EOF on control channel, closing connection;May 12 14:44:44 XXX-server rory: System test
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process (6254) terminated with status 1
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process (6265) terminated with status 1
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process (6276) terminated with status 1
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process (6287) terminated with status 1
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process (6298) terminated with status 1
Jun  5 09:10:51 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process (6309) terminated with status 1
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process (6320) terminated with status 1
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process (6331) terminated with status 1
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process ended, respawning
Jun  5 09:10:52 XXX-server kernel: init: squid3 main process (6342) terminated with status 1
```

This is not causing me any other problems, but it's something I;d like to fix... anyone got any ideas?

---

### Post by RoryH on 2014-05-19
bump! anybody have any ideas?

---

### Post by Joe_CoT on 2014-07-22
I'm having the exact same issue. For me it's logging entries for today (July 22nd) as Sep 23.

Do you happen to be running on EC2?

---

### Post by Joe_CoT on 2014-07-28
I've tracked down the source. The issue is the dmesg time jumping. Example here:

```

[    0.000000] Xen version: 3.4.3.amazon (preserve-AD)
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: 
[    0.000000] pcpu-alloc:
[    0.000000] pcpu-alloc: [0] 0 
[7493812.749226] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 430298
[7493812.749229] Policy zone: DMA32
[7493812.749232] Kernel command line: root=LABEL=cloudimg-rootfs ro console=hvc0 
[7493812.750892] PID hash table entries: 4096 (order: 3, 32768 bytes)
[7493812.750945] Checking aperture...
[7493812.760330] No AGP bridge found

```

The problem is discussed here:
[https://forums.aws.amazon.com/thread.jspa?threadID=59753](https://forums.aws.amazon.com/thread.jspa?threadID=59753)

Supposedly it was already fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459)

I'm going to guess that the fix is broken again in 14.04

---

### Post by Joe_CoT on 2014-07-28
Made a post about it in the Virtualization section over here:
[http://ubuntuforums.org/showthread.php?t=2236742&p=13085273](http://ubuntuforums.org/showthread.php?t=2236742&p=13085273)

---

### Post by Joe_CoT on 2014-07-28
Kernel bug reopened here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/727459)

---

### Post by Joe_CoT on 2014-07-28
For right now, you can work around this by telling syslog-ng to ignore the timestamp for the kernel logs.
Change this:
```

source s_src {
	system();
	internal();
};

```
to this:
```

source s_src {
	unix-dgram("/dev/log");
	file("/proc/kmsg" program-override("kernel") flags(kernel) keep_timestamp(no));
	internal();
};

```

Basically, separate out the system() call to be what it's actually getting the info from on linux servers (as explained [here](http://www.balabit.com/sites/default/files/documents/syslog-ng-ose-3.3-guides/en/syslog-ng-ose-v3.3-guide-admin-en/html/configuring-source-system.html)), and tell it to ignore the timestamp for the kernel logs.

That means that kernel logs will be logged for the time they're received by syslog-ng, which means that on start up, all the kernel logs will be recorded as the same second syslog-ng starts. Not ideal. Better than logging for months in the future.

---

### Post by Joe_CoT on 2014-07-29
Asked to open a new bug for this. If you're affected by this bug, please login and click "this bug also affects me" to say so.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1349883](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1349883)

---

