---
title: "Disable systemd service for bootup and re-enable after bootup"
date: 2016-10-05
forum: General Help
---

### Post by raleigh3 on 2016-10-05
Trying to speed up the time it takes for Ubuntu to start.

System boot manager shows two services which are taking 33 seconds.

```
Manages print jobs - cups
```
and
```
cups browsed
```



I would like to disable these and restart them after reboot.

FRom systemd-analyze blame
 	Quote:
```
udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2%5Cx2d5.service
udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2%5Cx2d4.service
``` 	
 
I think I need to use systemctl start the services.

 	Quote:
 	[https://access.redhat.com/documentat...Services-Start]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/sect-Managing_Services_with_systemd-Services.html#sect-Managing_Services_with_systemd-Services-Start")
 
But I can not understand how I need to use it for my case.

---

### Post by DuckHook on 2016-10-08
These forums straddle all 24 time zones. The user with knowledge of your issue may be at work or asleep, for example, when you posted. It is acceptable to bump your thread to the top of the forum every 12 hrs.

Also, for some reason, your output has been attached in a peculiar table format and changed into an email link. To avoid any such future odd behaviour:

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by DuckHook on 2016-10-08
Also, though I do not feel qualified enough with systemd dependency resolutions to help you, those who might eventually help will appreciate complete readouts rather than truncated ones. Please post the whole output from:```
systemd-analyze blame
```

---

### Post by raleigh3 on 2016-10-09
```
39.235s apt-daily.service
         21.184s udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2\x2d4.service
         19.431s mysql.service
         15.470s NetworkManager-wait-online.service
         14.235s udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb2-2\x2d5.service
         10.848s apparmor.service
         10.100s ModemManager.service
          7.793s dev-sda3.device
          7.665s tor@default.service
          5.429s NetworkManager.service
          5.292s accounts-daemon.service
          4.333s lightdm.service
          4.210s grub-common.service
          3.903s cpufreqd.service
          3.862s snapd.firstboot.service
          3.518s apport.service
          3.154s systemd-udevd.service
          3.137s networking.service
          3.093s irqbalance.service
          2.940s systemd-fsck@dev-disk-by\x2duuid-b3b0f384\x2d9e2e\x2d45f5\x2d8995\x2d932f1113f59d.service
          2.923s lm-sensors.service
          2.913s rsyslog.service
          2.906s pppd-dns.service
          2.893s gpu-manager.service
          2.869s ondemand.service
          2.634s loadcpufreq.service
          2.278s cpufrequtils.service
          2.234s systemd-fsck@dev-disk-by\x2duuid-fd00f2d7\x2dd666\x2d4614\x2d885d\x2d5ace942dd3f6.service
          2.217s colord.service
          1.667s systemd-modules-load.service
          1.476s ntp.service
          1.420s systemd-fsck@dev-disk-by\x2duuid-8adebdf0\x2d6bc3\x2d4eee\x2d8363\x2d3e9440688d42.service
          1.329s polkitd.service
          1.229s systemd-tmpfiles-setup-dev.service
          1.199s systemd-journald.service
          1.176s keyboard-setup.service
          1.164s systemd-logind.service
          1.144s snapd.refresh.service
          1.102s binfmt-support.service
          1.077s systemd-tmpfiles-setup.service
          1.074s console-setup.service
           933ms wpa_supplicant.service
           903ms plymouth-start.service
           864ms systemd-rfkill.service
           797ms resolvconf.service
           651ms sys-kernel-debug.mount
           646ms dev-mqueue.mount
           645ms dev-hugepages.mount
           464ms systemd-backlight@backlight:acpi_video0.service
           460ms systemd-sysctl.service
           415ms kmod-static-nodes.service
           371ms udisks2.service
           353ms upower.service
           350ms systemd-udev-trigger.service
           331ms media-andy-MAXTOR_SDB2.mount
           311ms systemd-update-utmp.service
           260ms media-andy-MAXTOR_SDB5.mount
           257ms speech-dispatcher.service
           251ms setvtrgb.service
           241ms systemd-user-sessions.service
           221ms systemd-journal-flush.service
           218ms ufw.service
           206ms plymouth-read-write.service
           206ms systemd-remount-fs.service
           185ms alsa-restore.service
           180ms tor.service
           134ms systemd-random-seed.service
           110ms proc-sys-fs-binfmt_misc.mount
            90ms user@1000.service
            61ms rc-local.service
            52ms media-andy-MAXTOR_SDB1.mount
            34ms snapd.socket
            28ms systemd-tmpfiles-clean.service
            27ms media-ramdisk.mount
            27ms hddtemp.service
            16ms systemd-update-utmp-runlevel.service
             9ms snapd.boot-ok.service
             6ms sys-fs-fuse-connections.mount
             5ms ureadahead-stop.service
             5ms rtkit-daemon.service
             2ms plymouth-quit-wait.service

```

---

### Post by kevdog on 2016-10-09
Do you need cups at all -- this is for printing?  It's likely searching for a printer it can't find or is configured improperly.

---

### Post by raleigh3 on 2016-10-12
Cups is used for printing.

I will disable it and see if my printers still work.

---

### Post by DuckHook on 2016-10-12
Your printers will definitely stop working if you disable cups. *kevdog* was asking you likely on the basis of seeing mysql installed. This sometimes indicates a server, and few servers are connected to printers.

If you have multiple printers installed, then do not deactivate cups. However, the second part of his question is still valid: do you have a printer defined in the OS that is not physically attached to your computer, or is not configured properly?

---

