---
title: "No Splash &amp; /dev/sda2/clean boot after Nvidia Install"
date: 2017-07-09
forum: General Help
---

### Post by Ghost Hacks on 2017-07-09
Hello Ubuntu Forums,

I have a Dell XPS M1530 laptop running Ubuntu Mate 17.04 and after installing the nvidia driver the Ubuntu Mate splash screen does not show, and instead my i see the fsck /dev/sda2/clean message.  The boot process does not halt, it continues and shows some start-up process messages and then the nvidia splash screen and finally the Ubuntu Login screen.

I have tried searching for a fix as I would like to see a quick Ubuntu Splash screen instead of the linux boot processes.  I found three possible solutions, 1) is to stop the fsck during boot; but from what I found its normal to have the quick fsck conducted when using systemd, 2) purge-nvidia driver command; but I also have seen comments about this has made the situation worse, and 3) change the grub/plymouth screen resolutions to something supported.  Can anyone provide the latest information for fixing my issue?  I would like to have a quick startup with splash images.

Here are my full specs:

Dell XPS m1530
Intel Core2 Duo T5550 1.8Ghz
4GB DDR2 Ram
120GB 5400RPM HDD (12GB Swap, 100GB / partition)

Ubuntu Mate 17.04 x64 (Fresh Install)
Nvidia Driver 340.102
I also installed the latest TLP PPA and Intel Powertop PPA.

Let me know if you need any other information.

---

### Post by Ghost Hacks on 2017-07-09
In terms of boot speed, I ran the systemd-analyze blame command and below is the output, the big one is the dev-sda2.device and tlp.service.  I would like to keep the tlp.service as my laptop does not last very long on its older battery and I've noticed a huge improvement using powertop and tlp.  Is the dev-sda2.service that fsck that occurs during boot?  Would it be safe to disable it or change to occur only once every 30 days?

```
username@pc-name~$ systemd-analyze blame
         47.941s dev-sda2.device
         34.370s tlp.service
         10.602s accounts-daemon.service
         10.203s NetworkManager-wait-online.service
          7.632s grub-common.service
          7.589s apparmor.service
          6.853s loadcpufreq.service
          6.300s ModemManager.service
          5.933s postfix@-.service
          5.866s speech-dispatcher.service
          5.843s thermald.service
          5.808s gpu-manager.service
          4.998s NetworkManager.service
          2.758s irqbalance.service
          2.703s keyboard-setup.service
          2.427s avahi-daemon.service
          2.426s systemd-tmpfiles-setup.service
          2.413s polkit.service
          2.321s rsyslog.service
          2.251s systemd-modules-load.service
          2.130s systemd-tmpfiles-setup-dev.service
          2.023s networking.service
          2.019s plymouth-start.service
          1.591s apport.service
          1.549s upower.service
          1.328s cpufrequtils.service
          1.295s lm-sensors.service
          1.290s systemd-udevd.service
          1.204s lightdm.service
          1.158s plymouth-quit-wait.service
          1.047s wpa_supplicant.service
           948ms console-setup.service
           812ms resolvconf.service
           793ms systemd-timesyncd.service
           778ms systemd-resolved.service
           720ms dev-mqueue.mount
           720ms dev-hugepages.mount
           719ms sys-kernel-debug.mount
           639ms systemd-udev-trigger.service
           546ms kmod-static-nodes.service
           533ms ufw.service
           525ms systemd-user-sessions.service
           503ms openvpn.service
           480ms systemd-backlight@backlight:acpi_video0.service
           403ms systemd-update-utmp.service
           388ms systemd-journal-flush.service
           252ms setvtrgb.service
           251ms udisks2.service
           246ms systemd-tmpfiles-clean.service
           225ms systemd-journald.service
           219ms systemd-logind.service
           187ms systemd-sysctl.service
           142ms systemd-remount-fs.service
           134ms snapd.socket
           108ms dev-disk-by\x2duuid-2d6dad52\x2de72c\x2d49a3\x2da0bd\x2de5c9967
           107ms systemd-random-seed.service
           105ms user@1000.service
            83ms pppd-dns.service
            61ms hddtemp.service
            60ms alsa-restore.service
            60ms rtkit-daemon.service
            28ms snapd.autoimport.service
            23ms plymouth-read-write.service
            14ms ureadahead-stop.service
             7ms systemd-update-utmp-runlevel.service
             3ms sys-fs-fuse-connections.mount
```

---

