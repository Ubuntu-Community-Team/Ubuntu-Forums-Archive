---
title: "Very slow boot times on dell xps 13 running zesty"
date: 2017-07-30
forum: General Help
---

### Post by HappyHappyJoy on 2017-07-30
Brand new i5 with 256gig ssd takes almost 108 seconds to boot.  Fresh install, not dual booting.  

When I run dmesg the big delay point is:

[    6.788952] ath10k_pci 0000:3a:00.0 wlp58s0: renamed from wlan0
[   94.098579] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

There are a few other delays, but that is the big one. 

Any ideas?  Thanks in advance.

---

### Post by Autodave on 2017-07-30
What video card does it have? Did you install any video driver yet? If you did, where did you get the driver from?

---

### Post by HappyHappyJoy on 2017-07-30
I have not installed any video driver.

On my purchase order the video driver is listed as sku #490-BDFO / Intel HD Graphics

Thanks for your response.

---

### Post by ajgreeny on 2017-07-30
Show us the output in terminal of command ```
systemd-analyze blame
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by HappyHappyJoy on 2017-08-02
```

          4.769s systemd-resolved.service
          3.848s fwupd.service
          1.402s rtkit-daemon.service
           435ms dev-nvme0n1p1.device
           192ms networking.service
           155ms lightdm.service
           152ms plymouth-quit-wait.service
           127ms gpu-manager.service
           117ms ModemManager.service
           115ms systemd-timesyncd.service
           113ms apparmor.service
           110ms repowerd.service
           108ms irqbalance.service
            91ms accounts-daemon.service
            76ms keyboard-setup.service
            75ms NetworkManager.service
            69ms thermald.service
            69ms systemd-udev-trigger.service
            64ms grub-common.service
            60ms systemd-logind.service
            58ms apport.service
            57ms speech-dispatcher.service
            47ms upower.service
            45ms bluetooth.service
            43ms udisks2.service
            37ms avahi-daemon.service
            32ms rsyslog.service
            28ms systemd-udevd.service
            27ms user@1000.service
            25ms systemd-journald.service
            25ms pppd-dns.service
            25ms snapd.autoimport.service
            23ms systemd-tmpfiles-clean.service
            20ms colord.service
            16ms ureadahead-stop.service
            16ms alsa-restore.service
            16ms plymouth-start.service
            16ms polkit.service
            14ms systemd-tmpfiles-setup-dev.service
            13ms systemd-tmpfiles-setup.service
            13ms systemd-backlight@backlight:intel_backlight.service
            13ms systemd-modules-load.service
            12ms setvtrgb.service
            11ms plymouth-read-write.service
            10ms dns-clean.service
             9ms dev-hugepages.mount
             8ms kmod-static-nodes.service
             7ms systemd-backlight@leds:dell::kbd_backlight.service
             7ms resolvconf.service
             7ms ufw.service
             7ms console-setup.service
             7ms wpa_supplicant.service
             7ms systemd-sysctl.service
             6ms dev-mqueue.mount
             6ms systemd-update-utmp.service
             6ms systemd-remount-fs.service
             5ms sys-fs-fuse-connections.mount
             5ms systemd-rfkill.service
             5ms NetworkManager-dispatcher.service
             5ms systemd-journal-flush.service
             5ms systemd-user-sessions.service
             4ms sys-kernel-debug.mount
             3ms systemd-update-utmp-runlevel.service
             3ms systemd-random-seed.service
             1ms openvpn.service
             1ms swapfile.swap
           543us snapd.socket


```

Nothing in there seems like it is taking very long.  

Thanks again for everyones help.

---

