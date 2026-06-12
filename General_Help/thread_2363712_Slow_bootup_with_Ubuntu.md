---
title: "Slow bootup with Ubuntu"
date: 2017-06-13
forum: General Help
---

### Post by 0marthamydear on 2017-06-13
I am using Ubuntu 16.04.2 LTS and its kernel is Linux 4.4.78-generic (i686) in the LXDE Lubuntu desktop environment. I have no idea what I just said but it is what comes up in my system profiler so I figured it might be helpful.

When I first installed Lubuntu two year ago I was impressed at how lightning fast myold HP Compaq n6220 laptop booted up...something like 15 seconds. Little by little I have been nagged to install updates and my bootup time is now about 90 to 120 seconds.

I researched on this forum a little and used 
systemd-analyze blame in the terminal mode. Here is what it came up with: 

```
20.371s networking.service
          19.849s apport.service
          16.780s dev-sda1.device
          16.434s ModemManager.service
          13.858s apparmor.service
          11.604s grub-common.service
          11.276s irqbalance.service
          10.844s ondemand.service
           9.969s lightdm.service
           9.873s NetworkManager-wait-online.service
           9.580s console-kit-log-system-start.service
           9.477s rsyslog.service
           9.240s alsa-restore.service
           9.211s gpu-manager.service
           9.201s pppd-dns.service
           9.200s systemd-user-sessions.service
           9.140s avahi-daemon.service
           8.224s apt-daily.service
           4.757s NetworkManager.service
           3.691s console-setup.service
           2.897s systemd-tmpfiles-setup.service
           2.773s thermald.service
           2.771s systemd-udevd.service
           2.726s colord.service
           2.287s keyboard-setup.service
           2.213s accounts-daemon.service
           1.864s systemd-tmpfiles-setup-dev.service
           1.678s polkitd.service
           1.659s plymouth-start.service
           1.510s binfmt-support.service
           1.353s systemd-journald.service
           1.221s systemd-modules-load.service
           1.139s wpa_supplicant.service
           1.074s dev-hugepages.mount
           1.073s sys-kernel-debug.mount
           1.066s upower.service
            921ms dev-mqueue.mount
            894ms systemd-logind.service
            827ms systemd-udev-trigger.service
            822ms systemd-sysctl.service
            806ms systemd-update-utmp.service
            788ms udisks2.service
            735ms ufw.service
            707ms systemd-journal-flush.service
            700ms systemd-backlight@backlight:intel_backlight.service
            571ms plymouth-read-write.service
            569ms dns-clean.service
            513ms kmod-static-nodes.service
            483ms systemd-random-seed.service
            458ms dev-disk-by\x2duuid-238b078c\x2daf7d\x2d4bb7\x2dabf6\x2d8b13bd7
            297ms resolvconf.service
            189ms proc-sys-fs-binfmt_misc.mount
            157ms user@1000.service
            133ms systemd-remount-fs.service
             92ms setvtrgb.service
             77ms snapd.autoimport.service
             52ms systemd-tmpfiles-clean.service
             50ms snapd.socket
             38ms ntp.service
             37ms rc-local.service
             25ms systemd-update-utmp-runlevel.service
             18ms rtkit-daemon.service
             18ms ureadahead-stop.service
             13ms sys-fs-fuse-connections.mount
             11ms plymouth-quit-wait.service
              9ms systemd-rfkill.service
              8ms minidlna.service
```

Holy smokes! No wonder this poor ol' laptop chokes on bootup but I have no idea what is important and what is not to
retain from all of these files.

Can anyone help me with what is definitely unnecessary so I can delete it? I basically just use my laptop for email (Thunderbird) with Firefox as my browser and occasionally use GIMP, Libreoffice Writer, Audacity and VLC for audio/video.

Thanks for any direction the community can provide.

---

