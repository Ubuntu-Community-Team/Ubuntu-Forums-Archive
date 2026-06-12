---
title: "Ubuntu 16.04 hangs"
date: 2016-09-16
forum: General Help
---

### Post by ganesh3 on 2016-09-16
Hi,

I am facing an issue with the performance of Ubuntu wherein Ubuntu Desktop hangs and the only way to work with it is to again restart the machine. I have also installed elementary desktop (Pantheon) in which I dont face this issue.

I have a Lenovo Ideapad 100 14 with Intel i3 with Integrated Graphics (00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)) and graphics driver I have installed is of Intel.

I have also set the following in the GRUB which does not make a huge difference to the performance[INDENT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
```
[/INDENT]

Can someone please help? Please let me know if you need any further details.

Also, the startup takes some time and I am sharing the output of the services that are started and take whatever time they need. Can someone please also help in improving this issue?

Additional details on the SWAP 

```
$ sudo swapon --show[INDENT]NAME      TYPE      SIZE USED PRIO
/dev/sda3 partition 3.9G   0B   -1
[/INDENT]

```
```
$ free -h[INDENT]              total        used        free      shared  buff/cache   available
Mem:           3.8G        1.1G        1.7G        245M        1.0G        2.2G
Swap:          3.9G          0B        3.9G
[/INDENT]

```
```
$systemd-analyze blame

          8.124s NetworkManager-wait-online.service
          6.523s ModemManager.service
          5.585s dev-sda2.device
          4.453s grub-common.service
          3.803s apport.service
          3.738s networking.service
          3.711s systemd-logind.service
          3.705s irqbalance.service
          3.149s thermald.service
          3.128s speech-dispatcher.service
          3.064s alsa-restore.service
          3.053s lm-sensors.service
          2.846s NetworkManager.service
          2.631s avahi-daemon.service
          2.444s accounts-daemon.service
          2.329s gpu-manager.service
          2.123s apparmor.service
          1.920s snapd.firstboot.service
          1.847s console-setup.service
          1.763s polkitd.service
          1.547s systemd-rfkill.service
          1.350s rsyslog.service
          1.335s lightdm.service
          1.258s lvm2.service
          1.050s bluetooth.service
           930ms systemd-journald.service
           886ms systemd-modules-load.service
           867ms keyboard-setup.service
           798ms upower.service
           775ms systemd-user-sessions.service
           725ms systemd-tmpfiles-setup-dev.service
           713ms systemd-udevd.service
           654ms pppd-dns.service
           654ms ondemand.service
           651ms iio-sensor-proxy.service
           648ms colord.service
           572ms kmod-static-nodes.service
           563ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-7E6D\x2d75EF.servic"]systemd-fsck@dev-disk-by\x2duuid-7E6D\x2d75EF.servic[/EMAIL]e
           487ms dev-sda3.swap
           476ms udisks2.service
           433ms dns-clean.service
           388ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           388ms systemd-tmpfiles-setup.service
           364ms snapd.refresh.service
           353ms dev-mqueue.mount
           351ms dev-hugepages.mount
           339ms openvpn.service
           301ms ufw.service
           238ms systemd-localed.service
           206ms wpa_supplicant.service
           204ms systemd-journal-flush.service
           194ms systemd-update-utmp.service
           189ms systemd-udev-trigger.service
           184ms systemd-random-seed.service
           178ms systemd-remount-fs.service
           160ms resolvconf.service
           145ms systemd-sysctl.service
           111ms systemd-hostnamed.service
           106ms systemd-timesyncd.service
            94ms setvtrgb.service
            75ms rc-local.service
            68ms plymouth-read-write.service
            67ms hddtemp.service
            54ms rtkit-daemon.service
            53ms sys-kernel-debug.mount
            51ms snapd.socket
            44ms boot-efi.mount
            35ms systemd-tmpfiles-clean.service
            32ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            15ms systemd-update-utmp-runlevel.service
             7ms snapd.boot-ok.service
             5ms ureadahead-stop.service
             2ms sys-fs-fuse-connections.mount
             2ms plymouth-quit-wait.service
lines 28-74/74 (END)

```

Thanks

Ganesh Bhat

---

### Post by ganesh3 on 2016-10-02
Can anyone please help?

---

