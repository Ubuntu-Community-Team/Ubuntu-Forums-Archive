---
title: "Slow boot due to btrfs"
date: 2022-08-12
forum: General Help
---

### Post by dorpapst on 2022-08-12
I use Ubuntu 20.04 and I decrypt my filesystem with btrfs, including a swap space. 
Weirdly, the booting process takes ages and I do not remember that it has been like that before (I didnt use the PC for a year and now updated everything).

After just 3 seconds it asks me for the password of the cryptdata and then it decrypts, but then it is stuck for 5min before I see the logscreen.
It is stuck at the message: "Begin: Running /scripts/local-premount ... Scanning for Btrfs filesystems"

Why is that taking so long?
Is there any way of making this faster?

Some information:
My /etc/default/grub looks like that:
```
GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor loglevel=3"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
GRUB_ENABLE_CRYPTODISK="y"
GRUB_DISABLE_OS_PROBER="true"
```

My /etc/fstab looks like that:
```
/dev/mapper/cryptdata /               btrfs   defaults,subvol=@,ssd,noatime,space_cache,commit=120,compress=zstd 0       0
UUID=6767-C67B  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/cryptdata /home           btrfs   defaults,subvol=@home,ssd,noatime,space_cache,commit=120,compress=zstd 0       0
/dev/mapper/cryptswap none            swap    sw              0       0
```

Is there anybody who sees something obvious slowing down the process? Otherwise the computer is extremely quick in everything, thats why I wonder.

---

### Post by mIk3_08 on 2022-08-13
> **dorpapst said:**
> 
Why is that taking so long?
Is there any way of making this faster?

Have you checked the system logs? Try to run the command below in your terminal and paste the results here in this thread. Regards and cheers.
```
sudo dmesg
```
```
cat /var/log/syslog
```

---

