---
title: "systemd-fsckd.service Running Way Too Long at Bootup"
date: 2016-07-11
forum: General Help
---

### Post by Alpha_Kilo on 2016-07-11
I've installed Lubuntu 16.04 on an Acer Cloudbook 14.  It runs great.  I'm very happy with it.  The only problems I have are very slow boot times and hanging at shutdown.  Running system-analyze tells me

```
mobile@mobile-1:~$ systemd-analyze
Startup finished in 2min 32.240s (kernel) + 3.443s (userspace) = 2min 35.684s

```

Blame doesn't show anything taking nearly that long:

```
mobile@mobile-1:~$ sudo systemd-analyze blame
[sudo] password for mobile: 
          1.042s dev-mmcblk0p5.device
           855ms networking.service
           806ms accounts-daemon.service
           770ms ModemManager.service

```

Running the following plot command shows systemd-fsckd.service is running the entire 158 seconds of boot time.

```

mobile@mobile-1:~$ systemd-analyze plot > plot.svg

```

My theory is that fsck is running at boot time because I'm never able to properly shutdown.  Whenever I shutdown, whether I use "shutdown -h now" at the prompt or through LXDE it always hangs - the machine never powers down.  To power off the machine I have to hold down the power button for about 5 seconds.  So I think that next time I boot up it's running fsck to check the disk since it possibly wasn't properly unmounted.

A couple of questions:
[LIST=1]
[*]Any holes in my theory?
[*]How am I suppose to analyze and debug the shutdown issue?  I know I can use dmesg for boot logs, but not sure how to see shutdown...
[/LIST]

---

