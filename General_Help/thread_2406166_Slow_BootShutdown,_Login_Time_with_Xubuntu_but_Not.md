---
title: "Slow Boot/Shutdown, Login Time with Xubuntu but Not Ubuntu"
date: 2018-11-16
forum: General Help
---

### Post by Gaboontoo on 2018-11-16
I have searched regarding slow boot times already and have come across some clues but many of the solutions appear specific to someone's particular hardware or other circumstances.

I have two laptops with very similar hardware that makes me think something in Xubuntu is the problem. Both are HP Compaq 2510p (Core 2 Duo @ 1.2 GHz, 4 GB RAM) and only the one with Xubuntu takes several minutes to boot and less, but still abnormally long, time to shutdown. Even after logging in, the system will also just idle until finally there's HDD activity. I also have issues putting the Xubuntu laptop to sleep where the system just goes into semi-sleep but not entirely. 

I ran the systemd commands and have pasted the outputs below. I also generated a graph. Something that seems to have made things worse for the Xubuntu laptop is that I upgraded the HDD to a SSD and expanded the partition after cloning to use the extra space available. However, to be clear, the Xubuntu laptop's boot time was always slow even with the prior traditional HDD. Post-SSD the system seems to take a bit longer. Much of this delayed boot/shutdown/login time is the system just sitting there with no HDD activity indicated at all until it finally starts kicking in.

```
systemd-analyze
Startup finished in 1min 12.390s (kernel) + 1min 6.543s (userspace) = 2min 18.934s
graphical.target reached after 1min 6.172s in userspace
```

```
systemd-analyze blame
         31.787s plymouth-start.service
         31.727s lightdm.service
         31.671s plymouth-quit-wait.service
         29.455s plymouth-read-write.service
         13.394s NetworkManager-wait-online.service
          4.498s dev-sda1.device
          2.516s apparmor.service
          2.450s snapd.service
          2.072s hddtemp.service
          2.007s dev-loop0.device
          2.001s dev-loop2.device
          1.996s dev-loop1.device
          1.726s systemd-journal-flush.service
          1.317s udisks2.service
          1.203s networkd-dispatcher.service
           884ms ModemManager.service
           821ms systemd-udev-trigger.service
           817ms accounts-daemon.service
           802ms upower.service
           750ms keyboard-setup.service
           697ms NetworkManager.service
           688ms swapfile.swap
           595ms systemd-logind.service
           525ms iio-sensor-proxy.service
           509ms lm-sensors.service
           503ms avahi-daemon.service
           503ms systemd-journald.service
           491ms alsa-restore.service
           487ms bluetooth.service
           479ms grub-common.service
           457ms wpa_supplicant.service
           384ms pgl.service
           371ms tlp.service
           366ms gpu-manager.service
           301ms apport.service
           284ms speech-dispatcher.service
           221ms systemd-timesyncd.service
           214ms thermald.service
           182ms systemd-resolved.service
           158ms systemd-udevd.service
           157ms binfmt-support.service
           153ms colord.service
           142ms user@1000.service
           123ms pppd-dns.service
           122ms systemd-modules-load.service
           121ms geoclue.service
           102ms snap-skype-63.mount
           100ms sys-kernel-debug.mount
            96ms snap-skype-66.mount
            95ms rsyslog.service
            93ms systemd-tmpfiles-setup.service
            90ms kmod-static-nodes.service
            79ms dev-mqueue.mount
            76ms systemd-tmpfiles-setup-dev.service
            73ms console-setup.service
            72ms kerneloops.service
            72ms ufw.service
            72ms snapd.seeded.service
            62ms systemd-remount-fs.service
            60ms systemd-tmpfiles-clean.service
            57ms systemd-sysctl.service
            53ms polkit.service
            53ms sys-fs-fuse-connections.mount
            52ms snap-core-5742.mount
            50ms dev-hugepages.mount
            46ms sys-kernel-config.mount
            44ms systemd-user-sessions.service
            36ms systemd-update-utmp-runlevel.service
            32ms proc-sys-fs-binfmt_misc.mount
            32ms rtkit-daemon.service
            27ms systemd-update-utmp.service
            25ms systemd-backlight@backlight:acpi_video0.service
            19ms ureadahead-stop.service
            18ms setvtrgb.service
            15ms systemd-backlight@backlight:intel_backlight.service
            10ms systemd-random-seed.service
             3ms snapd.socket
```

```
systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @1min 5.964s
&#9492;&#9472;multi-user.target @1min 5.961s
  &#9492;&#9472;getty.target @1min 5.960s
    &#9492;&#9472;getty@tty1.service @1min 5.959s
      &#9492;&#9472;system-getty.slice @1min 5.956s
        &#9492;&#9472;setvtrgb.service @1min 5.940s +14ms
          &#9492;&#9472;systemd-user-sessions.service @34.312s +44ms
            &#9492;&#9472;network.target @34.293s
              &#9492;&#9472;NetworkManager.service @33.482s +808ms
                &#9492;&#9472;dbus.service @33.401s
                  &#9492;&#9472;basic.target @33.172s
                    &#9492;&#9472;sockets.target @33.172s
                      &#9492;&#9472;snapd.socket @33.168s +3ms
                        &#9492;&#9472;sysinit.target @33.154s
                          &#9492;&#9472;cryptsetup.target @33.154s
                            &#9492;&#9472;systemd-ask-password-wall.path @411ms
                              &#9492;&#9472;-.mount @405ms
                                &#9492;&#9472;system.slice @413ms
                                  &#9492;&#9472;-.slice @405ms
```

Any help is greatly appreciated. Thanks!

---

### Post by Gaboontoo on 2018-11-18
Does anyone have any ideas or anything to try? As an update, putting the machine to sleep works as it should now. However, waking from sleep results in a noticeable delay (10+ seconds) where the display is blank and the network activity indicator on the laptop blinks until the login screen finally appears.

---

