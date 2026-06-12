---
title: "Slow boot time"
date: 2018-06-21
forum: General Help
---

### Post by bizhat on 2018-06-21
I am running Ubuntu 18.04. My PC take lot of time to boot

```
boby@ok-pc-01:~$ systemd-analyze 
Startup finished in 4.909s (kernel) + 3min 488ms (userspace) = 3min 5.397s
graphical.target reached after 1min 44.646s in userspace
boby@ok-pc-01:~$ 

```

3min 5.397s to complete the boot. 

I have SSD for boot drive. My friend with normal HDD have following boot time

> Startup finished in 4.672s (firmware) + 3.989s (loader) + 3.052s (kernel) + 23.660s (userspace) = 35.375s


Here is list of applications that take more time as per systemd-analyze blame.

```

boby@ok-pc-01:~$ systemd-analyze blame
          7.904s mysql.service
          6.141s NetworkManager-wait-online.service
          5.847s apt-daily-upgrade.service
          2.984s systemd-udev-settle.service
          1.990s dev-sdd1.device
          1.896s zfs-import-cache.service
          1.423s plymouth-quit-wait.service
          1.180s dev-loop2.device
          1.179s dev-loop1.device
          1.172s dev-loop3.device
          1.166s lm-sensors.service
          1.159s dev-loop4.device
          1.143s dev-loop5.device
          1.139s dev-loop7.device
          1.137s dev-loop6.device
          1.134s dev-loop8.device
          1.132s dev-loop9.device
          1.099s dev-loop10.device
          1.085s dev-loop11.device
          1.067s dev-loop12.device
           860ms fwupd.service
           841ms udisks2.service
           780ms snapd.service
           743ms lvm2-pvscan@8:16.service
           316ms systemd-logind.service
           302ms phpsessionclean.service
           299ms NetworkManager.service
           258ms upower.service
           247ms dev-loop0.device
           230ms networkd-dispatcher.service
           184ms systemd-resolved.service
           184ms systemd-timesyncd.service
           161ms snap-gnome\x2dcharacters-69.mount
           158ms snap-gnome\x2dsystem\x2dmonitor-45.mount
           144ms snap-gnome\x2dcalculator-178.mount
           133ms systemd-udev-trigger.service
           127ms systemd-journald.service
           126ms bolt.service
           123ms snap-gnome\x2dlogs-25.mount
           122ms ModemManager.service
           118ms snap-gnome\x2dsystem\x2dmonitor-36.mount
           118ms apache2.service
           115ms systemd-journal-flush.service
           114ms snap-core-4830.mount
           111ms keyboard-setup.service
           109ms zfs-mount.service
           106ms snap-core-4486.mount
            99ms snap-gnome\x2dlogs-37.mount
            92ms accounts-daemon.service
            89ms systemd-udevd.service
            86ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
            81ms apparmor.service
            79ms lvm2-monitor.service
            79ms snap-core-4650.mount
            77ms grub-common.service
boby@ok-pc-01:~$ 

```


Any idea why my PC take so much time to boot ? It can be one of the application or it stuck waiting for something to come up.

---

### Post by bizhat on 2018-06-22
I got the problem fixed. It was due to /etc/fstab having an entry for non existant disk.

[https://www.serverok.in/ubuntu-slow-boot](https://www.serverok.in/ubuntu-slow-boot)

---

### Post by Bashing-om on 2018-06-22
bizhat; :)

Good sleuthing on your part .
Great that you provided the resolution.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

