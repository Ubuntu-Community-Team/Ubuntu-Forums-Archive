---
title: "Ubuntu 19.04 hangs on shutdown"
date: 2019-06-16
forum: General Help
---

### Post by habana on 2019-06-16
I performed a clean installation of 19.04 on my desktop computer in April. The system was working well until I experienced a hardware failure a couple of weeks ago. As the motherboard was 7 years old (Gigabyte B75M-D3H), I replaced the motherboard, PSU, CPU and RAM. The new motherboard is a Gigabyte B360M HD3 with the latest BIOS. I retained the Samsung SSD which is fairly new and the HDD on which I store data. I use internal graphics, there are no add-on cards.

The new system immediately booted up OK but on shutdown the system hangs on the splash screen. Attempting to shut down by ```
shutdown -P
``` produces a black screen with a blinking cursor. In both cases I have to use the power button to shut down.

The B360M BIOS screen is very similar to the old B75 screen. The main difference in relation to power  is "Platform Power Management" on the newer board. This is disabled by default. "Power on by keyboard" and all similar options are disabled.

It may or may not be relevant but Xsensors freezes on the new system. I have rerun sensors detect and removed the old entries from /etc/modules but to no effect. I don't think lmsensors will be much use to me now as the new motherboard hardware sensor chip is not supported as far as I can ascertain. I am not too concerned with that at this stage.

Any help on the shutdown problem would be appreciated.

---

### Post by habana on 2019-06-18
Bump

---

### Post by habana on 2019-06-19
After attempting to shut down via the normal pull down menu, here are the last few lines of ```
journalctl -b -1
```

It looks pretty normal to me except of course the power doesn't go off.

```
Jun 19 09:36:44 computer2 systemd[1]: Unmounted Mount unit for gtk-common-themes, revision 1198.
Jun 19 09:36:44 computer2 systemd[1]: snap-core-6673.mount: Succeeded.
Jun 19 09:36:44 computer2 systemd[1]: Unmounted Mount unit for core, revision 6673.
Jun 19 09:36:44 computer2 systemd[1]: Reached target Unmount All Filesystems.
Jun 19 09:36:44 computer2 systemd[1]: Stopped target Local File Systems (Pre).
Jun 19 09:36:44 computer2 systemd[1]: systemd-tmpfiles-setup-dev.service: Succeeded.
Jun 19 09:36:44 computer2 systemd[1]: Stopped Create Static Device Nodes in /dev.
Jun 19 09:36:44 computer2 systemd[1]: systemd-sysusers.service: Succeeded.
Jun 19 09:36:44 computer2 systemd[1]: Stopped Create System Users.
Jun 19 09:36:44 computer2 systemd[1]: systemd-remount-fs.service: Succeeded.
Jun 19 09:36:44 computer2 systemd[1]: Stopped Remount Root and Kernel File Systems.
Jun 19 09:36:44 computer2 systemd[1]: Reached target Shutdown.
Jun 19 09:36:44 computer2 systemd[1]: Reached target Final Step.
Jun 19 09:36:44 computer2 systemd[1]: systemd-poweroff.service: Succeeded.
Jun 19 09:36:44 computer2 systemd[1]: Started Power-Off.
Jun 19 09:36:44 computer2 systemd[1]: Reached target Power-Off.
Jun 19 09:36:44 computer2 systemd[1]: Shutting down.
Jun 19 09:36:44 computer2 kernel: printk: systemd-shutdow: 73 output lines suppressed due to ratelimiting
Jun 19 09:36:44 computer2 systemd-shutdown[1]: Syncing filesystems and block devices.
Jun 19 09:36:44 computer2 systemd-shutdown[1]: Sending SIGTERM to remaining processes...
Jun 19 09:36:44 computer2 systemd-journald[368]: Journal stopped
```

---

