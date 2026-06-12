---
title: "UBUNTU 16.04 LTS takes to much time to boot !"
date: 2016-12-18
forum: General Help
---

### Post by thoreau0042 on 2016-12-18
HERE IS MY systemd-analyze blame RESULT 

```
         39.108s click-system-hooks.service
         17.976s lxd-containers.service
         14.549s NetworkManager-wait-online.service
         11.464s accounts-daemon.service
         11.074s grub-common.service
         10.911s preload.service
         10.323s schroot.service
          9.930s dev-sda2.device
          9.316s apport.service
          9.049s networking.service
          8.968s ModemManager.service
          8.700s ondemand.service
          8.679s irqbalance.service
          8.627s speech-dispatcher.service
          7.542s rsyslog.service
          7.538s gpu-manager.service
          7.525s systemd-user-sessions.service
          7.500s alsa-restore.service
          7.483s pppd-dns.service
          7.323s avahi-daemon.service
          7.256s bluetooth.service
          7.238s thermald.service
          6.593s apparmor.service
          5.766s NetworkManager.service
          4.311s lightdm.service
          2.849s keyboard-setup.service
          2.525s polkitd.service
          2.502s systemd-tmpfiles-setup-dev.service
          1.801s systemd-modules-load.service
          1.678s systemd-logind.service
          1.516s ofono.service
          1.484s ebtables.service
          1.307s console-setup.service
          1.281s rc-local.service
          1.181s binfmt-support.service
          1.077s systemd-fsck@dev-disk-by\x2duuid-EE9B\x2d39B9.service
          1.057s systemd-sysctl.service
          1.000s systemd-journald.service
           967ms user@1000.service
           958ms wpa_supplicant.service
           931ms udisks2.service
           925ms dev-loop0.device
           823ms systemd-rfkill.service
           674ms systemd-backlight@backlight:intel_backlight.service
           673ms systemd-udevd.service
           583ms dns-clean.service
           567ms systemd-timesyncd.service
           566ms plymouth-read-write.service
           564ms systemd-update-utmp.service
           462ms resolvconf.service
           454ms dev-hugepages.mount
           415ms systemd-random-seed.service
           413ms dev-loop1.device
           407ms upower.service
           384ms systemd-journal-flush.service
           375ms colord.service
           373ms openvpn.service
           318ms dev-mqueue.mount
           318ms ufw.service
           311ms systemd-tmpfiles-setup.service
           288ms dev-sda3.swap
           251ms kmod-static-nodes.service
           233ms snap-core-641.mount
           233ms snap-emoj-1.mount
           233ms tmp.mount
           217ms systemd-udev-trigger.service
           174ms setvtrgb.service
           174ms boot-efi.mount
           140ms sys-kernel-debug.mount
           114ms proc-sys-fs-binfmt_misc.mount
            84ms systemd-remount-fs.service
            78ms snapd.socket
            41ms plymouth-quit-wait.service
            19ms snapd.autoimport.service
             9ms systemd-update-utmp-runlevel.service
             8ms rtkit-daemon.service
             5ms lxd.socket
             2ms sys-fs-fuse-connections.mount
```

---

### Post by jeremy31 on 2016-12-18
*Thread moved to **General Help**.*

---

