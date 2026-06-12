---
title: "Systemd journal flush service takes a lot of my boot time"
date: 2018-06-15
forum: General Help
---

### Post by flaviomonteiro2013 on 2018-06-15
Any ideas how to solve it?

Also, if anyone knows how to make dev-sda7.device, dev-loop0.device, dev-loop1.device and systemd-udevd.service disappear or be much shorter that'd be appreciated.

I suspect the dev-loopX devices are snapcraft's fault, since I have exactly two snap packages installed (core & discord) and IIRC snap used to mount each package on a loopback device.

Output of systemd-analyze blame
```

         41.275s systemd-journal-flush.service
         36.162s dev-sda7.device
         29.003s dev-loop0.device
         28.725s dev-loop1.device
         27.029s systemd-udevd.service
          7.101s NetworkManager-wait-online.service
          6.538s udisks2.service
          6.041s accounts-daemon.service
          5.686s grub-common.service
          5.495s loadcpufreq.service
          4.757s NetworkManager.service
          4.573s networkd-dispatcher.service
          4.267s snapd.service
          4.092s ModemManager.service
          3.564s thermald.service
          3.378s speech-dispatcher.service
          3.302s systemd-fsck@dev-disk-by\x2duuid-E878\x2d8D80.service
          3.143s systemd-resolved.service
          2.937s wpa_supplicant.service
          2.386s keyboard-setup.service
          2.379s apport.service
          2.348s avahi-daemon.service
          2.347s bluetooth.service
          2.345s systemd-logind.service
          2.340s lm-sensors.service
          2.327s gpu-manager.service
          2.324s pppd-dns.service
          2.322s rsyslog.service
          2.296s alsa-restore.service
          2.293s plymouth-start.service
          2.200s snap-core-4650.mount
          2.020s systemd-random-seed.service
          1.851s polkit.service
          1.563s snap-discord-66.mount
          1.490s systemd-tmpfiles-setup-dev.service
          1.211s systemd-remount-fs.service
          1.201s dev-hugepages.mount
          1.126s sys-kernel-debug.mount
          1.096s systemd-modules-load.service
          1.095s dev-mqueue.mount
          1.005s systemd-timesyncd.service
           987ms upower.service
           886ms apparmor.service
           643ms systemd-sysctl.service
           638ms cpufrequtils.service
           547ms kmod-static-nodes.service
           524ms swapfile.swap
           472ms systemd-journald.service
           452ms boot-efi.mount
           445ms systemd-backlight@backlight:intel_backlight.service
           407ms systemd-tmpfiles-setup.service
           295ms ufw.service
           214ms lightdm.service
           213ms plymouth-quit-wait.service
           138ms virtualbox.service
           126ms setvtrgb.service
           117ms systemd-udev-trigger.service
           115ms user@1000.service
            64ms snapd.seeded.service
            61ms plymouth-read-write.service
            13ms hddtemp.service
            12ms kerneloops.service
             9ms systemd-user-sessions.service
             9ms ureadahead-stop.service
             5ms systemd-update-utmp-runlevel.service
             3ms systemd-update-utmp.service
             2ms rtkit-daemon.service
             2ms systemd-backlight@leds:dell::kbd_backlight.service
             2ms systemd-rfkill.service
             2ms console-setup.service
             1ms sys-kernel-config.mount
             1ms sys-fs-fuse-connections.mount
           455us snapd.socket

```

I'm on Xubuntu 18.04

---

### Post by flaviomonteiro2013 on 2018-06-15
I did systemctl mask systemd-journal-flush.service and apt-get purge snapd, now my top entries in systemd-analyze blame are this:

I will have to rerun it manually from time to time to clean my journal, but that's okay. As of snapd, I don't really use it for anything.

```

         25.990s dev-sda7.device
         12.522s systemd-udevd.service
         10.039s systemd-tmpfiles-setup-dev.service
          8.352s keyboard-setup.service
          6.840s NetworkManager-wait-online.service

```

dev-sda7.device (my root partition) still takes an insane amount of time, but this is way better.

---

