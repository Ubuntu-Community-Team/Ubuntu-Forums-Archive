---
title: "Boot problems"
date: 2019-07-16
forum: General Help
---

### Post by michelangelo98 on 2019-07-16
Hi all!
Since I've installed ubuntu 19.04 I'm having boot problems: freeze on purple screen or long loadings. First thanks to the log of boot-repair I added a boot partition (using [this]("https://help.ubuntu.com/community/BootPartition") guide) that improves a lot the problems, but sometimes it still freeze on purple screen. So with [this ]("http://paste.ubuntu.com/p/rBv4XTFpsd/") log of boot-repair I'm facing problems that i don't now how to solve.
Thank in advanced!

---

### Post by oldfred on 2019-07-16
What brand/model system?
What video card/chip?

You do have newer UEFI system, but Ubuntu installed in the now older BIOS/MBR configuration. That should work, but you must make sure UEFI is set for BIOS/CSM/Legacy boot only.

Most desktop systems should not need a separate /boot partition, but your configuration should be ok.
But sometimes a smaller / (root) of 25GB and then rest of drive as /home and/or data partitions may be better.

Post these:
        systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain 
    
Some other slow boot threads:
       [https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html) 
    
I have made these changes in one of may installs. I have several to experiment with.
       turned off NetworkManager-wait
Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

---

### Post by michelangelo98 on 2019-07-19
Thanks for the reply!
I have i5-5200U and a Nvidia vga that i disabled to be sure that graphics drivers doesn't cause the freezing. 

Here is the result of [COLOR=#000000]systemd-analyze:

[/COLOR]Startup finished in 3.893s (kernel) + 54.432s (userspace) = 58.326s 
graphical.target reached after 54.283s in userspace

 ```
systemd-analyze blame:

         24.778s plymouth-quit-wait.service
         12.258s dev-sda1.device
         10.485s snapd.service
         10.071s NetworkManager-wait-online.service
          8.795s networkd-dispatcher.service
          8.594s accounts-daemon.service
          8.454s ModemManager.service
          6.983s udisks2.service
          6.717s plymouth-read-write.service
          6.654s dev-loop9.device
          6.553s dev-loop14.device
          6.353s dev-loop13.device
          6.114s dev-loop12.device
          6.090s dev-loop16.device
          5.867s dev-loop17.device
          5.768s dev-loop19.device
          5.768s dev-loop11.device
          5.687s dev-loop7.device
          5.545s dev-loop15.device
          5.531s dev-loop8.device
          5.443s dev-loop18.device
          5.398s dev-loop10.device
          5.056s apparmor.service
          4.993s NetworkManager.service
          4.737s dns-clean.service
          4.450s apport.service
          4.048s grub-common.service
          3.705s avahi-daemon.service
          3.657s systemd-logind.service
          3.652s bluetooth.service
          3.644s thermald.service
          3.341s dev-loop6.device
          3.320s gpu-manager.service
          3.310s switcheroo-control.service
          3.260s dev-loop2.device
          3.212s rsyslog.service
          3.172s wpa_supplicant.service
          3.121s dev-loop3.device
          3.089s grub-initrd-fallback.service
          3.068s dev-loop5.device
          3.063s dev-loop4.device
          2.830s pppd-dns.service
          2.813s systemd-rfkill.service
          2.745s dev-loop0.device
          2.702s dev-loop1.device
          2.143s polkit.service
          2.098s console-setup.service
          1.890s gdm.service
          1.361s upower.service
          1.163s systemd-sysctl.service
          1.156s systemd-fsck@dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2da8
          1.042s fwupd.service
           977ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           762ms networking.service
           718ms snap-code-11.mount
           688ms systemd-modules-load.service
           684ms snap-onlyoffice\x2ddesktopeditors-31.mount
           649ms snap-gnome\x2dcharacters-296.mount
           633ms snap-gnome\x2d3\x2d28\x2d1804-67.mount
           626ms snap-code-10.mount
           620ms snap-gnome\x2d3\x2d28\x2d1804-63.mount
           607ms systemd-tmpfiles-setup.service
           546ms systemd-tmpfiles-setup-dev.service
           489ms snap-gnome\x2dcalculator-406.mount
           470ms snap-gnome\x2dsystem\x2dmonitor-95.mount
           453ms snap-gnome\x2dsystem\x2dmonitor-100.mount
           450ms systemd-sysusers.service
           449ms keyboard-setup.service
           439ms snap-gnome\x2dlogs-61.mount
           411ms snap-gnome\x2dcharacters-292.mount
           394ms swapfile.swap
           393ms snap-thunderbird-37.mount
           390ms snap-gtk\x2dcommon\x2dthemes-1313.mount
           381ms snap-core-7270.mount
           374ms snap-gtk\x2dcommon\x2dthemes-1198.mount
           371ms snap-onlyoffice\x2ddesktopeditors-35.mount
           363ms plymouth-start.service
           345ms systemd-update-utmp.service
           343ms systemd-udev-trigger.service
           336ms snap-thunderbird-34.mount
           325ms snap-core-7169.mount
           306ms systemd-journald.service
           298ms snap-core18-1066.mount
           294ms snap-core18-1055.mount
           290ms motd-news.service
           275ms systemd-timesyncd.service
           273ms systemd-resolved.service
           203ms colord.service
           197ms dev-hugepages.mount
           195ms sys-kernel-debug.mount
           190ms systemd-random-seed.service
           165ms systemd-remount-fs.service
           151ms boot.mount
           148ms setvtrgb.service
           139ms snapd.seeded.service
           130ms systemd-user-sessions.service
           127ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
           113ms openvpn.service
           104ms ifupdown-pre.service
            88ms kerneloops.service
            75ms bolt.service
            64ms ufw.service
            56ms kmod-static-nodes.service
            31ms systemd-udevd.service
            25ms snapd.socket
            23ms systemd-update-utmp-runlevel.service
            22ms rtkit-daemon.service
            21ms [EMAIL="user-runtime-dir@1000.servic"]user-runtime-dir@1000.servic[/EMAIL]e
             8ms systemd-journal-flush.service
             5ms dev-mqueue.mount
             3ms sys-kernel-config.mount
             2ms sys-fs-fuse-connections.mount
```

```
and finally systemd-analyze critical-chain:

graphical.target @54.283s
&#9492;&#9472;multi-user.target @54.282s
  &#9492;&#9472;kerneloops.service @39.511s +88ms
    &#9492;&#9472;network-online.target @39.450s
      &#9492;&#9472;NetworkManager-wait-online.service @29.378s +10.071s
        &#9492;&#9472;NetworkManager.service @24.372s +4.993s
          &#9492;&#9472;dbus.service @24.363s
            &#9492;&#9472;basic.target @23.879s
              &#9492;&#9472;sockets.target @23.879s
                &#9492;&#9472;snapd.socket @23.853s +25ms
                  &#9492;&#9472;sysinit.target @23.799s
                    &#9492;&#9472;systemd-update-utmp.service @22.001s +345ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @21.392s +607ms
                        &#9492;&#9472;local-fs.target @17.080s
                          &#9492;&#9472;boot.mount @16.929s +151ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-3eef6465\x2ddc97\
                              &#9492;&#9472;dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2d
lines 1-20/20 (END)...skipping...
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


graphical.target @54.283s
&#9492;&#9472;multi-user.target @54.282s
  &#9492;&#9472;kerneloops.service @39.511s +88ms
    &#9492;&#9472;network-online.target @39.450s
      &#9492;&#9472;NetworkManager-wait-online.service @29.378s +10.071s
        &#9492;&#9472;NetworkManager.service @24.372s +4.993s
          &#9492;&#9472;dbus.service @24.363s
            &#9492;&#9472;basic.target @23.879s
              &#9492;&#9472;sockets.target @23.879s
                &#9492;&#9472;snapd.socket @23.853s +25ms
                  &#9492;&#9472;sysinit.target @23.799s
                    &#9492;&#9472;systemd-update-utmp.service @22.001s +345ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @21.392s +607ms
                        &#9492;&#9472;local-fs.target @17.080s
                          &#9492;&#9472;boot.mount @16.929s +151ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2da8f8\x2d16de9f8e1f9d.service @15.712s +1.156s
                              &#9492;&#9472;dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2da8f8\x2d16de9f8e1f9d.device @15.710s
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-20/20 (END)


```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


```
graphical.target @54.283s
&#9492;&#9472;multi-user.target @54.282s
  &#9492;&#9472;kerneloops.service @39.511s +88ms
    &#9492;&#9472;network-online.target @39.450s
      &#9492;&#9472;NetworkManager-wait-online.service @29.378s +10.071s
        &#9492;&#9472;NetworkManager.service @24.372s +4.993s
          &#9492;&#9472;dbus.service @24.363s
            &#9492;&#9472;basic.target @23.879s
              &#9492;&#9472;sockets.target @23.879s
                &#9492;&#9472;snapd.socket @23.853s +25ms
                  &#9492;&#9472;sysinit.target @23.799s
                    &#9492;&#9472;systemd-update-utmp.service @22.001s +345ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @21.392s +607ms
                        &#9492;&#9472;local-fs.target @17.080s
                          &#9492;&#9472;boot.mount @16.929s +151ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2da8f8\x2d16de9f8e1f9d.service @15.712s +1.156s
                              &#9492;&#9472;dev-disk-by\x2duuid-3eef6465\x2ddc97\x2d4c38\x2da8f8\x2d16de9f8e1f9d.device @15.710s
```

---

### Post by oldfred on 2019-07-19
Please use code tags for longer text or terminal output. Also preserves formatting.

One change I have tried is using  noplymouth boot parameter. You can test just by editing grub when you boot. Use e to edit and on linux line replace quiet splash with noplymouth. You then see the detail boot process instead of a "pretty" screen. I prefer to see process anyway, but now new system boots so fast that it scrolls by very quickly. Back when boot was slow it scrolled by and was very readable.

If it works you  can edit grub to make it permanent.
sudo nano /etc/default/grub

I comment out original line to make it easy to change back if needed.
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

After edit:
sudo update-grub

---

### Post by michelangelo98 on 2019-07-24
Hi,
i've made the change you said and the boot now is really fast! Thanks for help!

---

