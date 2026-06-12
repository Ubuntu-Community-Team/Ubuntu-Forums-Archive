---
title: "Huge increase in boot time with kernel 4.10 compared to 4.4"
date: 2017-05-22
forum: General Help
---

### Post by lucian-iuga-gmail on 2017-05-22
Hi all!

I am using 17.04 now and the boot times with kernels 4.8 and 4.10 are huge compared to what I used to have with the 4.4 kernel in 16.04. I had the same problem in 16.10 with 4.8 kernel, but postponed asking about it.

For comparison, I also installed kernel 4.4 under 17.04 and the difference is huge. Kernel 4.4 is not normally found in repos for 17.04, but I enabled an older repo and installed it.

I did some googling and I did notice other folks having similar issues with 4.8 kernel, but by the output of systemd-analyze, my instance is different from anything I have seen anywhere. Unfortunately, I am not skilled enough to take the investigation further.

I am posting below the outputs of
      uname -a
      systemd-analyze blame
      systemd-analyze critical-chain

from both kernels.

Not sure if it makes sense to post the hardware, as it doesn't seem to have anything to do with it. I will do it in case it is needed.

Any help will be greatly appreciated.

**Kernel 4.10 - long boot time**
```
$ uname -a
Linux ubuntu 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ systemd-analyze blame
         11.232s lightdm.service
         11.228s plymouth-quit-wait.service
          4.008s apparmor.service
          3.528s colord.service
          2.022s fwupd.service
          1.148s dev-sda1.device
           751ms networking.service
           739ms click-system-hooks.service
           597ms user@1000.service
           358ms systemd-resolved.service
           357ms systemd-cryptsetup@cryptswap1.service
           322ms upower.service
           243ms repowerd.service
           226ms apport.service
           221ms accounts-daemon.service
           216ms ModemManager.service
           199ms irqbalance.service
           194ms grub-common.service
           184ms speech-dispatcher.service
           178ms keyboard-setup.service
           171ms systemd-logind.service
           162ms avahi-daemon.service
           160ms gpu-manager.service
           153ms NetworkManager.service
           139ms alsa-restore.service
           129ms systemd-rfkill.service
           123ms systemd-tmpfiles-setup-dev.service
           122ms rsyslog.service
           114ms systemd-fsck@dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.service
           103ms systemd-timesyncd.service
            99ms systemd-udev-trigger.service
            90ms pppd-dns.service
            82ms systemd-tmpfiles-clean.service
            80ms systemd-journald.service
            63ms binfmt-support.service
            62ms systemd-modules-load.service
            59ms udisks2.service
            54ms snapd.autoimport.service
            52ms systemd-update-utmp.service
            48ms systemd-udevd.service
            46ms bluetooth.service
            41ms proc-sys-fs-binfmt_misc.mount
            39ms home.mount
            36ms systemd-tmpfiles-setup.service
            33ms rc-local.service
            33ms openvpn.service
            31ms systemd-user-sessions.service
            30ms dev-mqueue.mount
            29ms dev-hugepages.mount
            24ms polkit.service
            23ms wpa_supplicant.service
            21ms sys-kernel-debug.mount
            21ms kmod-static-nodes.service
            17ms dev-mapper-cryptswap1.swap
            17ms plymouth-read-write.service
            16ms systemd-backlight@backlight:acpi_video0.service
            16ms systemd-journal-flush.service
            15ms dns-clean.service
            15ms plymouth-start.service
            14ms ufw.service
            12ms systemd-sysctl.service
            11ms setvtrgb.service
             9ms ureadahead-stop.service
             9ms console-setup.service
             8ms systemd-remount-fs.service
             6ms systemd-update-utmp-runlevel.service
             6ms rtkit-daemon.service
             5ms resolvconf.service
             5ms sys-fs-fuse-connections.mount
             4ms systemd-random-seed.service
             4ms snapd.socket
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


$ systemd-analyze critical-chain
graphical.target @17.536s
&#9492;&#9472;multi-user.target @17.536s
  &#9492;&#9472;getty.target @17.536s
    &#9492;&#9472;getty@tty1.service @17.536s
      &#9492;&#9472;system-getty.slice @17.535s
        &#9492;&#9472;setvtrgb.service @17.523s +11ms
          &#9492;&#9472;systemd-user-sessions.service @6.258s +31ms
            &#9492;&#9472;network.target @6.254s
              &#9492;&#9472;wpa_supplicant.service @6.472s +23ms
                &#9492;&#9472;basic.target @5.504s
                  &#9492;&#9472;sockets.target @5.504s
                    &#9492;&#9472;snapd.socket @5.499s +4ms
                      &#9492;&#9472;sysinit.target @5.499s
                        &#9492;&#9472;apparmor.service @1.490s +4.008s
                          &#9492;&#9472;local-fs.target @1.485s
                            &#9492;&#9472;home.mount @1.445s +39ms
                              &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.service @1.327s +114ms
                                &#9492;&#9472;dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.device @1.325s

```

**Kernel 4.4 - Shorter boot time**
```
$ uname -a
Linux pestisor-ubuntu 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ systemd-analyze blame
          3.944s apparmor.service
          2.077s fwupd.service
          1.218s dev-sda1.device
           719ms networking.service
           712ms click-system-hooks.service
           613ms user@1000.service
           595ms lightdm.service
           576ms plymouth-quit-wait.service
           476ms systemd-resolved.service
           475ms repowerd.service
           372ms systemd-logind.service
           261ms apport.service
           223ms irqbalance.service
           197ms keyboard-setup.service
           187ms grub-common.service
           182ms speech-dispatcher.service
           179ms pppd-dns.service
           169ms systemd-rfkill.service
           163ms gpu-manager.service
           156ms upower.service
           150ms rsyslog.service
           149ms avahi-daemon.service
           123ms systemd-cryptsetup@cryptswap1.service
           115ms alsa-restore.service
           113ms systemd-udev-trigger.service
           101ms udisks2.service
            97ms bluetooth.service
            96ms systemd-timesyncd.service
            91ms binfmt-support.service
            91ms systemd-journald.service
            89ms polkit.service
            80ms systemd-tmpfiles-setup-dev.service
            60ms snapd.autoimport.service
            58ms dns-clean.service
            52ms systemd-modules-load.service
            45ms systemd-fsck@dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.service
            41ms systemd-udevd.service
            40ms systemd-update-utmp.service
            38ms ureadahead-stop.service
            37ms dev-mqueue.mount
            23ms proc-sys-fs-binfmt_misc.mount
            21ms systemd-tmpfiles-setup.service
            20ms sys-kernel-debug.mount
            20ms wpa_supplicant.service
            20ms dev-hugepages.mount
            20ms home.mount
            18ms ufw.service
            17ms dev-mapper-cryptswap1.swap
            16ms kmod-static-nodes.service
            16ms colord.service
            16ms plymouth-read-write.service
            16ms plymouth-start.service
            12ms systemd-sysctl.service
            11ms systemd-journal-flush.service
            10ms systemd-user-sessions.service
            10ms rc-local.service
            10ms openvpn.service
             8ms systemd-backlight@backlight:acpi_video0.service
             7ms systemd-update-utmp-runlevel.service
             7ms systemd-remount-fs.service
             7ms resolvconf.service
             5ms console-setup.service
             4ms rtkit-daemon.service
             4ms setvtrgb.service
             3ms systemd-random-seed.service
             2ms snapd.socket
             2ms sys-fs-fuse-connections.mount
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

$ systemd-analyze critical-chain
graphical.target @6.839s
&#9492;&#9472;multi-user.target @6.839s
  &#9492;&#9472;getty.target @6.839s
    &#9492;&#9472;getty@tty1.service @6.839s
      &#9492;&#9472;system-getty.slice @6.838s
        &#9492;&#9472;setvtrgb.service @6.833s +4ms
          &#9492;&#9472;systemd-user-sessions.service @6.206s +10ms
            &#9492;&#9472;network.target @6.205s
              &#9492;&#9472;wpa_supplicant.service @6.552s +20ms
                &#9492;&#9472;basic.target @5.488s
                  &#9492;&#9472;sockets.target @5.487s
                    &#9492;&#9472;snapd.socket @5.485s +2ms
                      &#9492;&#9472;sysinit.target @5.481s
                        &#9492;&#9472;apparmor.service @1.516s +3.944s
                          &#9492;&#9472;local-fs.target @1.513s
                            &#9492;&#9472;home.mount @1.493s +20ms
                              &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.service @1.429s +45ms
                                &#9492;&#9472;dev-disk-by\x2duuid-578da18b\x2daf7b\x2d44a4\x2d9dc3\x2d3d9490cf9d9f.device @1.419s

```

---

### Post by lucian-iuga-gmail on 2017-06-06
Bump

---

### Post by QIII on 2017-06-06
Hello!

Waiting two weeks to bump pretty much guaranteed that your thread settled into the muck at the bottom of the sea and was forgotten.

Please feel free to bump if you have not gotten a response in about 12 hours time.

---

### Post by lucian-iuga-gmail on 2017-06-22
Thanks for the tip. I would do that, but I am not really able to track this so closely.

---

### Post by lucian-iuga-gmail on 2017-09-09
Late bump. The problem is still there at 4.10.0-33-generic

---

### Post by lucian-iuga-gmail on 2018-03-07
If anyone can help, I am still looking for a solution to this. The situation is still there with kernel 4.15.

For now, I keep booting into 4.4 kernels from older releases of Ubuntu, but I don't know for how long that will still be possible. The 4.4 branch is still getting new builds, but that will probably stop at some point.

---

