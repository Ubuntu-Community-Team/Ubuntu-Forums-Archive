---
title: "Slow boot time."
date: 2017-10-20
forum: General Help
---

### Post by surender7790 on 2017-10-20
Boot Time is very slow. How to increase it? It takes more than 1 minute to boot. Please Help!!
```
[FONT=monospace]
         16.783s NetworkManager-wait-online.service
         13.750s mysql.service
         11.256s dev-sda9.device
          9.574s libvirtd.service
          7.209s docker.service
          5.746s NetworkManager.service
          5.365s chrome-remote-desktop.service
          5.089s accounts-daemon.service
          4.123s setvtrgb.service
          4.073s lvm2-monitor.service
          3.952s ModemManager.service
          3.648s snapd.service
          3.615s apache2.service
          3.402s teamviewerd.service
          3.231s networking.service
          3.227s apport.service
          2.636s thermald.service
          2.608s apparmor.service
          2.606s keyboard-setup.service
          2.476s systemd-fsck@dev-disk-by\x2duuid-EE7D\x2d3E49.service
          2.327s systemd-timesyncd.service
          2.228s gpu-manager.service
          1.982s lm-sensors.service
          1.916s grub-common.service
          1.910s irqbalance.service
          1.688s mnt-Volume_E.mount
          1.624s systemd-rfkill.service
          1.614s mnt-Volume_F.mount
          1.612s polkit.service
          1.545s mnt-Volume_D.mount
          1.494s systemd-udevd.service
          1.438s rsyslog.service
          1.436s systemd-tmpfiles-setup-dev.service
          1.407s systemd-modules-load.service
          1.194s avahi-daemon.service
           886ms user@1000.service
           829ms upower.service
           706ms docker.socket
           672ms boot-efi.mount
           616ms systemd-user-sessions.service
           603ms resolvconf.service
           550ms dev-sda2.swap
           533ms systemd-tmpfiles-setup.service
           511ms udisks2.service
[COLOR=#ffffff]lines 1-44[/COLOR]

[/FONT]
```

---

### Post by mastablasta on 2017-10-20
leave it on all the time.

if laptop, then remove services you do not need up and running at boot (Apache web server for example).

---

