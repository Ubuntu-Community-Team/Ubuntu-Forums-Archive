---
title: "Suspend/Resume does not work on an old laptop"
date: 2018-03-24
forum: General Help
---

### Post by karmey on 2018-03-24
Hello everyone,

When I suspend and resume my laptop, one CPU core remains constantly loaded at ~70%, and moreover, I can't suspend again.

Hardware: ~10 years old Asus laptop with dual-core CPU, 4 Gb RAM, AMD Radeon graphics adapter.
Software: Ubuntu 16.04; also tried Xubuntu 16.04, it has the same problem. The laptop had run Windows 7 for years, and suspension worked fine.

Simplest way to reproduce I've found:
1. Boot from Ubuntu installation DVD.
2. Choose "Try Ubuntu".
3. Suspend.
4. Resume.

--> the laptop resumes, and has a high CPU load. Output of cpustat:
```

%CPU   %USR   %SYS   PID S  CPU   Time Task
 67.33   0.00  67.33  6274 R    1  1.91m [kworker/1:0H]
 32.67   0.00  32.67    16 R    1  2.91m [ksoftirqd/1]
  4.95   3.96   0.99  4203 R    0 25.06s /usr/lib/xorg/Xorg
  2.97   1.98   0.99  4711 S    0 18.66s compiz
  1.98   0.99   0.99  5947 S    0  9.99s gnome-system-monitor
  0.99   0.00   0.99  7011 S    0  0.04s [kworker/u4:2]
  0.99   0.00   0.99  7347 R    0  0.01s cpustat

```

5. Suspend.
--> the screen turns off, but the laptop doesn't stop at all; after some time the screen turns on. Output of dmesg:
```

[ 1070.607461] Freezing remaining freezable tasks ...
[ 1090.610525] Freezing of tasks failed after 20.003 seconds (0 tasks refusing to freeze, wq_busy=1):
[ 1090.610530] Showing busy workqueues and worker pools:
[ 1090.610532] workqueue events_freezable_power_: flags=0x86
[ 1090.610533]   pwq 4: cpus=0-1 flags=0x4 nice=0 active=1/0
[ 1090.610539]     in-flight: 5681:disk_events_workfn
[ 1090.610549]     delayed: disk_events_workfn, disk_events_workfn
[ 1090.610556] workqueue kblockd: flags=0x18
[ 1090.610557]   pwq 3: cpus=1 node=0 flags=0x0 nice=-20 active=1/256
[ 1090.610562]     in-flight: 6274:scsi_requeue_run_queue
[ 1090.610575] pool 3: cpus=1 node=0 flags=0x0 nice=-20 hung=0s workers=2 idle: 4834
[ 1090.610580] pool 4: cpus=0-1 flags=0x4 nice=0 hung=4s workers=4 idle: 7355 5684 7011
[ 1090.610673] Restarting kernel threads ... done.
[ 1090.610859] OOM killer enabled.
[ 1090.610860] Restarting tasks ... done.
[ 1090.666141] video LNXVIDEO:00: Restoring backlight state
[ 1090.674799] IPv6: ADDRCONF(NETDEV_UP): enp0s4: link is not ready
[ 1090.725820] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 1090.744030] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

```

I guess, after a resume, something in the kernel keeps running, loading the CPU and preventing the laptop from suspending again. But I don't have enough knowledge to debug it further. Would be grateful for any help.

---

### Post by TheFu on 2018-03-24
I'd verify that the BIOS version fully supports the required spec.

In the BIOS, which of the suspend wake options are enabled? I think there are 3.

Vendors test suspend on Windows.  They usually don't test anything on Linux.  Suspend is working well on my chromebook running 16.04, BTW. I use it every night just after running backups on the machine.  
Some settings are in /etc/systemd/logind.conf  There is a manpage for logind.conf too that has multiple references to suspend.

---

### Post by karmey on 2018-03-25
Thanks for your answer. Looked in BIOS, but there is no suspend mode option on my laptop.

I searched more in the internet and found that there is a workaround; someone has already had the same problem, and figured out that it's related to the DVD drive. If the drive is disconnected, the problem doesn't happen. That works for me.

For those who may have the same problem with suspending/resuming Ubuntu/Linux on ASUS X59SL: disable the DVD drive as described in this answer on Ask Ubuntu: [https://askubuntu.com/a/387261](https://askubuntu.com/a/387261) (physically disconnecting the drive also helps).

---

### Post by TheFu on 2018-03-25
Thanks for posting the likely answer.   Please mark this thread as SOLVED - thread tools near top - to help the community.

The takeaway for this is that with any laptop, **always look for solution specific for that model laptop.** 

Laptops can be extremely picky about things for a number of reasons, like they are trying to save battery. Sometimes the designers come up with really innovative/odd solutions and let the drivers deal with any issues later.  Drivers are OS-specific and many vendors don't attempt to do much with their Linux drivers, if anything.
[B]
Whenever posting questions related to laptops, it is very important to include the model.[/B]

---

### Post by karmey on 2018-03-25
Sure, thanks for explaining. Will keep that in mind.

---

