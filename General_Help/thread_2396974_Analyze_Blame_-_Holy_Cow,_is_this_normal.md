---
title: "Analyze Blame - Holy Cow, is this normal?"
date: 2018-07-23
forum: General Help
---

### Post by galacticstone on 2018-07-23
I ran system-md analyze blame to try to figure out what's going on with my seemingly-random slow-boot issue. Sometimes things will boot or reboot normally. Other times, for no apparent reason, the boot or reboot process hangs on a black screen and takes forever to load. If I move the mouse around and click the touchpad several times, this increases the entropy and seems to snap it out of the funk quicker and it will resume booting quicker.

Anyways....I tried analyze blame and got this surprisingly-long result. Is this normal? Why are all of these processes taking so long?

My PC didn't do this right after I freshly installed or after the first few updates. This started recently, in the last few weeks.

```
23.022s systemd-journal-flush.service
         21.327s dev-sda1.device
         15.294s apparmor.service
         15.090s systemd-udevd.service
         14.094s console-setup.service
         14.058s dns-clean.service
         13.473s snap-vlc-365.mount
         13.401s snap-gnome\x2d3\x2d26\x2d1604-59.mount
         13.311s snap-vlc-190.mount
         13.307s snap-gnome\x2dcharacters-101.mount
         13.098s snap-gnome\x2dcharacters-96.mount
         13.078s snap-gnome\x2dlogs-37.mount
         13.049s snap-core-4830.mount
         13.044s snap-gnome\x2d3\x2d26\x2d1604-70.mount
         13.042s snap-gtk\x2dcommon\x2dthemes-319.mount
         12.979s snap-gnome\x2d3\x2d26\x2d1604-64.mount
         12.956s snap-gnome\x2dcharacters-103.mount
         12.912s snap-gnome\x2dlogs-31.mount
         12.897s snap-core-4650.mount
         12.881s snap-gnome\x2dlogs-34.mount
         12.849s snap-core-4917.mount
         10.254s plymouth-quit-wait.service
          5.858s apt-daily-upgrade.service
          5.087s bolt.service
lines 1-24...skipping...
         23.022s systemd-journal-flush.service
         21.327s dev-sda1.device
         15.294s apparmor.service
         15.090s systemd-udevd.service
         14.094s console-setup.service
         14.058s dns-clean.service
         13.473s snap-vlc-365.mount
         13.401s snap-gnome\x2d3\x2d26\x2d1604-59.mount
         13.311s snap-vlc-190.mount
         13.307s snap-gnome\x2dcharacters-101.mount
         13.098s snap-gnome\x2dcharacters-96.mount
         13.078s snap-gnome\x2dlogs-37.mount
         13.049s snap-core-4830.mount
         13.044s snap-gnome\x2d3\x2d26\x2d1604-70.mount
         13.042s snap-gtk\x2dcommon\x2dthemes-319.mount
         12.979s snap-gnome\x2d3\x2d26\x2d1604-64.mount
         12.956s snap-gnome\x2dcharacters-103.mount
         12.912s snap-gnome\x2dlogs-31.mount
         12.897s snap-core-4650.mount
         12.881s snap-gnome\x2dlogs-34.mount
         12.849s snap-core-4917.mount
         10.254s plymouth-quit-wait.service
          5.858s apt-daily-upgrade.service
          5.087s bolt.service
          4.658s dev-loop9.device
          4.648s dev-loop11.device
          4.618s dev-loop13.device
          4.602s dev-loop14.device
          4.575s dev-loop0.device
          4.558s dev-loop1.device
          4.485s dev-loop3.device
          4.477s dev-loop5.device
          4.473s dev-loop12.device
          4.469s dev-loop2.device
          4.442s dev-loop4.device
          4.415s snapd.service
          4.234s dev-loop6.device
          4.205s dev-loop7.device
          4.123s dev-loop8.device
          4.055s dev-loop10.device
          3.169s systemd-rfkill.service
          2.764s udisks2.service
          2.371s grub-common.service
          2.228s NetworkManager.service
          2.152s accounts-daemon.service
          2.137s preload.service
          2.074s networkd-dispatcher.service
          1.922s ModemManager.service
          1.599s keyboard-setup.service
          1.294s plymouth-start.service
          1.171s systemd-tmpfiles-setup-dev.service
          1.099s fwupd.service
           987ms ufw.service
           948ms systemd-modules-load.service
           947ms thermald.service
           947ms kmod-static-nodes.service
           876ms polkit.service
           867ms systemd-sysctl.service
           860ms swapfile.swap
           768ms colord.service
           679ms apt-daily.service
           570ms systemd-journald.service
           526ms systemd-random-seed.service
           506ms gdm.service
           430ms apport.service
           413ms [email]user@120.servic[/email]e
           397ms speech-dispatcher.service
           391ms iio-sensor-proxy.service
           383ms sys-kernel-debug.mount
           382ms dev-mqueue.mount
           373ms alsa-restore.service
           367ms systemd-remount-fs.service
           348ms systemd-logind.service
           332ms dev-hugepages.mount
           327ms networking.service
           281ms systemd-update-utmp.service
           261ms avahi-daemon.service
           245ms systemd-resolved.service
           244ms systemd-timesyncd.service
           233ms rsyslog.service
           170ms wpa_supplicant.service
           146ms kerneloops.service
           138ms pppd-dns.service
           114ms systemd-tmpfiles-setup.service
           104ms snapd.socket
           101ms gpu-manager.service
            98ms systemd-udev-trigger.service
            88ms systemd-tmpfiles-clean.service
            87ms packagekit.service
            75ms [email]user@1000.servic[/email]e
            75ms upower.service
            63ms setvtrgb.service
            34ms bluetooth.service
            20ms lm-sensors.service
            18ms snapd.seeded.service
            11ms plymouth-read-write.service
            10ms systemd-update-utmp-runlevel.service
             7ms ureadahead-stop.service
             5ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
             3ms rtkit-daemon.service
             3ms systemd-user-sessions.service
             3ms sys-kernel-config.mount
             2ms sys-fs-fuse-connections.mount
```

---

### Post by &amp;KyT$0P# on 2018-07-23
Please post the output of running this command in Terminal -
```
uname -r
```

---

