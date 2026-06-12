---
title: "Raspberry Pi 3B+ Regression on 18.04.4 &amp; 20.04 - causing crashes"
date: 2020-06-08
forum: General Help
---

### Post by russkel on 2020-06-08
I am running a Raspberry Pi 3B+ on a robot called the Turtlebot ([https://www.robotis.us/turtlebot-3/](https://www.robotis.us/turtlebot-3/)). This is a robot which is designed to use the Robotics Operating System 2 (ROS2), and as ROS2 Foxy has been released, I am attempting to install and use it with a Focal ubuntu server setup. Everything comes together fine and installations are painless. 

The issue is when I start the ROS2 services designed to initialise the robot. It opens up the serial connections and I can see RX/TX light activity on the OpenCR board. If I open a new SSH terminal to the robot and then use a ROS2 command to show the "topics" the robot is publishing I can see the relevant topics so it does seem to be working up to this point. However if I use a ROS2 command to echo the messages to stdout, it works the first time, if I ctrl+C and then start it back up again, it will echo a few times and then it halts, and the RPi becomes non-responsive. I don't believe it is those commands directly that are doing it, but I did notice a bit of core activity with htop, and it looks like the RPi does shift clock speed up. I can repeat this over and over and the crashes occur.

RPi is connected to two USB devices:
[LIST]
[*]/dev/ttyACM0 - connects to OpenCR board. Serial interface - controls the robot and gets rosserial data in return. 
[*]/dev/ttyUSB0 - LIDAR serial interface. I have experimented by removing this and the crashes still occur. 
[/LIST]

I am using WiFi, but crashes also occur when connected via eth.

It is powered by the 5V pins from the OpenCR board, which is powered by a 3S battery.

I connected a UART to the UART0 pins to get all the kernel logging I could. The following has the boot up sequence, showing a login prompt. And then the messages succeeding that are the result of the RPi crashing.

```
MMC:   mmc@7e202000: 0, mmcnr@7e300000: 1
Loading Environment from FAT... *** Warning - bad CRC, using default environment

In:    serial
Out:   vidconsole
Err:   vidconsole
Net:   No ethernet found.
starting USB...
Bus usb@7e980000: scanning bus usb@7e980000 for devices... 6 USB Device(s) found
       scanning usb for storage devices... 0 Storage Device(s) found
## Info: input data size = 6 = 0x6
Hit any key to stop autoboot:  0 
switch to partitions #0, OK
mmc0 is current device
Scanning mmc 0:1...
Found U-Boot script /boot.scr
2603 bytes read in 6 ms (422.9 KiB/s)
## Executing script at 02400000
8378005 bytes read in 364 ms (21.9 MiB/s)
Total of 1 halfword(s) were the same
Decompressing kernel...
Uncompressed size: 25905664 = 0x18B4A00
29426757 bytes read in 1262 ms (22.2 MiB/s)
Booting Ubuntu (with booti) from mmc 0:...
## Flattened Device Tree blob at 02600000
   Booting using the fdt blob at 0x2600000
   Using Device Tree in place at 0000000002600000, end 0000000002609f2f

Starting kernel ...

[    1.966598] spi-bcm2835 3f204000.spi: could not get clk: -517
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
ext4
Thu Jan  1 00:00:07 UTC 1970
date: invalid date '          Wed Apr  1 17:23:46 2020'
-.mount
dev-mqueue.mount
sys-kernel-debug.mount
sys-kernel-tracing.mount
kmod-static-nodes.service
systemd-modules-load.service
systemd-remount-fs.service
ufw.service
sys-fs-fuse-connections.mount
sys-kernel-config.mount
systemd-sysctl.service
systemd-random-seed.service
systemd-sysusers.service
keyboard-setup.service
systemd-tmpfiles-setup-dev.service
swapfile.swap
lvm2-monitor.service
systemd-udevd.service
systemd-journald.service
systemd-udev-trigger.service
systemd-journal-flush.service
[   14.813759] brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
[   15.128676] brcmfmac: brcmf_fw_alloc_request: using brcm/brcmfmac43455-sdio for chip BCM4345/6
[   15.174878] brcmfmac: brcmf_c_preinit_dcmds: Firmware: BCM4345/6 wl0: Feb 27 2018 03:15:32 version 7.45.154 (r684107 CY) FWID 01-4fbe0b04
systemd-rfkill.service
systemd-udev-settle.service
netplan-wpa-wlan0.service
multipathd.service
[   17.840942] brcmfmac: brcmf_cfg80211_set_power_mgmt: power save enabled
systemd-fsckd.service
snap-core18-1708.mount
snap-core18-1753.mount
snap-lxd-14808.mount
snap-lxd-15066.mount
snap-snapd-7267.mount
systemd-fsck@dev-disk-by\x2dlabel-system\x2dboot.service
boot-firmware.mount
console-setup.service
         Mounting Arbitrary Executable File Formats File System...
finalrd.service
[  OK  ] Finished Tell Plymouth To Write Out Runtime Data.
[  OK  ] Mounted Arbitrary Executable File Formats File System.
proc-sys-fs-binfmt_misc.mount
[  OK  ] Finished Create Volatile Files and Directories.
systemd-tmpfiles-setup.service
         Starting Network Time Synchronization...
         Starting Update UTMP about System Boot/Shutdown...
[  OK  ] Finished Enable support for…onal executable binary formats.
binfmt-support.service
[  OK  ] Finished Update UTMP about System Boot/Shutdown.
systemd-update-utmp.service
[  OK  ] Finished Load AppArmor profiles.
apparmor.service
         Starting Load AppArmor prof… managed internally by snapd...
[  OK  ] Finished Load AppArmor prof…es managed internally by snapd.
snapd.apparmor.service
[  OK  ] Started Network Time Synchronization.
[  OK  ] Reached target System Time Set.
[  OK  ] Reached target System Time Synchronized.
systemd-timesyncd.service
[   25.080879] cloud-init[1148]: Cloud-init v. 20.1-10-g71af48df-0ubuntu5 running 'init-local' at Sun, 24 May 2020 08:15:54 +0000. Up 24.20 seconds.
[  OK  ] Finished Initial cloud-init job (pre-networking).
[  OK  ] Reached target Network (Pre).
cloud-init-local.service
         Starting Network Service...
[  OK  ] Started Network Service.
systemd-networkd.service
         Starting Wait for Network to be Configured...
         Starting Network Name Resolution...
[  OK  ] Finished Wait for Network to be Configured.
systemd-networkd-wait-online.service
         Starting Initial cloud-init…b (metadata service crawler)...
[  OK  ] Started Network Name Resolution.
[  OK  ] Reached target Host and Network Name Lookups.
systemd-resolved.service
[   29.538238] cloud-init[1170]: Cloud-init v. 20.1-10-g71af48df-0ubuntu5 running 'init' at Sun, 24 May 2020 08:15:59 +0000. Up 28.67 seconds.
[   29.538788] cloud-init[1170]: ci-info: ++++++++++++++++++++++++++++++++++++++Net device info+++++++++++++++++++++++++++++++++++++++
[   29.540670] cloud-init[1170]: ci-info: +--------+-------+----------------------------+---------------+--------+-------------------+
[   29.541896] cloud-init[1170]: ci-info: | Device |   Up  |          Address           |      Mask     | Scope  |     Hw-Address    |
[   29.543805] cloud-init[1170]: ci-info: +--------+-------+----------------------------+---------------+--------+-------------------+
[   29.545298] cloud-init[1170]: ci-info: |  eth0  | False |             .              |       .       |   .    | b8:27:eb:89:55:2a |
[   29.546816] cloud-init[1170]: ci-info: |   lo   |  True |         127.0.0.1          |   255.0.0.0   |  host  |         .         |
[   29.548589] cloud-init[1170]: ci-info: |   lo   |  True |          ::1/128           |       .       |  host  |         .         |
[   29.550684] cloud-init[1170]: ci-info: | wlan0  |  True |       192.168.1.104        | 255.255.255.0 | global | b8:27:xx:dc:xx:xx |
[   29.552179] cloud-init[1170]: ci-info: | wlan0  |  True | fe80::ba27:ebff:fedc:7f/64 |       .       |  link  | b8:27:xx:dc:xx:xx |
[   29.554004] cloud-init[1170]: ci-info: +--------+-------+----------------------------+---------------+--------+-------------------+
[   29.555532] cloud-init[1170]: ci-info: ++++++++++++++++++++++++++++++Route IPv4 info++++++++++++++++++++++++++++++
[   29.557284] cloud-init[1170]: ci-info: +-------+-------------+-------------+-----------------+-----------+-------+
[   29.558922] cloud-init[1170]: ci-info: | Route | Destination |   Gateway   |     Genmask     | Interface | Flags |
[   29.560561] cloud-init[1170]: ci-info: +-------+-------------+-------------+-----------------+-----------+-------+
[   29.562171] cloud-init[1170]: ci-info: |   0   |   0.0.0.0   | 192.168.1.1 |     0.0.0.0     |   wlan0   |   UG  |
[   29.564460] cloud-init[1170]: ci-info: |   1   | 192.168.1.0 |   0.0.0.0   |  255.255.255.0  |   wlan0   |   U   |
[   29.566004] cloud-init[1170]: ci-info: |   2   | 192.168.1.1 |   0.0.0.0   | 255.255.255.255 |   wlan0   |   UH  |
[   29.567921] cloud-init[1170]: ci-info: +-------+-------------+-------------+-----------------+-----------+-------+
[   29.569529] cloud-init[1170]: ci-info: +++++++++++++++++++Route IPv6 info+++++++++++++++++++
[   29.571384] cloud-init[1170]: ci-info: +-------+-------------+---------+-----------+-------+
[   29.573242] cloud-init[1170]: ci-info: | Route | Destination | Gateway | Interface | Flags |
[   29.575341] cloud-init[1170]: ci-info: +-------+-------------+---------+-----------+-------+
[   29.577009] cloud-init[1170]: ci-info: |   1   |  fe80::/64  |    ::   |   wlan0   |   U   |
[   29.578952] cloud-init[1170]: ci-info: |   3   |    local    |    ::   |   wlan0   |   U   |
[   29.580974] cloud-init[1170]: ci-info: |   4   |   ff00::/8  |    ::   |   wlan0   |   U   |
[   29.582773] cloud-init[1170]: ci-info: +-------+-------------+---------+-----------+-------+
[  OK  ] Finished Initial cloud-init job (metadata service crawler).
[  OK  ] Reached target Cloud-config availability.
[  OK  ] Reached target System Initialization.
cloud-init.service
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Started Periodic ext4 Onlin…data Check for All Filesystems.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Refresh fwupd metadata regularly.
[  OK  ] Started Daily rotation of log files.
[  OK  ] Started Daily man-db regeneration.
[  OK  ] Started Message of the Day.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Reached target Paths.
[  OK  ] Reached target Timers.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
[  OK  ] Listening on D-Bus System Message Bus Socket.
[  OK  ] Listening on Open-iSCSI iscsid Socket.
[  OK  ] Listening on Socket unix for snap application lxd.daemon.
         Starting Socket activation for snappy daemon.
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Reached target Sockets.
[  OK  ] Reached target Basic System.
         Starting Accounts Service...
         Starting Avahi mDNS/DNS-SD Stack...
[  OK  ] Started D-Bus System Message Bus.
dbus.service
[  OK  ] Started Save initial kernel messages after boot.
dmesg.service
         Starting Remove Stale Onlin…xt4 Metadata Check Snapshots...
[  OK  ] Started irqbalance daemon.
irqbalance.service
         Starting Dispatcher daemon for systemd-networkd...
[  OK  ] Started Set the CPU Frequency Scaling governor.
ondemand.service
         Starting System Logging Service...
         Starting Snap Daemon...
         Starting Login Service...
         Starting WPA supplicant...
[  OK  ] Finished Remove Stale Online ext4 Metadata Check Snapshots.
[  OK  ] Started System Logging Service.
rsyslog.service
[  OK  ] Started WPA supplicant.
wpa_supplicant.service
[  OK  ] Started Avahi mDNS/DNS-SD Stack.
[  OK  ] Reached target Network.
avahi-daemon.service
[  OK  ] Reached target Network is Online.
[  OK  ] Reached target Remote File Systems (Pre).
[  OK  ] Reached target Remote File Systems.
         Starting LSB: automatic crash report generation...
         Starting Deferred execution scheduler...
         Starting Availability of block devices...
[  OK  ] Started Regular background program processing daemon.
cron.service
         Starting Service for snap application lxd.activate...
         Starting OpenBSD Secure Shell server...
         Starting Permit User Sessions...
[  OK  ] Started Deferred execution scheduler.
atd.service
[  OK  ] Finished Availability of block devices.
blk-availability.service
[  OK  ] Started Login Service.
systemd-logind.service
[  OK  ] Finished Permit User Sessions.
systemd-user-sessions.service
         Starting Hold until boot process finishes up...
         Starting Terminate Plymouth Boot Screen...

Ubuntu 20.04 LTS whopper ttyS0

whopper login:

[  379.937717] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  379.946532] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  379.957445] cpufreq: __target_index: Failed to change cpu frequency: -22
[  380.993421] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  381.002224] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  381.002229] cpufreq: __target_index: Failed to change cpu frequency: -22
[  382.049419] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  382.058204] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  382.069109] cpufreq: __target_index: Failed to change cpu frequency: -22
[  383.105431] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  383.117817] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  383.132371] cpufreq: __target_index: Failed to change cpu frequency: -22
[  384.161443] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  384.173864] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  384.188390] cpufreq: __target_index: Failed to change cpu frequency: -22
[  385.217451] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  385.229839] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  385.244342] cpufreq: __target_index: Failed to change cpu frequency: -22
[  386.273448] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  386.285902] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  386.300457] cpufreq: __target_index: Failed to change cpu frequency: -22
[  387.333453] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  387.345845] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  387.360371] cpufreq: __target_index: Failed to change cpu frequency: -22
[  388.385476] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  388.397857] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  388.412356] cpufreq: __target_index: Failed to change cpu frequency: -22
[  389.445471] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  389.457865] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  389.472366] cpufreq: __target_index: Failed to change cpu frequency: -22
[  390.117438] mmc0: timeout waiting for hardware interrupt.
[  390.373441] mmc1: Timeout waiting for hardware interrupt.
[  390.380828] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  390.501480] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  390.513696] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  390.528025] cpufreq: __target_index: Failed to change cpu frequency: -22
[  391.553488] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  391.565694] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  391.580033] cpufreq: __target_index: Failed to change cpu frequency: -22
[  392.609489] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  392.621701] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  392.636036] cpufreq: __target_index: Failed to change cpu frequency: -22
[  393.665497] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  393.677717] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  393.692057] cpufreq: __target_index: Failed to change cpu frequency: -22
[  394.725504] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  394.737709] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  394.752122] cpufreq: __target_index: Failed to change cpu frequency: -22
[  395.777509] bcm2835-cpufreq:bcm2835_cpufreq_set_clock:76: Failed to set clock: 1400000 (-110)
[  395.789895] bcm2835-cpufreq:bcm2835_cpufreq_driver_target_index:176: Error occurred setting a new frequency (1400000)
[  395.804412] cpufreq: __target_index: Failed to change cpu frequency: -22
[  400.109498] rcu: INFO: rcu_sched detected stalls on CPUs/tasks:
[  400.117471] rcu:     3-...0: (0 ticks this GP) idle=3ce/1/0x4000000000000002 softirq=19876/19876 fqs=2442 
[  400.353510] mmc0: timeout waiting for hardware interrupt.
[  400.609504] mmc1: Timeout waiting for hardware interrupt.
[  400.616877] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  410.593565] mmc0: timeout waiting for hardware interrupt.
[  410.849594] mmc1: Timeout waiting for hardware interrupt.
[  410.856918] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  420.837624] mmc0: timeout waiting for hardware interrupt.
[  421.089625] mmc1: Timeout waiting for hardware interrupt.
[  421.096834] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  431.073685] mmc0: timeout waiting for hardware interrupt.
[  431.329691] mmc1: Timeout waiting for hardware interrupt.
[  431.336803] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  441.313750] mmc0: timeout waiting for hardware interrupt.
[  441.569749] mmc1: Timeout waiting for hardware interrupt.
[  441.576783] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110
[  451.553804] mmc0: timeout waiting for hardware interrupt.
[  451.809805] mmc1: Timeout waiting for hardware interrupt.
[  451.816732] brcmfmac: brcmf_sdio_htclk: HT Avail request error: -110

```

I then tried the software on 18.04.4 and exactly the same thing occurred. I reported this to the manufacturer ([https://github.com/ROBOTIS-GIT/turtlebot3/issues/593](https://github.com/ROBOTIS-GIT/turtlebot3/issues/593)) and was informed it's a known issue and it still works on 18.04.3.
I have not tried that version. But a few people seem to have confirmed this issue goes away using that particular version ([https://github.com/ROBOTIS-GIT/turtlebot3/issues/546](https://github.com/ROBOTIS-GIT/turtlebot3/issues/546)). So it's likely something that changed between .4 and .3.

Does anyone have any clues on what my next steps are?
Relevant ubuntu-bugs report: [https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/1880388](https://bugs.launchpad.net/ubuntu/+source/linux-raspi/+bug/1880388)

---

### Post by carlos-tangerino on 2020-07-13
Using the 20.04 and heavily use of /dev/ttyUSB0 (like a infinite loop using a loopback tx-rx) crashes the whole system
I don't know where to find help

---

