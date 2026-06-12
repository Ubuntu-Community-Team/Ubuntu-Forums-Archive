---
title: "Slow boot time on my Ubuntu"
date: 2017-02-07
forum: General Help
---

### Post by absolutezer02 on 2017-02-07
So I am starting to like Ubuntu quite a lot but I don't know why it boots so slow always...
I am dual booting with windows but I have seen it on the laptop of a friend which is a lot older, and he boots like in 5-6 seconds.
Can someone please look at the output of systemd-analyze blame?

```
         30.416s apt-daily.service
         10.593s systemd-fsck@dev-disk-by\x2duuid-B21C\x2d554E.service
          8.330s NetworkManager-wait-online.service
          6.883s dev-sda8.device
          4.596s nmbd.service
          4.343s samba-ad-dc.service
          3.865s teamviewerd.service
          3.120s NetworkManager.service
          2.989s thermald.service
          2.287s accounts-daemon.service
          2.225s ModemManager.service
          1.626s vboxdrv.service
          1.436s gpu-manager.service
          1.434s vpnagentd.service
          1.206s systemd-udevd.service
          1.164s keyboard-setup.service
          1.018s iio-sensor-proxy.service
           977ms plymouth-start.service
           964ms grub-common.service
           963ms systemd-backlight@backlight:intel_backlight.service
           956ms udisks2.service
           946ms systemd-tmpfiles-setup-dev.service
           785ms polkitd.service
           754ms systemd-journald.service
           679ms bluetooth.service
           605ms lightdm.service
           567ms dev-mqueue.mount
           565ms sys-kernel-debug.mount
           546ms systemd-modules-load.service
           533ms apparmor.service
           483ms kmod-static-nodes.service
           422ms networking.service
           413ms irqbalance.service
           375ms systemd-rfkill.service
           341ms systemd-tmpfiles-setup.service
           339ms upower.service
           331ms avahi-daemon.service
           319ms systemd-logind.service
           290ms console-setup.service
           286ms ondemand.service
           279ms wpa_supplicant.service
           278ms speech-dispatcher.service
           252ms pppd-dns.service
           248ms systemd-user-sessions.service
           240ms rsyslog.service
           236ms smbd.service
           197ms apport.service
           166ms systemd-sysctl.service
           161ms systemd-timesyncd.service
           140ms ufw.service
           139ms colord.service
           131ms systemd-update-utmp.service
           114ms systemd-remount-fs.service
           107ms systemd-udev-trigger.service
           101ms systemd-journal-flush.service
            88ms boot-efi.mount
            84ms dev-hugepages.mount
            51ms setvtrgb.service
            36ms plymouth-read-write.service
            34ms binfmt-support.service
            25ms systemd-random-seed.service
            19ms user@1000.service
            16ms snapd.autoimport.service
            14ms alsa-restore.service
            12ms snapd.socket
             7ms ureadahead-stop.service
             6ms rc-local.service
             6ms dns-clean.service
             5ms vboxweb-service.service
             4ms proc-sys-fs-binfmt_misc.mount
             4ms resolvconf.service
             3ms vboxautostart-service.service
             3ms vboxballoonctrl-service.service
             3ms systemd-update-utmp-runlevel.service
             3ms plymouth-quit-wait.service
             3ms rtkit-daemon.service
             2ms sys-fs-fuse-connections.mount

```
Thank you in advance!

---

### Post by Impavidus on 2017-02-08
Some information on your hardware may help. In particular the hard drive. With an SSD (common in new laptops or as smaller drive in desktops) boot times on the order of 10 seconds are normal, with a fast spinning drive (desktops and older heavy laptops) it should be about 23 seconds, with a slow spinning drive (older light laptops) 30 seconds or more.

I've never looked at systemd-analyze blame. Someone else may be more familiar with it.

---

### Post by RobGoss on 2017-02-08
Comparing the too machines may not be a good way to analyze your boot time unless they are identical with hardware and specs 

There are a few ways to help your boot time, one is by disabling some programs at startup 

If you're using Ubuntu 16.04 with the Unity desktop you can click on the unity menu in the left side of your desktop and type **startup application**, this will bring up a dialog box which will allow you to disable and enable startup applications

Make sure you have a full understanding of what applications you're disabling. On older machine the boot time may not be as fast but I feel it's still acceptable in most cases if it's only a few seconds...

After doing so reboot your system and see if it helps

---

### Post by Autodave on 2017-02-08
What Win version are you running? Does Linux boot up quicker than Win? Please give specs on your machine.

---

### Post by Morbius1 on 2017-02-08
You might want to run systemd-analyze a different way to provide the folks here with more information:
```
systemd-analyze critical-chain
```
"blame" just lists the time it takes for the service to start. It may be running in parallel with something else or not involved in getting to the desktop.

For example if I run "blame" it lists:
>  1min 4.156s apt-daily.service
But it doesn't take 1 min+ to boot.

---

