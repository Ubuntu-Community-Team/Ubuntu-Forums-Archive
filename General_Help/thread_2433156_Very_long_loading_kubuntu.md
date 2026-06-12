---
title: "Very long loading kubuntu"
date: 2019-12-14
forum: General Help
---

### Post by sc3ry on 2019-12-14
Have Windows and Kubuntu 19.10 on NVMe. Windows boots very fast, but linux takes long time to load.

```
[FONT=monospace][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ systemd-analyze time[/COLOR]
Startup finished in 1.903s (kernel) + 1min 30.895s (userspace) = 1min 32.798s  
graphical.target reached after 1min 30.890s in userspace[/FONT]
```
```
[FONT=monospace][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ systemd-analyze blame[/COLOR]
           442ms systemd-logind.service
           381ms dev-nvme0n1p5.device
           259ms upower.service
           240ms systemd-journald.service
           165ms mpd.service
           145ms systemd-resolved.service
           144ms systemd-timesyncd.service
           136ms snapd.service
           102ms networkd-dispatcher.service
            80ms udisks2.service
            73ms swapfile.swap
            59ms ModemManager.service
            53ms user@1000.service
            45ms systemd-udev-trigger.service
            43ms accounts-daemon.service
            39ms NetworkManager.service
            31ms gpu-manager.service
            30ms keyboard-setup.service
            29ms plymouth-quit.service
            28ms grub-common.service
            27ms systemd-udevd.service
            26ms pppd-dns.service
            26ms wpa_supplicant.service
            22ms apparmor.service
            22ms packagekit.service
            19ms nvidia-persistenced.service
            17ms thermald.service
            13ms plymouth-read-write.service
            13ms plymouth-read-write.service
            13ms grub-initrd-fallback.service
            12ms plymouth-start.service
            12ms kerneloops.service
            10ms systemd-tmpfiles-setup.service
            10ms binfmt-support.service
             9ms systemd-modules-load.service
             9ms polkit.service
             8ms user-runtime-dir@1000.service
             8ms snapd.seeded.service
             6ms systemd-remount-fs.service
             5ms systemd-update-utmp.service
             5ms dev-mqueue.mount
             5ms systemd-sysusers.service
             5ms dev-hugepages.mount
             5ms systemd-sysctl.service
             4ms kmod-static-nodes.service
             4ms avahi-daemon.service
             4ms ufw.service
             4ms systemd-tmpfiles-setup-dev.service
             4ms systemd-user-sessions.service
             4ms proc-sys-fs-binfmt_misc.mount
             3ms sys-kernel-debug.mount
             3ms rtkit-daemon.service
             3ms systemd-update-utmp-runlevel.service
             3ms console-setup.service
             2ms systemd-random-seed.service
             2ms sddm.service
             2ms setvtrgb.service
             1ms sys-fs-fuse-connections.mount
             1ms sys-kernel-config.mount
             1ms snapd.socket
[/FONT]
```

```
[FONT=monospace][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ systemd-analyze critical-chain[/COLOR]
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 30.890s
&#9492;&#9472;[COLOR=#FF5454]**sddm.service @1min 30.887s +2ms**[/COLOR]
  &#9492;&#9472;[COLOR=#FF5454]**systemd-logind.service @1min 30.443s +442ms**[/COLOR]
    &#9492;&#9472;basic.target @1min 30.421s
      &#9492;&#9472;sockets.target @1min 30.421s
        &#9492;&#9472;[COLOR=#FF5454]**snapd.socket @1min 30.420s +1ms**[/COLOR]
          &#9492;&#9472;sysinit.target @1min 30.418s
            &#9492;&#9472;[COLOR=#FF5454]**systemd-timesyncd.service @1min 30.273s +144ms**[/COLOR]
              &#9492;&#9472;[COLOR=#FF5454]**systemd-tmpfiles-setup.service @1min 30.259s +10ms**[/COLOR]
                &#9492;&#9472;[COLOR=#FF5454]**systemd-journald.service @93ms +240ms**[/COLOR]
                  &#9492;&#9472;systemd-journald-dev-log.socket @92ms
                    &#9492;&#9472;system.slice @87ms
                      &#9492;&#9472;-.slice @87ms[/FONT]
```

So I need help.

---

### Post by mörgæs on 2019-12-15
Hi, welcome to the fora.

Remember that Windows does not actually boot under standard operation. It wakes up from hibernation which gives a much shorter 'boot' time.

Have you considered to remove Snap and install the classic package versions in stead?

---

### Post by sc3ry on 2019-12-15
Yes, I already have tried it. I fixed this problem by reinstalling Kubuntu.

Thanks.

---

