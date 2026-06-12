---
title: "How to increase boot time"
date: 2017-01-15
forum: General Help
---

### Post by Emmanuele on 2017-01-15
Hi all, mine it is not a true problem but only a simple question. I was a Debian user and every boot was about 5 / 15 sec at he most (from booting to login screen). With Ubuntu boot is about  20 / 35 sec. Not a real problem but curiosity: why if PC is always the same are there such delay? Is there a possibility to improve such time? I've checked my journal and I've not found any anomaly (per my opinion) only some warning in "/usr/lib/gdm3/gdm-x-session". Should be these warnings the causes of such delays?

My PC is:

SSD 250GB Samsung EVO
16GB ram 1866Mhz GSkill
i7 3770K @4.2Ghz

and I attach my latest journal... please help me to understand... thanks!

---

### Post by SeijiSensei on 2017-01-15
What is the value for GRUB_TIMEOUT in /etc/default/grub?  That is the number of seconds grub waits before booting the default kernel.  If you change it, run "sudo update-grub" afterward.

---

### Post by Emmanuele on 2017-01-16
Thanks for your reply. TIMEOUT is set to 0.

---

### Post by deadflowr on 2017-01-16
Look at 
```
systemd-analyze blame
```
for how long various service are taking to load/start 
as well as what services are starting at boot.

---

### Post by Emmanuele on 2017-01-17
Thanks for your reply. Here attached latest figure. Could you please help me to understand wher can I improve boot time... if any possibility?

```

          1.239s plymouth-quit-wait.service
           419ms rtirq.service
           416ms media-Dati.mount
           358ms accounts-daemon.service
           354ms NetworkManager.service
           335ms gpu-manager.service
           319ms thermald.service
           318ms grub-common.service
           317ms irqbalance.service
           308ms dev-sda2.device
           303ms iio-sensor-proxy.service
           273ms avahi-daemon.service
           228ms ondemand.service
           200ms apport.service
            60ms networking.service
            58ms speech-dispatcher.service
            55ms apparmor.service
            49ms systemd-udev-trigger.service
            48ms console-setup.service
            47ms upower.service
            42ms gdomap.service
            41ms udisks2.service
            38ms systemd-timesyncd.service
            38ms systemd-logind.service
            35ms keyboard-setup.service
            35ms rsyslog.service
            29ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-8AAA\x2d5A3C.servic"]systemd-fsck@dev-disk-by\x2duuid-8AAA\x2d5A3C.servic[/EMAIL]e
            29ms systemd-journald.service
            24ms systemd-udevd.service
            23ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-aab32048\x2d75c2\x2d43ab\x2d987f\x2d42eb0ba47eef.servic"]systemd-fsck@dev-disk-by\x2duuid-aab32048\x2d75c2\x2d43ab\x2d987f\x2d42eb0ba47eef.servic[/EMAIL]e
            21ms systemd-tmpfiles-setup-dev.service
            20ms systemd-modules-load.service
            17ms colord.service
            14ms binfmt-support.service
            14ms plymouth-read-write.service
            13ms polkitd.service
            13ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            12ms gdm.service
            12ms [EMAIL="user@121.servic"]user@121.servic[/EMAIL]e
            12ms plymouth-start.service
            11ms alsa-restore.service
            10ms resolvconf.service
            10ms systemd-tmpfiles-setup.service
             8ms wpa_supplicant.service
             8ms systemd-journal-flush.service
             7ms dev-hugepages.mount
             6ms systemd-user-sessions.service
             6ms systemd-update-utmp.service
             6ms [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
             6ms vboxballoonctrl-service.service
             6ms kmod-static-nodes.service
             6ms dev-loop0.device
             6ms sys-kernel-debug.mount
             6ms snap-core-714.mount
             5ms dev-mqueue.mount
             5ms snapd.autoimport.service
             5ms systemd-remount-fs.service
             5ms pppd-dns.service
             5ms home.mount
             4ms systemd-random-seed.service
             4ms systemd-sysctl.service
             4ms boot-efi.mount
             4ms ufw.service
             3ms proc-sys-fs-binfmt_misc.mount
             3ms systemd-update-utmp-runlevel.service
             2ms rtkit-daemon.service
             2ms ureadahead-stop.service
             2ms setvtrgb.service
             1ms sys-fs-fuse-connections.mount
             1ms rc-local.service
           467us snapd.socket

```

---

### Post by Emmanuele on 2017-01-17
Is it possible that another "eating" time process is the mounting of squashfs?

Here is my blkid

> 
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="8AAA-5A3C" TYPE="vfat" PARTUUID="fa5961b1-33e0-455a-ba69-9d4680b2ba2f"
/dev/sda2: UUID="2c0b959f-1c17-4347-8e80-779c42f59029" TYPE="ext4" PARTUUID="f32a5c8d-42e6-407c-83d1-7e9cf4d0ddca"
/dev/sda3: UUID="aab32048-75c2-43ab-987f-42eb0ba47eef" TYPE="ext4" PARTUUID="caa76612-2f0c-488d-8020-c047587646de"
/dev/sdb1: LABEL="Giochi" UUID="1682DB0A82DAED6D" TYPE="ntfs" PARTUUID="0005f220-01"
/dev/sdc1: LABEL="Dati" UUID="01D05383867FFBA0" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="00009d8d-78f0-c1f4-bf53-d0011a3b0100"
/dev/sdd1: LABEL="Backup" UUID="BCF6A7DDF6A79664" TYPE="ntfs" PARTUUID="9df2ff63-dea2-40e0-a917-620ecfd06ef4"


How can I disable/uninstall such squashfs?

---

### Post by Emmanuele on 2017-01-18
Hi to all, is there any improper settings in my files?

---

