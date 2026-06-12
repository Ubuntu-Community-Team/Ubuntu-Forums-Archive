---
title: "Please help me diagnose my slow boot issue - 17.04"
date: 2017-05-27
forum: General Help
---

### Post by wokeaf on 2017-05-27
Hi guys, please help if you can. 

From dmesg, these are the problem areas:

[    7.247452] lp: driver loaded but no devices found
[COLOR=#ff0000][    7.467627] ppdev: user-space parallel port driver
[   20.904343] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro[/COLOR]
[   20.920099] systemd-journald[238]: Received request to flush runtime journal from PID 1

and

[   31.986166] R8188EU: ERROR assoc success 
[COLOR=#ff0000][   31.986208] IPv6: ADDRCONF(NETDEV_CHANGE): wlxc4e98406eea0: link becomes ready
[   50.063076] kauditd_printk_skb: 75 callbacks suppressed[/COLOR]
[   50.063078] audit: type=1400 audit(1495866277.547:37): apparmor="DENIED" operation="sendmsg" profile="/usr/lib/telepathy/telepathy-*" name="/run/systemd/journal/socket" pid=1915 comm="telepathy-haze" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0

And here is the entire output file: [http://paste.ubuntu.com/24675663/](http://paste.ubuntu.com/24675663/)

Please let me know if additional information is required.

Thanks!

---

### Post by kc1di on 2017-05-27
Try running this command and it will tell you exactly where the longest load times are

```
systemd-analyze blame 
```

---

### Post by wokeaf on 2017-05-27
> **kc1di said:**
> Try running this command and it will tell you exactly where the longest load times are

```
systemd-analyze blame 
```

Thanks for responding kc1di.

The three slowest processes are:

16.717s dev-sda7.device
14.892s keyboard-setup.service
14.521s systemd-tmpfiles-setup-dev.service

Can anything be done to reduce the load times? 
Let me know if you're interested in seeing the entire output or any other information.

Thanks!

---

### Post by kc1di on 2017-05-27
it would be better to post the whole output

---

### Post by wokeaf on 2017-05-29
> **kc1di said:**
> it would be better to post the whole output

Here you are:

 17.180s dev-sda7.device
         14.769s keyboard-setup.service
         14.313s systemd-tmpfiles-setup-dev.service
         13.744s systemd-sysctl.service
          3.636s click-system-hooks.service
          2.652s grub-common.service
          2.554s accounts-daemon.service
          2.538s avahi-daemon.service
          2.373s fwupd.service
          1.275s ModemManager.service
          1.012s udisks2.service
           878ms NetworkManager.service
           840ms thermald.service
           807ms networking.service
           807ms systemd-modules-load.service
           670ms [email]user@1000.servic[/email]e
           666ms upower.service
           583ms repowerd.service
           576ms [email]systemd-fsck@dev-disk-by\x2duuid-b07ecba7\x2d8a96\x2d4b38\x2db197\x2d19b6e2e15787.servic[/email]e
           560ms colord.service
           552ms irqbalance.service
           397ms home.mount
           365ms dev-mqueue.mount
           365ms dev-hugepages.mount
           363ms rtkit-daemon.service
           362ms sys-kernel-debug.mount
           326ms gpu-manager.service
           317ms rsyslog.service
           314ms apparmor.service
           301ms systemd-journald.service
           253ms systemd-resolved.service
           249ms ufw.service
           241ms dev-disk-by\x2duuid-14f2f4db\x2dbae4\x2d4e4f\x2daf42\x2d93a789ac3ad9.swap
           237ms kmod-static-nodes.service
           210ms wpa_supplicant.service
           158ms lightdm.service
           156ms systemd-tmpfiles-setup.service
           154ms plymouth-quit-wait.service
           115ms systemd-udev-trigger.service
           111ms setvtrgb.service
           103ms systemd-timesyncd.service
           102ms systemd-logind.service
            96ms speech-dispatcher.service
            70ms pppd-dns.service
            69ms apport.service
            69ms polkit.service
            56ms alsa-restore.service
            53ms systemd-update-utmp.service
            49ms plymouth-read-write.service
            46ms systemd-udevd.service
            44ms binfmt-support.service
            42ms systemd-journal-flush.service
            37ms ureadahead-stop.service
            33ms systemd-remount-fs.service
            32ms rc-local.service
            31ms plymouth-start.service
            31ms systemd-user-sessions.service
            30ms openvpn.service
            22ms snapd.autoimport.service
            13ms dns-clean.service
            11ms systemd-random-seed.service
             8ms console-setup.service
             7ms systemd-update-utmp-runlevel.service
             5ms proc-sys-fs-binfmt_misc.mount
             4ms resolvconf.service
             2ms sys-fs-fuse-connections.mount
             1ms snapd.socket

---

