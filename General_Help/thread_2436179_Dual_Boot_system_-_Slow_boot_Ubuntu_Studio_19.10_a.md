---
title: "Dual Boot system - Slow boot Ubuntu Studio 19.10 after installation"
date: 2020-02-01
forum: General Help
---

### Post by eby on 2020-02-01
We use this machine only for Audacity and checking live streaming.

Ubuntu Studio 19.10 Live USB(A1 rated MicroSD card with USB adapter) booted to desktop under 40seconds from Grub menu. After installing, it is taking approx 1.2mins to boot to desktop on Ubuntu, whilst Windows 10 does it in less than 25seconds from the Grub menu.

Ubuntu is up-to-date, not sure where the problem lies. The reason i've installed MATE is, the installed GUI (Xfce) was completely different and ugly from what is used on Live image, and it took longer to boot to desktop.

Any help is appreciated to reduce boot time and permanently remove Windows from this machine.

thanks,

```

~$ inxi -F
System:    Host: Audio-Station Kernel: 5.3.0-26-lowlatency x86_64 bits: 64 Desktop: MATE 1.22.2 
           Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop System: Hewlett-Packard product: h9-1186in v: 1.00 serial: <root required> 
           Mobo: PEGATRON model: 2AD5 v: 1.03 serial: <root required> UEFI: AMI v: 7.14 date: 05/22/2012 
CPU:       Topology: Quad Core model: Intel Core i7-3770 bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 3898 MHz min/max: 1600/3900 MHz Core speeds (MHz): 1: 3884 2: 3890 3: 2190 4: 2459 5: 3889 6: 1709 7: 3828 
           8: 3831 
Graphics:  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: modesetting unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel Ivybridge Desktop v: 4.2 Mesa 19.2.1 
Audio:     Device-1: Intel 7 Series/C216 Family High Definition Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.3.0-26-lowlatency 
Network:   Device-1: Broadcom and subsidiaries BCM43228 802.11a/b/g/n driver: bcma-pci-bridge 
           Device-2: Qualcomm Atheros AR8161 Gigabit Ethernet driver: alx 
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: 4c:72:b9:02:d1:3a 
Drives:    Local Storage: total: 1.82 TiB used: 12.83 GiB (0.7%) 
           ID-1: /dev/sda vendor: Seagate model: ST2000DM005-2CW102 size: 1.82 TiB 
Partition: ID-1: / size: 117.15 GiB used: 12.80 GiB (10.9%) fs: ext4 dev: /dev/sda6 
Sensors:   System Temperatures: cpu: 43.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 240 Uptime: 14m Memory: 15.53 GiB used: 1010.6 MiB (6.4%) Shell: bash inxi: 3.0.36 

```


```
~$ systemd-analyze blame
         27.178s man-db.service
         17.699s networkd-dispatcher.service
         16.195s udisks2.service
         15.761s snapd.service
         13.289s logrotate.service
         11.813s accounts-daemon.service
          9.643s ModemManager.service
          9.151s lightdm.service
          9.149s plymouth-quit-wait.service
          8.730s NetworkManager.service
          7.109s dev-sda6.device
          6.442s systemd-resolved.service
          6.371s grub-initrd-fallback.service
          6.350s avahi-daemon.service
          6.219s thermald.service
          6.218s rsyslog.service
          6.213s secureboot-db.service
          6.211s grub-common.service
          6.210s e2scrub_reap.service
          5.940s wpa_supplicant.service
          5.939s apport.service
          5.931s gpu-manager.service
          5.931s systemd-logind.service
          5.741s upower.service
          4.734s bluetooth.service
          4.728s rtirq.service
          3.419s NetworkManager-wait-online.service
          2.907s apt-daily-upgrade.service
          2.471s networking.service
          2.040s systemd-journal-flush.service
          1.706s systemd-udevd.service
          1.525s polkit.service
          1.207s pppd-dns.service
          1.204s lm-sensors.service
           720ms systemd-modules-load.service
           701ms keyboard-setup.service
           656ms systemd-fsck@dev-disk-by\x2duuid-AACF\x2d50FD.service
           652ms apparmor.service
           652ms colord.service
           560ms systemd-journald.service
           536ms systemd-sysctl.service
           475ms systemd-sysusers.service
           453ms kerneloops.service
           416ms user@1000.service
           403ms snapd.seeded.service
           391ms systemd-tmpfiles-setup-dev.service
           379ms swapfile.swap
           376ms systemd-tmpfiles-setup.service
           362ms systemd-udev-trigger.service
           339ms openvpn.service
           224ms systemd-timesyncd.service
           211ms systemd-rfkill.service
           198ms systemd-remount-fs.service
           184ms systemd-user-sessions.service
           176ms hddtemp.service
           134ms systemd-update-utmp.service
           106ms sys-kernel-debug.mount
           106ms dev-hugepages.mount
            96ms dev-mqueue.mount
            83ms plymouth-read-write.service
            76ms ifupdown-pre.service
            67ms boot-efi.mount
            47ms systemd-random-seed.service
            44ms kmod-static-nodes.service
            34ms console-setup.service
            28ms ufw.service
            25ms user-runtime-dir@1000.service
            25ms setvtrgb.service
            24ms rtkit-daemon.service
            13ms plymouth-start.service
             6ms systemd-update-utmp-runlevel.service
             3ms sys-fs-fuse-connections.mount
             2ms snapd.socket
             2ms sys-kernel-config.mount

```


```

~$ sudo systemd-analyze time
Startup finished in 3.964s (kernel) + 40.075s (userspace) = 44.040s 
graphical.target reached after 31.178s in userspace

```

---

