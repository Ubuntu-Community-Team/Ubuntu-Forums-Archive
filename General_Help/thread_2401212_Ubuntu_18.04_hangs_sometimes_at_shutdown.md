---
title: "Ubuntu 18.04 hangs sometimes at shutdown"
date: 2018-09-15
forum: General Help
---

### Post by warhammer365 on 2018-09-15
So, I installed Ubuntu 18.04 recently alongside my Windows 7 OS. Ever since the install I have been facing this issue where I my Laptop hangs at shutdown. The splash screen is seen and then the blank screen appears. Which SHOULD mean the laptop has shutdown. But the light that indicates power on(on the side of my lappy) is still on. I always have to hold down the power button for 5 seconds for it to completely shutdown.

I tried using journalctlbut it looks pretty much normal to me (I'm relatively new to linux):
```
Sep 15 12:45:11 warhammer-PC systemd[1]: Deactivated swap /dev/sda6.
Sep 15 12:45:11 warhammer-PC systemd[1]: Deactivated swap /dev/disk/by-uuid/8d13e2b7-a4cd-472b-8a80-
Sep 15 12:45:11 warhammer-PC systemd[1]: Reached target Unmount All Filesystems.
Sep 15 12:45:11 warhammer-PC systemd[1]: Reached target Final Step.
Sep 15 12:45:11 warhammer-PC systemd[1]: Starting Reboot...
Sep 15 12:45:11 warhammer-PC systemd[1]: Shutting down.
Sep 15 12:45:11 warhammer-PC kernel: systemd-shutdow: 22 output lines suppressed due to ratelimiting
Sep 15 12:45:11 warhammer-PC systemd-shutdown[1]: Syncing filesystems and block devices.
Sep 15 12:45:12 warhammer-PC systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Sep 15 12:45:12 warhammer-PC systemd-journald[269]: Journal stopped

```

and my laptop is Hp 15-r250 tu

---

### Post by Dennis N on 2018-09-15
Wait up to 2 minutes and see if it shuts itself down. If it does, there is an intermittent bug which can cause such a delay. Usually there is a one line message starting with "a stop job is running..." but sometimes may just be a blank screen. 

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

If it doesn't shut down itself in 2 min. time, you have a different problem.

(I had this problem with my Uubntu 18.04, but it seems to have gone now. Haven't seen it for probably a month.)

---

### Post by warhammer365 on 2018-09-16
Thanks for reply.
Okay, so I tried that. waited for more than 5 minutes or so. Didnt seem to work.

---

### Post by warhammer365 on 2018-09-16
Although I did get an idea from your reply. So I went to the grub file and changed :
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to:
```

GRUB_CMDLINE_LINUX_DEFAULT=""

```
 AND IT SEEMS TO WORK.
 I also tried "quiet" and "splash" sepeartely but then the laptop hangs again.
So, changing it to "" temporarily does solve my problem but I still would like to know What the f is wrong with my laptop, and how to fix this.

---

