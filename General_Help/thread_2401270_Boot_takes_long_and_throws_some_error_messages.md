---
title: "Boot takes long and throws some error messages"
date: 2018-09-16
forum: General Help
---

### Post by manmath on 2018-09-16
My system (Ubuntu Bionic) is working fine as of now. But it seems there's something wrong in the setup. Here are two observations:

#1 I see the boot stuck for a few seconds and throws some error messages.

> acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Failed to insert module 'autofs4': No such file or directory

Is there anything wrong. If so how to fix it, or suppress the error message.

#2 My Ubuntu Bionic system is a dualcore (pentium g620) with 8gb ddr3 memory sitting on a 1TB HDD. Boot takes ~10 seconds, shutdown is instantaneous ~2 seconds. "systemd-analyze" returns:

> Startup finished in 2.817s (kernel) + 6.554s (userspace) = 9.372s
graphical.target reached after 6.546s in userspace

As you see kernel takes quite less time to finish, but userspace takes rather long. And "systemd-analyze blame" returns:

 >           2.330s udisks2.service
          2.223s accounts-daemon.service
          2.002s networkd-dispatcher.service
          1.925s dev-sda1.device
          1.902s NetworkManager.service
          1.212s grub-common.service
          1.173s polkit.service
           798ms systemd-resolved.service
           677ms wpa_supplicant.service
           600ms alsa-restore.service
           585ms systemd-logind.service
           568ms keyboard-setup.service
           551ms systemd-fsck-root.service
           357ms systemd-journal-flush.service
           329ms systemd-tmpfiles-setup-dev.service
           305ms sys-fs-fuse-connections.mount
           281ms [email]systemd-fsck@dev-disk-by\x2duuid-c586c909\x2d4c88\x2d4da2\x2d8570\x2d21510d17804f.servic[/email]e
           267ms lightdm.service
           233ms systemd-journald.service
           229ms systemd-sysctl.service
           205ms networking.service
           205ms systemd-timesyncd.service
           197ms systemd-remount-fs.service
           157ms upower.service
           152ms setvtrgb.service
           145ms systemd-rfkill.service
           136ms plymouth-read-write.service
           120ms systemd-udevd.service
           103ms console-setup.service
            78ms home.mount
            57ms systemd-udev-trigger.service
            43ms systemd-tmpfiles-setup.service
            42ms systemd-modules-load.service
            42ms hddtemp.service
            37ms [email]user@1000.servic[/email]e
            22ms systemd-update-utmp.service
            17ms systemd-user-sessions.service
             8ms systemd-random-seed.service
             8ms ureadahead-stop.service
             6ms systemd-update-utmp-runlevel.service
             2ms plymouth-quit-wait.service

Is it normal? O is there any way to shorten boot time.?

---

