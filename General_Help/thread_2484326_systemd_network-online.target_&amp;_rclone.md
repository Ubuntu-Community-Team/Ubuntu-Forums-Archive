---
title: "systemd network-online.target &amp; rclone"
date: 2023-02-23
forum: General Help
---

### Post by zkab on 2023-02-23
I tested r*clone mount *by creating a systemd service.
It worked OK but after reboot I got tons of network dependencies.
My systemd unit looks like this:
```
# /etc/systemd/system/pcloud.mount

[Unit]
Description=Mount rclone
After=network-online.target

[Mount]
Type=rclone
What=pcloud:
Where=/pcloud
Options=rw,allow_other,args2env,vfs-cache-mode=writes,config=/root/.config/rclone/rclone.conf,cache-dir=/var/rclone

[Install]
WantedBy=multi-user.target
```
After reboot:
```
journalctl -b -0 | grep network
feb 23 13:51:33 beelink kernel: drop_monitor: Initializing network drop monitor service
feb 23 13:51:33 beelink systemd[1]: network.target: Found ordering cycle on systemd-resolved.service/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on systemd-tmpfiles-setup.service/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on local-fs.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on pcloud.mount/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Job systemd-resolved.service/start deleted to break ordering cycle starting with network.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found ordering cycle on NetworkManager.service/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on dbus.service/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on sysinit.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on systemd-update-utmp.service/verify-active
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on systemd-tmpfiles-setup.service/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on local-fs.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on pcloud.mount/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: network.target: Job NetworkManager.service/start deleted to break ordering cycle starting with network.target/start
feb 23 13:51:33 beelink systemd[1]: wpa_supplicant.service: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: wpa_supplicant.service: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: paths.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: paths.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network-online.target/start
feb 23 13:51:33 beelink systemd[1]: basic.target: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found ordering cycle on systemd-resolved.service/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on systemd-tmpfiles-setup.service/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on local-fs.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on pcloud.mount/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Job systemd-resolved.service/start deleted to break ordering cycle starting with network.target/start
feb 23 13:51:34 beelink systemd[1]: systemd-update-utmp.service: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: systemd-update-utmp.service: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found ordering cycle on systemd-resolved.service/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on systemd-tmpfiles-setup.service/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on local-fs.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on pcloud.mount/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: network.target: Job systemd-resolved.service/start deleted to break ordering cycle starting with network.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network-online.target/start
feb 23 13:51:34 beelink systemd[1]: sysinit.target: Found dependency on network.target/start
feb 23 13:51:35 beelink systemd[1]: systemd-tmpfiles-setup.service: Found dependency on network-online.target/start
feb 23 13:51:35 beelink systemd[1]: systemd-tmpfiles-setup.service: Found dependency on network.target/start
feb 23 13:51:36 beelink systemd[1]: Dispatcher daemon for systemd-networkd was skipped because all trigger condition checks failed.
feb 23 13:51:36 beelink NetworkManager[771]: <info>  [1677156696.5016] monitoring ifupdown state file '/run/network/ifstate'.
feb 23 13:51:36 beelink NetworkManager[771]: <info>  [1677156696.7713] ifupdown: interfaces file /etc/network/interfaces doesn't exist
feb 23 13:51:37 beelink systemd[933]: Listening on GnuPG network certificate management daemon.
feb 23 13:51:37 beelink NetworkManager[771]: <info>  [1677156697.3801] failed to open /run/network/ifstate
feb 23 13:51:55 beelink systemd[1535]: Listening on GnuPG network certificate management daemon.
feb 23 13:52:12 beelink systemd[933]: Closed GnuPG network certificate management daemon.

```

Don't have much experience of systemd.
How can this be fixed?

---

