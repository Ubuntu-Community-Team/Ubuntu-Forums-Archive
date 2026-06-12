---
title: "Slow shutdown after upgrade from 16.10 to 17.04. How to find the cause?"
date: 2017-07-23
forum: General Help
---

### Post by firepol2 on 2017-07-23
Hi, a few days ago I upgraded ubuntu from 16.10 to 17.04.

The system was hanging at shutdown. By pressing Ctrl+Alt+F7 I could see in the screen a problem related to libvirt-guests. I won't go in detail about this, but I searched for this and a solution was to disable the libvirt-guests service, which I did.

Still, my system now takes about 1 minute and 30 seconds to shutdown.
After shutting it down, I press Ctrl+Alt+F7 to see the last messages on the screen and I see:

> /sbin/fsck.xfs: XFS file system.

I already booted my system with the live USB stick with ubuntu 17.04 and did a xfs_repair on my partitions, thinking that maybe there were some errors to be fixed, but when I shut down my system it still takes 1 minute and 30 seconds.

How can I determine what exactly is slowing the shutdown process?

I tried this command: ```
sudo systemd-analyze blame
``` and the output is:

>          10.297s systemd-resolved.service
          5.540s networking.service
          1.393s fwupd.service
           933ms lvm2-activation-early.service
           325ms systemd-udev-settle.service
           309ms dev-mapper-vg0\x2droot.device
           250ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
           215ms click-system-hooks.service
           200ms lvm2-activation.service
           158ms lvm2-monitor.service
           140ms upower.service
           105ms lightdm.service
           105ms plymouth-quit-wait.service
            92ms udisks2.service
            89ms smbd.service
            75ms bluetooth.service
            63ms grub-common.service
            58ms keyboard-setup.service
            54ms libvirtd.service
            52ms ddclient.service
            51ms systemd-udev-trigger.service
            46ms apparmor.service
            41ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-66f9c8a8\x2d7773\x2d4688\x2da33e\x2df7d4b91384b2.servic"]systemd-fsck@dev-disk-by\x2duuid-66f9c8a8\x2d7773\x2d4688\x2da33e\x2df7d4b91384b2.servic[/EMAIL]e
            38ms apache2.service
            37ms home.mount
            37ms systemd-sysctl.service
            34ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-66D5\x2dF1E8.servic"]systemd-fsck@dev-disk-by\x2duuid-66D5\x2dF1E8.servic[/EMAIL]e
            27ms systemd-journald.service
            27ms mnt-qwork.mount
            25ms systemd-udevd.service
            24ms systemd-modules-load.service
            23ms lm-sensors.service
            22ms boot.mount
            20ms apport.service
            19ms gpu-manager.service
            18ms data.mount
            18ms irqbalance.service
            17ms snapd.autoimport.service
            17ms nmbd.service


I also checked */var/log/syslog*, hoping to find something to help me understand what's taking ages to shutdown, without success: I can't really find in the timestamps any service that takes a huge amount of time... this stuff probably is not even logged or I have no idea where it is logged.

Can you help me to to find the cause of this slow shutdown? Thank you.

---

