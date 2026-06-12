---
title: "Will a &quot;Clean-House Script&quot; clear this issue?"
date: 2022-05-18
forum: General Help
---

### Post by wyattwhiteeagle on 2022-05-18
Will a "house-cleaning script" temporarily correct these issue's until I find and apply real solutions?

Response times are taking longer and longer as days go by.

Booting up and shut down is taking longer
mouse-click detection is taking longer
applications, programs, and packages are taking longer to open

The laptop (not a server) is taking longer in general

---

### Post by #&amp;thj^% on 2022-05-18
Your longest targets are:
```

graphical.target @21.262s
cups-browsed.service @21.260s
 &#9492;&#9472;cups.service @18.169s +3.081s
      &#9492;&#9472;network.target @18.082s
NetworkManager.service @14.350s +3.728s
```
That will happen from time to time with updates and upgrades.
Can you think of any current changes by you to your system?
And  check if UN-necssary units are loading.
```
systemctl list-unit-files --state=enabled
UNIT FILE                          STATE   VENDOR PRESET
apparmor.service                   enabled disabled     
avahi-daemon.service               enabled disabled     
bluetooth.service                  enabled disabled     
expressvpn.service                 enabled disabled     
firewalld.service                  enabled disabled     
getty@.service                     enabled enabled      
libvirtd.service                   enabled disabled     
lightdm.service                    enabled disabled     
NetworkManager-dispatcher.service  enabled disabled     
NetworkManager-wait-online.service enabled disabled     
NetworkManager.service             enabled disabled     
nordvpnd.service                   enabled disabled     
power-profiles-daemon.service      enabled disabled     
systemd-timesyncd.service          enabled enabled      
avahi-daemon.socket                enabled disabled     
libvirtd-ro.socket                 enabled disabled     
libvirtd.socket                    enabled disabled     
virtlockd.socket                   enabled disabled     
virtlogd.socket                    enabled disabled     
fstrim.timer                       enabled disabled     
pamac-cleancache.timer             enabled disabled     

21 unit files listed.
lines 1-24


```
Here is brief guide:
```
 NetworkManager-wait-online.service
	

yes
	

Disable NetworkManager-wait-online.service only if you do not need working network connection available right after the boot. 
If the service is enabled, the system does not finish the boot before the network connection is working. 
This may prolong the boot time significantly.

NetworkManager.service
	

yes
	

Disable NetworkManager.service only if you do not need connection to a network. 
```
Ok I found the link to help with services: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_basic_system_settings/optimizing-systemd-to-shorten-the-boot-time_configuring-basic-system-settings](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_basic_system_settings/optimizing-systemd-to-shorten-the-boot-time_configuring-basic-system-settings)

---

### Post by ActionParsnip on 2022-05-18
Do you use a printer? If not then I can suggest you disable CUPS :o

---

### Post by wyattwhiteeagle on 2022-05-20
This isn't the way I want the system.
I still have things to do until it is the way I want it.

The following is just a start.

I've already disabled a few startup services.
The boot time seemed to improve by 17-24secs.
I used a custom script to disable those few services.
I'm not sure which services were contributing to the extended boot times.

The prolonged times was happening to more than just the system stuff.
It was also happening to other thing's too such as stacer, bleachbit, google-chrome, even things installed through Wine such as IMVU and IMVU_cache_cleaner.

For the system...startup times were extended.
For the things on my system that I use...opening times were extended
It was happening with everything, not just booting up.

In /etc/logrotate.d, I changed/added the following into the active log rotations...
```
daily
rotate 0
maxsize 10M
```

Here's what I currently have starting up...
```
11.118s logrotate.service
 9.671s accounts-daemon.service
 8.164s dev-sda3.device
 6.879s NetworkManager.service
 5.998s gpu-manager.service
 5.888s avahi-daemon.service
 5.530s systemd-resolved.service
 5.411s apt-daily-upgrade.service
 4.931s wpa_supplicant.service
 4.540s thermald.service
 4.535s systemd-logind.service
 4.105s rsyslog.service
 3.019s udisks2.service
 2.235s polkit.service
 1.801s cups.service
 1.672s ua-timer.service
 1.631s systemd-modules-load.service
 1.433s keyboard-setup.service
 1.256s systemd-udev-trigger.service
 1.154s e2scrub_reap.service
 1.050s grub-common.service
  937ms systemd-udevd.service
  863ms systemd-random-seed.service
  771ms update-notifier-download.service
  729ms grub-initrd-fallback.service
  707ms user@1000.service
  611ms upower.service
  590ms systemd-sysusers.service
  587ms systemd-sysctl.service
  568ms setvtrgb.service
  567ms systemd-rfkill.service
  539ms sddm.service
  533ms systemd-timesyncd.service
  516ms systemd-tmpfiles-setup.service
  483ms systemd-tmpfiles-setup-dev.service
  453ms swapfile.swap
  445ms systemd-journald.service
  442ms systemd-journal-flush.service
  406ms kerneloops.service
  342ms systemd-backlight@backlight:acpi_video0.service
  296ms lvm2-monitor.service
  212ms systemd-remount-fs.service
  181ms ufw.service
  177ms dev-hugepages.mount
  173ms dev-mqueue.mount
  170ms sys-kernel-debug.mount
  168ms sys-kernel-tracing.mount
  157ms kmod-static-nodes.service
  146ms modprobe@configfs.service
  145ms modprobe@drm.service
  144ms plymouth-read-write.service
  131ms modprobe@fuse.service
  118ms systemd-update-utmp.service
   82ms console-setup.service
   75ms systemd-tmpfiles-clean.service
   41ms plymouth-start.service
   36ms plymouth-quit.service
   35ms systemd-user-sessions.service
   30ms alsa-restore.service
   28ms motd-news.service
   24ms user-runtime-dir@1000.service
   18ms rtkit-daemon.service
   17ms systemd-backlight@backlight:intel_backlight.service
   12ms systemd-update-utmp-runlevel.service
    7ms sys-kernel-config.mount
    5ms sys-fs-fuse-connections.mount
  110us blk-availability.service
```

---

