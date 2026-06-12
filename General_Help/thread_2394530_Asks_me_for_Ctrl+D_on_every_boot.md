---
title: "Asks me for Ctrl+D on every boot"
date: 2018-06-18
forum: General Help
---

### Post by libcha on 2018-06-18
Hello,

I use Ubuntu 16.04.3.

When booting, it asks me to press Ctrl+D on every boot. When I press it, it continues booting normally, and the system is running fine afterwards.

I'm not really sure what shall I provide here to ease the debugging.

Bellow you can find a snippet from `journalctl -b`. Today I waited 16 minutes before pressing Ctrl+D to have the logging clear.

```
Jun 18 09:00:42 lpeltan-Latitude-5580 kernel: input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
Jun 18 09:00:42 lpeltan-Latitude-5580 kernel: input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
Jun 18 09:00:42 lpeltan-Latitude-5580 kernel: input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
Jun 18 09:00:43 lpeltan-Latitude-5580 systemd[1]: Received SIGRTMIN+20 from PID 423 (plymouthd).
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: usbcore: registered new interface driver snd-usb-audio
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: usb 2-5.2: reset SuperSpeed USB device number 3 using xhci_hcd
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: r8152 2-5.2:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr a4:4c:c8:cd:b7:24
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: ax88179_178a 1-4.6:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-4.6, ASIX AX88179 USB 3.0 Gigabit Ethernet, 80:1f:02:75:d1:44
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: usbcore: registered new interface driver ax88179_178a
Jun 18 09:00:43 lpeltan-Latitude-5580 kernel: ax88179_178a 1-4.6:1.0 enx801f0275d144: renamed from eth0
Jun 18 09:00:43 lpeltan-Latitude-5580 systemd[1]: Started ifup for enx801f0275d144.
Jun 18 09:00:43 lpeltan-Latitude-5580 systemd[1]: Found device AX88179 Gigabit Ethernet.
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: IPv6: ADDRCONF(NETDEV_UP): enx801f0275d144: link is not ready
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Waiting for firmware download to complete
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Firmware loaded in 1604608 usecs
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Waiting for device to boot
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Device booted in 11761 usecs
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-12-16.ddc
Jun 18 09:00:44 lpeltan-Latitude-5580 kernel: Bluetooth: hci0: Applying Intel DDC parameters completed
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Reached target Bluetooth.
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Started Raise network interfaces.
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Reached target Network.
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Reached target Network is Online.
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Startup finished in 4.928s (kernel) + 2.510s (userspace) = 7.439s.
Jun 18 09:00:44 lpeltan-Latitude-5580 systemd[1]: Received SIGRTMIN+21 from PID 423 (plymouthd).
Jun 18 09:00:45 lpeltan-Latitude-5580 kernel: r8152 2-5.2:1.0 eth0: v1.09.9
Jun 18 09:00:45 lpeltan-Latitude-5580 kernel: usb 2-5.2: Disable of device-initiated U1 failed.
Jun 18 09:00:45 lpeltan-Latitude-5580 kernel: usb 2-5.2: Disable of device-initiated U2 failed.
Jun 18 09:00:45 lpeltan-Latitude-5580 kernel: usb 2-5.2: reset SuperSpeed USB device number 3 using xhci_hcd
Jun 18 09:00:45 lpeltan-Latitude-5580 kernel: r8152 2-5.2:1.0 enxa44cc8cdb724: renamed from eth0
Jun 18 09:01:27 lpeltan-Latitude-5580 systemd[1]: Starting Stop ureadahead data collection...
Jun 18 09:01:27 lpeltan-Latitude-5580 systemd[1]: Stopping Read required files in advance...
Jun 18 09:01:27 lpeltan-Latitude-5580 systemd[1]: Started Stop ureadahead data collection.
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:events/fs/open_exec/enable: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:buffer_size_kb: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:tracing_on: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:resolvconf: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:.: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:1/stat: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:1/cmdline: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:2/stat: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:2/cmdline: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:3/stat: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:3/cmdline: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:4/stat: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:4/cmdline: Ignored relative path
....
(many more messages from ureadahead)
....
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:size: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:start: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:size: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:start: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:size: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:start: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:tracing_on: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:events/fs/open_exec/enable: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: ureadahead:events/fs/do_sys_open/enable: Ignored relative path
Jun 18 09:01:27 lpeltan-Latitude-5580 ureadahead[257]: Counted 4 CPUs
Jun 18 09:01:27 lpeltan-Latitude-5580 systemd[1]: Stopped Read required files in advance.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Mounting /home/lpeltan/linux_libnfc-nci...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Listening on Syslog Socket.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Started Read required files in advance.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopping Load/Save Screen Backlight Brightness of backlight:intel_backlight...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Started Braille Device Support.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopping Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped target Emergency Mode.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped target Sound Card.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped target Bluetooth.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopping Emergency Shell...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Starting Show Plymouth Boot Screen...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Mounted /home/lpeltan/linux_libnfc-nci.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped Load/Save Screen Backlight Brightness of backlight:intel_backlight.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped Emergency Shell.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Stopped Load/Save Screen Backlight Brightness of leds:dell::kbd_backlight.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Reached target Local File Systems.
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Starting Clean up any mess left by 0dns-up...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
Jun 18 09:16:57 lpeltan-Latitude-5580 systemd[1]: Started Clean up any mess left by 0dns-up.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Received SIGRTMIN+20 from PID 1238 (plymouthd).
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started Show Plymouth Boot Screen.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Reached target System Initialization.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started Daily apt download activities.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started Daily Cleanup of Temporary Directories.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started CUPS Scheduler.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Starting Socket activation for snappy daemon.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Listening on D-Bus System Message Bus Socket.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Listening on CUPS Scheduler.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started ACPI Events Check.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Listening on ACPID Listen Socket.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Started Daily apt upgrade and clean activities.
Jun 18 09:16:58 lpeltan-Latitude-5580 systemd[1]: Listening on UUID daemon activation socket.
```


My `/etc/fstab`:

```
devpts                  /dev/pts        devpts          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=666 0 0
UUID=9103a4f3-d2ec-4e49-89d7-e882992ac792 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=c2b419b1-99e1-4437-8bfc-d95cddab7363 none            swap    sw              0       0

UUID=91987fa9-14c9-4f52-8504-b185a8aa8850 /home/lpeltan/Stažené ext4 errors=remount-ro 0 0

UUID=0379bf7a-845b-4402-b008-bd36d5fc9dd1 /var/lib/lxc ext4 errors=remount-ro 0 0

/home/lpeltan/S3ECU_bare /var/lib/lxc/m3sdk/rootfs/home/user/S3ECU_bare none bind,umask=000 0 0
/home/lpeltan/lsx_ol /var/lib/lxc/m3sdk/rootfs/home/user/lsx_ol none bind,umask=000 0 0
/home/lpeltan/LSX_bare /var/lib/lxc/m3sdk/rootfs/home/user/LSX_bare none bind,umask=000 0 0

/home/lpeltan/m3sdk/rootfs/home/user/linux_libnfc-nci /home/lpeltan/linux_libnfc-nci none bind,umask=000 0 0

/home/lpeltan/s3ecu /var/lib/lxc/m3sdk/rootfs/home/user/s3ecu none bind,umask=000 0 0


/home/lpeltan/S3ECU_bare /var/lib/lxc/m3sdk_v4/rootfs/home/user/S3ECU_bare none bind,umask=000 0 0
/home/lpeltan/s3ecu /var/lib/lxc/m3sdk_v4/rootfs/home/user/s3ecu none bind,umask=000 0 0
/home/lpeltan/M3_fw /var/lib/lxc/m3sdk_v4/rootfs/home/user/M3_fw none bind,umask=000 0 0
/home/lpeltan/display /var/lib/lxc/m3sdk_v4/rootfs/home/user/display none bind,umask=000 0 0
```

---

### Post by TheFu on 2018-06-18
cntl-d usually puts a system into "maintenance mode" with a direct root login.  If that is what you are seeing, there are a number of services which aren't being started and your system, if on a network, is quite hackable.  There is an error above the cntl-d - what is it? You should fix that.

**dmesg** output should have the boot error.

---

### Post by libcha on 2018-06-18
Here the snippet of dmesg. I don't see any obvious error message.
```
[    5.987606] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    5.987633] input: HDA Intel PCH HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[    5.987660] input: HDA Intel PCH HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input20
[    6.314421] usbcore: registered new interface driver snd-usb-audio
[    6.388457] usb 2-5.2: reset SuperSpeed USB device number 3 using xhci_hcd
[    6.413861] r8152 2-5.2:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr a4:4c:c8:cd:b7:24
[    6.849700] ax88179_178a 1-4.6:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-4.6, ASIX AX88179 USB 3.0 Gigabit Ethernet, 80:1f:02:75:d1:44
[    6.849712] usbcore: registered new interface driver ax88179_178a
[    6.852736] ax88179_178a 1-4.6:1.0 enx801f0275d144: renamed from eth0
[    7.232559] IPv6: ADDRCONF(NETDEV_UP): enx801f0275d144: link is not ready
[    7.334385] Bluetooth: hci0: Waiting for firmware download to complete
[    7.334387] Bluetooth: hci0: Firmware loaded in 1604608 usecs
[    7.334435] Bluetooth: hci0: Waiting for device to boot
[    7.346451] Bluetooth: hci0: Device booted in 11761 usecs
[    7.348154] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-12-16.ddc
[    7.350451] Bluetooth: hci0: Applying Intel DDC parameters completed
[    8.381155] r8152 2-5.2:1.0 eth0: v1.09.9
[    8.384795] usb 2-5.2: Disable of device-initiated U1 failed.
[    8.388289] usb 2-5.2: Disable of device-initiated U2 failed.
[    8.716335] usb 2-5.2: reset SuperSpeed USB device number 3 using xhci_hcd
[    8.739332] r8152 2-5.2:1.0 enxa44cc8cdb724: renamed from eth0
[  981.217827] new mount options do not match the existing superblock, will be ignored
[  981.443563] vboxdrv: loading out-of-tree module taints kernel.
[  981.443706] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[  981.451185] vboxdrv: Found 4 processor cores
[  981.468218] vboxdrv: TSC mode is Invariant, tentative frequency 2807993611 Hz
[  981.468219] vboxdrv: Successfully loaded version 5.1.34_Ubuntu (interface 0x002a0000)
[  981.478826] VBoxNetFlt: Successfully started.
[  981.501504] VBoxNetAdp: Successfully started.
[  981.511109] VBoxPciLinuxInit
[  981.513898] ip_tables: (C) 2000-2006 Netfilter Core Team
[  981.519535] vboxpci: IOMMU not found (not registered)
[  981.553900] bridge: filtering via arp/ip/ip6tables is no longer available by default. Update your scripts to load br_netfilter if you need this.
[  981.557595] IPv6: ADDRCONF(NETDEV_UP): lxcbr0: link is not ready
[  981.597928] nf_conntrack version 0.5.0 (65536 buckets, 262144 max)
[  981.856813] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  982.075906] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  982.078748] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
[  982.268417] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready


```

I don't know what the "Maintenance mode" should be, but the system is running normally from my point of view. All services, networking etc.

---

### Post by TheFu on 2018-06-18
Common issues are:
* corrupt file systems
* failing disk controllers
* cable errors in connecting from the disk controller to the storage device

To figure out which of these issues is most likely, I'd use smartctl to view the smart data for each disk.  And at the next boot, I'd force fsck to run against every file system, before any mounts happen.  You can manually do it for the non-OS disks, but it is often easiest to boot from an Ubuntu Install/Live disk/flash drive and run fsck manually against each of the storage devices from a troubleshooting environment.

The SMART data will show CRC errors for cable issues, usually.
Other issues will show up as relocated sectors and a few other elements in the SMART data.  Lots of online guides exist to explain.   Just be aware that SMART is only 78% effective. Disks can and do fail about 12% of the time with nothing "bad" showing up in the SMART data.
Failing disk controllers are harder.  Moving the SATA connections around and seeing of the disk errors follow those changes is a way to troubleshoot.

---

### Post by libcha on 2018-06-26
I run `fsck -fy` on all the partitions from LiveUSB Ubuntu. It told me only some "can be narrower" hints, after i re-run it twice, i rebooted back to my system and the issue persists.

With `smatrctl -a` I can see that SMART is completely OK. Anyway, it's a Dell notebook with builtin SATA SSD.

Overall, I don't think this is a hardware issue.

Any other hints please?

---

