---
title: "Slow Boot"
date: 2016-09-14
forum: General Help
---

### Post by mistcloud-misty on 2016-09-14
I only reboot once a week to avoid a complete system shut down (I still haven't found the cause of my laptop randomly shutting off but as long as it's rebooted every week it doesn't happen) and I've noticed the past couple times I've rebooted... I'm on the boot screen for absolutely ages. 

So I found a fancy command and it seems network manager and modem manager seem to be taking a long time... Maybe someone can help me out with speeding this up.

Just for your reference:
```
         11.323s NetworkManager.service
         10.622s apt-daily.service
         10.601s ModemManager.service
         10.578s gpu-manager.service
         10.571s accounts-daemon.service
          9.955s thermald.service
          6.847s NetworkManager-wait-online.service
          6.783s dev-sda7.device
          4.820s winbind.service
          4.802s nmbd.service
          4.629s samba-ad-dc.service
          3.329s systemd-fsck@dev-disk-by\x2duuid-9841\x2dF0DE.service
          3.190s apparmor.service
          2.371s snapd.firstboot.service
          2.220s plymouth-read-write.service
          1.740s polkitd.service
          1.663s grub-common.service
          1.472s systemd-udevd.service
          1.466s networking.service
          1.361s rsyslog.service
          1.273s keyboard-setup.service
          1.200s systemd-timesyncd.service
          1.193s systemd-tmpfiles-setup-dev.service
          1.123s plymouth-start.service
          1.000s systemd-modules-load.service
           902ms irqbalance.service
           805ms apport.service
           774ms udisks2.service
           726ms systemd-journald.service
           718ms systemd-tmpfiles-setup.service
           675ms systemd-backlight@backlight:intel_backlight.service
           664ms upower.service
           651ms ondemand.service
           640ms colord.service
           625ms systemd-logind.service
           607ms lm-sensors.service
           572ms smbd.service
           568ms pppd-dns.service
           524ms ufw.service
           492ms dev-hugepages.mount
           490ms sys-kernel-debug.mount
           486ms snapd.refresh.service
           457ms systemd-rfkill.service
           434ms speech-dispatcher.service
           422ms dev-mqueue.mount
           400ms boot-efi.mount

```

I use a USB wireless adapter because the chipset in my computer is absolute trash and frequently caused complete meltdowns no matter what driver I used. I never installed a driver for the chipset on this system so I didn't blacklist anything when usig the adapter. 

I don't really know if the other programs are in normal speeds or not...

---

### Post by ventrical on 2016-09-14
What version and DE are you running. Also .. what type of hardware/
Thanks

Regards..

---

### Post by mistcloud-misty on 2016-09-14
Sorry I thought those things in my head while typing and didn't type them...

I'm on Ubuntu 16.04. 

Hardware:
Intel i5200-U processor (also using it as graphics)
I have Nvidia Geforce940M graphics card but I don't have the driver installed because there were too many stability issues.
Built-in Wireless chip (also unused): MT7630E 
Wireless Adapter: TN-WN722N TP-Link adapter that uses AR9271 (Atheros)
8 GB Ram

---

