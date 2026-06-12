---
title: "Some systemd user services started even before login"
date: 2021-04-18
forum: General Help
---

### Post by 0x656b694d on 2021-04-18
Hello,

I noticed that some of the systemd user services are running for the user who hasn't logged in. How come?

The processes are:
```

/lib/systemd/systemd --user
(sd-pam)
/usr/bin/pipewire
/usr/bin/pipewire-media-session
/usr/bin/pipewire-pulse
/usr/libexec/tracker-miner-fs
/usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
/usr/libexec/gvfsd
/usr/libexec/gvfsd-fuse /run/user/1001/gvfs -f -o big_writes
/usr/libexec/gvfs-udisks2-volume-monitor
/usr/libexec/gvfs-mtp-volume-monitor
/usr/libexec/gvfs-afc-volume-monitor
/usr/libexec/gvfs-goa-volume-monitor
/usr/libexec/goa-daemon
/usr/libexec/goa-identity-service
/usr/libexec/gvfs-gphoto2-volume-monitor

```

---

### Post by 0x656b694d on 2021-04-18
This is called "lingering". To disable lingering, call `loginctl disable-linger username`.

---

### Post by grahammechanical on 2021-04-18
The developers have a choice. To quickly load the login screen and then cause the user to wait as all the services of an operating system are loaded into memory. And so giving an impression of a long boot time.

Or, start loading services prior to the login screen being loaded and continue as the user looks at the login screen. And so giving the impression of a fast boot time. Some of these services are useful even before we login. Video driver; keyboard layout; date and time; option to shutdown.; list of users installed; network manager. These are things that are not dependent upon which user is logged in as all users need them. SystemD, which is the program that starts and stops services has itself to be loaded.

People, please remember if you break it you get to keep the pieces.

Regards

---

### Post by 0x656b694d on 2021-04-18
Indeed, some of such services run at system level at start on boot, others are user specific (normally start after user login). In my case I suspect that pipewire doesn't work well (fail to acquire realtime permissions) when started in lingered mode.

---

