---
title: "Boot process gone long/haywire"
date: 2018-07-24
forum: General Help
---

### Post by kazakore on 2018-07-24
Recently, I think since the last update that pulled down a kernel (-24 or whichever caused the other issues reported was fine on my machine.) I have a laptop with SSD and previously full boot would typically take less than 15 seconds, usually something around 12, with the occasional long boot. Now it always seems to be taking more like 3 minutes!

After logging in for a fair while I get this response

```
$ systemd-analyze blame
Bootup is not yet finished. Please try again later.

$ systemd-analyze time
Bootup is not yet finished. Please try again later.

```

When it eventually works I get.
```
~$ systemd-analyze time
Startup finished in 5.948s (firmware) + 2.531s (loader) + 38.034s (kernel) + 3min 1.873s (userspace) = 3min 48.388s
graphical.target reached after 1min 38.597s in userspace

```

But nothing shows as taking a long time here
```
$ systemd-analyze blame
          6.356s NetworkManager-wait-online.service
          3.009s resolvconf-pull-resolved.service
           819ms lm-sensors.service
           473ms dev-sda2.device
           345ms rtirq.service
           306ms rc-local.service
           269ms networkd-dispatcher.service
           258ms udisks2.service
           210ms accounts-daemon.service
           191ms systemd-journal-flush.service
           175ms NetworkManager.service
           173ms networking.service
           167ms loadcpufreq.service
           157ms upower.service
           151ms systemd-logind.service
           136ms apport.service
           135ms ModemManager.service
           133ms thermald.service
           133ms grub-common.service
           127ms systemd-modules-load.service
           126ms keyboard-setup.service
           123ms speech-dispatcher.service
           109ms systemd-udev-trigger.service
           106ms avahi-daemon.service
           103ms lightdm.service
            98ms gpu-manager.service
            96ms pppd-dns.service
            94ms wpa_supplicant.service
            93ms munin-node.service
            81ms iio-sensor-proxy.service
            77ms virtualbox.service
            76ms systemd-rfkill.service
            70ms ld10k1.service
            69ms apparmor.service
            68ms redis-server.service
            62ms media-dale-data.mount
            60ms ntopng.service
            59ms systemd-timesyncd.service
            58ms systemd-journald.service
            58ms systemd-resolved.service
            58ms sysfsutils.service
            56ms systemd-fsck@dev-disk-by\x2duuid-be07e4f2\x2d9d3f\x2d4157\x2db3af\x2dbb4ba093d0c3.service
            51ms systemd-fsck@dev-disk-by\x2duuid-A27D\x2d524E.service
            48ms alsa-restore.service
            41ms rsyslog.service
            37ms user@1000.service
            33ms systemd-udevd.service
            32ms polkit.service
            24ms cpufrequtils.service
            20ms hddtemp.service
            17ms kerneloops.service
            15ms resolvconf.service
            15ms boot-efi.mount
            15ms dev-mqueue.mount
            13ms kmod-static-nodes.service
            13ms ufw.service
            13ms systemd-sysctl.service
            13ms plymouth-read-write.service
            13ms sys-kernel-debug.mount
            12ms plymouth-start.service
            12ms dev-hugepages.mount
            11ms systemd-random-seed.service
            11ms systemd-remount-fs.service
            10ms colord.service
             9ms systemd-tmpfiles-setup.service
             9ms systemd-user-sessions.service
             8ms systemd-tmpfiles-setup-dev.service
             6ms systemd-update-utmp.service
             5ms proc-sys-fs-binfmt_misc.mount
             5ms openvpn.service
             5ms sys-kernel-config.mount
             4ms systemd-update-utmp-runlevel.service
             4ms sys-fs-fuse-connections.mount
             4ms ureadahead-stop.service
             3ms systemd-backlight@backlight:intel_backlight.service
             3ms rtkit-daemon.service
             2ms tmp.mount
             2ms console-setup.service
             1ms setvtrgb.service
             1ms plymouth-quit-wait.service

```

And although my computer wasn't doing any heavy processing the fans kicked in and I have high temp alarms from a few minutes after the userspace sessions was ready.
dmesg : [https://paste.ubuntu.com/p/f4rQmFbkDB/](https://paste.ubuntu.com/p/f4rQmFbkDB/)

Any idea what might be doing on?

```
$ uname -srv
Linux 4.15.0-29-lowlatency #31-Ubuntu SMP PREEMPT Tue Jul 17 17:49:04 UTC 2018

```

EDIT
systemd-analyse plot attached.[ATTACH]280492[/ATTACH]

---

### Post by kazakore on 2018-07-25
No ideas??? To me that systemd plot looks very suspicious! Especially with nothing actually showing as taking any considerable time, so why the delay?!?

---

### Post by kazakore on 2018-07-25
Just noticed on booting a line similar to:
```

/dev/sda2: clean, xxxxx/xxxxx files, yyyyy/yyyyy blocks zzsec / 1m30sec
```

The numbers show don't seem to update when I get the page to redisplay and it reaches the 1min30 and then just stops.

sda2 is my root / partition of the Studio install and from [This Thread](https://askubuntu.com/questions/761653/startup-problem-in-16-04) it seems it may be running a fdsk every time I boot the system for some reason.

Any idea why it may be doing this and how to stop it?

I did a dist-upgrade to the -29 kernel just before the fault started, but I also installed another (Debian-based) distro on another partition of the drive at about the same time. I wonder if either of these actions may be related...

---

### Post by kazakore on 2018-07-25
Yeah jouralctl shows issues with the drives, yet all are as expected once it has actually started up. What is going on here?!?!

```
-- 
-- Unit resolvconf-pull-resolved.service has finished starting up.
-- 
-- The start-up result is RESULT.
Jul 25 14:03:28 ThisOne systemd[1]: dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device: Job dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device/start timed out.
Jul 25 14:03:28 ThisOne systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device.
-- Subject: Unit dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device has failed.
-- 
-- The result is RESULT.
Jul 25 14:03:28 ThisOne systemd[1]: Dependency failed for /dev/disk/by-uuid/4d281b03-f778-45f7-8783-a7bfdd328146.
-- Subject: Unit dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.swap has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.swap has failed.
-- 
-- The result is RESULT.
Jul 25 14:03:28 ThisOne systemd[1]: dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.swap: Job dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.swap/start failed with result 'dependency'.
Jul 25 14:03:28 ThisOne systemd[1]: Startup finished in 5.899s (firmware) + 3.411s (loader) + 6.801s (kernel) + 3min 1.770s (userspace) = 3min 17.882s.
-- Subject: System start-up is now complete
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- All system services necessary queued for starting at boot have been
-- started. Note that this does not mean that the machine is now idle as services
-- might still be busy with completing start-up.
-- 
-- Kernel start-up required 6801325 microseconds.
-- 
-- Initial RAM disk start-up required INITRD_USEC microseconds.
-- 
-- Userspace start-up required 181770937 microseconds.
Jul 25 14:03:28 ThisOne systemd[1]: dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device: Job dev-disk-by\x2duuid-4d281b03\x2df778\x2d45f7\x2d8783\x2da7bfdd328146.device/start failed with result 'timeout'.
Jul 25 14:03:58 ThisOne dbus-daemon[1239]: [session uid=1000 pid=1239] Activating service name='org.gnome.GConf' requested by ':1.79' (uid=1000 pid=2613 comm="/opt/waterfox/waterfox " label="unconfined")
Jul 25 14:03:58 ThisOne dbus-daemon[1239]: [session uid=1000 pid=1239] Successfully activated service 'org.gnome.GConf'
Jul 25 14:05:01 ThisOne CRON[2751]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 14:05:01 ThisOne CRON[2750]: pam_unix(cron:session): session opened for user munin by (uid=0)
Jul 25 14:05:01 ThisOne CRON[2752]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Jul 25 14:05:01 ThisOne CRON[2753]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)
Jul 25 14:05:01 ThisOne CRON[2751]: pam_unix(cron:session): session closed for user root
Jul 25 14:05:10 ThisOne CRON[2750]: pam_unix(cron:session): session closed for user munin
Jul 25 14:10:01 ThisOne CRON[3282]: pam_unix(cron:session): session opened for user munin by (uid=0)
Jul 25 14:10:01 ThisOne CRON[3283]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 25 14:10:01 ThisOne CRON[3284]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Jul 25 14:10:01 ThisOne CRON[3285]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)
Jul 25 14:10:01 ThisOne CRON[3283]: pam_unix(cron:session): session closed for user root
Jul 25 14:10:09 ThisOne CRON[3282]: pam_unix(cron:session): session closed for user munin
Jul 25 14:10:54 ThisOne gvfsd-metadata[2060]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Jul 25 14:10:54 ThisOne gvfsd-metadata[2060]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Jul 25 14:10:54 ThisOne dbus-daemon[1239]: [session uid=1000 pid=1239] Activating via systemd: service name='org.gnome.evince.Daemon' unit='evince.service' requested by ':1.81' (uid=1000 pid=3800 comm="evince /tmp/mozilla_dale0/westermo_ug_6643-2213_ly" 
Jul 25 14:10:54 ThisOne systemd[1187]: Starting Evince document viewer...
-- Subject: Unit UNIT has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit UNIT has begun starting up.
Jul 25 14:10:54 ThisOne dbus-daemon[1239]: [session uid=1000 pid=1239] Successfully activated service 'org.gnome.evince.Daemon'
Jul 25 14:10:54 ThisOne systemd[1187]: Started Evince document viewer.
-- Subject: Unit UNIT has finished start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit UNIT has finished starting up.
```

rc-local.service seems to be failing as well although it does seem to be being applied.

```
-- Unit rc-local.service has begun starting up.
Jul 25 14:33:43 ThisOne rc.local[6177]: Warning: `/etc/wireguard/mullvad-gb1.conf' is world accessible
Jul 25 14:33:43 ThisOne rc.local[6177]: wg-quick: `mullvad-gb1' already exists
Jul 25 14:33:43 ThisOne systemd[1]: rc-local.service: Control process exited, code=exited status=1
Jul 25 14:33:43 ThisOne systemd[1]: rc-local.service: Failed with result 'exit-code'.
Jul 25 14:33:43 ThisOne systemd[1]: Failed to start /etc/rc.local Compatibility.
-- Subject: Unit rc-local.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit rc-local.service has failed.
-- 
-- The result is RESULT.
Jul 25 14:33:43 ThisOne polkitd(authority=local)[983]: Unregistered Authentication Agent for unix-process:6164:199965 (system bus name :1.78, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)

```

---

### Post by kazakore on 2018-07-25
Fixed.

When I had installed the other OS and used the same Swap for some reason it had given it a new UUID.

Despite the above saying it related to sda2, which is root /, I edited the line for swap on sda5 in /etc/fstab and I'm back to nice quick startup. (Actually both showed up in the longer log but only saw sda2 reference on screen during boot time.)

```
$ systemd-analyze time
Startup finished in 5.897s (firmware) + 1.609s (loader) + 6.801s (kernel) + 9.100s (userspace) = 23.409s
graphical.target reached after 9.093s in userspace

```

---

