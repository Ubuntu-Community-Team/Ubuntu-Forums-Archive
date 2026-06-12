---
title: "Ubuntu dead after kernel removal"
date: 2016-02-28
forum: General Help
---

### Post by Wojciech_Marusiak on 2016-02-28
Hi, 

I am new in the forum and I would like to kindly ask you Ubuntu experts for help.

I have latest Ubuntu installed and I ran into networking problems. Basically eth0 wasn't up during boot. I was reading other threads and someone said that this is due to the last kernel 4.2.30 or something. I thought let's go back to 4.2.27. I uninstalled 4.2.30 and right after reboot I didn't have any kernel (my bad - I should have kept previous kernels - I was removing them by some fancy package which name I don't remember now).

I managed to mount lvm from live usb and I installed kernel and kernel headers. Ubuntu boots now but there are some problems:
[LIST]
[*]right after boot I can't move mouse or keyboard (they do work when live usb is booted) 
[*]network is still not working 
[/LIST]
I am attaching my syslog log.

```

Feb 28 11:30:50 ZBOX rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.12.0 try http://www.rsyslog.com/e/2222 ]
Feb 28 11:30:50 ZBOX rsyslogd: rsyslogd's groupid changed to 104
Feb 28 11:30:50 ZBOX rsyslogd: rsyslogd's userid changed to 101
Feb 28 11:30:50 ZBOX systemd-modules-load[255]: Inserted module 'lp'
Feb 28 11:30:50 ZBOX systemd-modules-load[255]: Inserted module 'ppdev'
Feb 28 11:30:50 ZBOX systemd-modules-load[255]: Inserted module 'parport_pc'
Feb 28 11:30:50 ZBOX systemd[1]: Started Create Static Device Nodes in /dev.
Feb 28 11:30:50 ZBOX systemd[1]: Starting udev Kernel Device Manager...
Feb 28 11:30:50 ZBOX lvm[265]: 2 logical volume(s) in volume group "ubuntu-vg" monitored
Feb 28 11:30:50 ZBOX systemd[1]: Started Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling.
Feb 28 11:30:50 ZBOX systemd[1]: Started udev Kernel Device Manager.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Show Plymouth Boot Screen...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Remount Root and Kernel File Systems...
Feb 28 11:30:50 ZBOX systemd[1]: Started Remount Root and Kernel File Systems.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Local File Systems (Pre).
Feb 28 11:30:50 ZBOX systemd[1]: Starting Flush Journal to Persistent Storage...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Load/Save Random Seed...
Feb 28 11:30:50 ZBOX systemd[1]: Started Show Plymouth Boot Screen.
Feb 28 11:30:50 ZBOX systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Feb 28 11:30:50 ZBOX systemd[1]: Started Flush Journal to Persistent Storage.
Feb 28 11:30:50 ZBOX systemd[1]: Started Load/Save Random Seed.
Feb 28 11:30:50 ZBOX mtp-probe: checking bus 2, device 2: "/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/usb2/2-1"
Feb 28 11:30:50 ZBOX mtp-probe: bus: 2, device: 2 was not an MTP device
Feb 28 11:30:50 ZBOX mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2"
Feb 28 11:30:50 ZBOX mtp-probe: bus: 3, device: 3 was not an MTP device
Feb 28 11:30:50 ZBOX mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.4"
Feb 28 11:30:50 ZBOX mtp-probe: bus: 3, device: 4 was not an MTP device
Feb 28 11:30:50 ZBOX systemd[1]: Found device /dev/mapper/ubuntu--vg-swap_1.
Feb 28 11:30:50 ZBOX systemd[1]: Activating swap /dev/mapper/ubuntu--vg-swap_1...
Feb 28 11:30:50 ZBOX systemd[1]: Activated swap /dev/mapper/ubuntu--vg-swap_1.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Swap.
Feb 28 11:30:50 ZBOX systemd[1]: Found device Hitachi_HTS727550A9E364 1.
Feb 28 11:30:50 ZBOX systemd[1]: Starting File System Check on /dev/disk/by-uuid/8ff08986-e2de-4d60-b854-d36f4a4ac091...
Feb 28 11:30:50 ZBOX systemd[1]: Started File System Check Daemon to report status.
Feb 28 11:30:50 ZBOX systemd[1]: Created slice system-lvm2\x2dpvscan.slice.
Feb 28 11:30:50 ZBOX systemd[1]: Starting LVM2 PV scan on device 8:5...
Feb 28 11:30:50 ZBOX lvm[381]: 2 logical volume(s) in volume group "ubuntu-vg" now active
Feb 28 11:30:50 ZBOX systemd[1]: Started LVM2 PV scan on device 8:5.
Feb 28 11:30:50 ZBOX systemd-fsck[373]: /dev/sda1 was not cleanly unmounted, check forced.
Feb 28 11:30:50 ZBOX systemd-fsck[373]: /dev/sda1: 304/62248 files (16.4% non-contiguous), 41807/248832 blocks
Feb 28 11:30:50 ZBOX systemd[1]: Started File System Check on /dev/disk/by-uuid/8ff08986-e2de-4d60-b854-d36f4a4ac091.
Feb 28 11:30:50 ZBOX systemd[1]: Mounting /boot...
Feb 28 11:30:50 ZBOX systemd[1]: Mounted /boot.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Local File Systems.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Create Volatile Files and Directories...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Remote File Systems.
Feb 28 11:30:50 ZBOX systemd-tmpfiles[393]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Clean up any mess left by 0dns-up...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...
Feb 28 11:30:50 ZBOX systemd[1]: Starting netfilter persistent configuration...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Set console keymap...
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: AppArmor initialization...
Feb 28 11:30:50 ZBOX systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
Feb 28 11:30:50 ZBOX sh[396]: Segmentation fault
Feb 28 11:30:50 ZBOX systemd[1]: Started Clean up any mess left by 0dns-up.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Nameserver information manager...
Feb 28 11:30:50 ZBOX loadkeys[399]: Loading /etc/console-setup/cached.kmap.gz
Feb 28 11:30:50 ZBOX systemd[1]: Started Set console keymap.
Feb 28 11:30:50 ZBOX systemd[1]: Started Nameserver information manager.
Feb 28 11:30:50 ZBOX netfilter-persistent[398]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start
Feb 28 11:30:50 ZBOX netfilter-persistent[398]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start
Feb 28 11:30:50 ZBOX netfilter-persistent[398]: Warning: skipping IPv6 (no rules to load)
Feb 28 11:30:50 ZBOX systemd[1]: Started netfilter persistent configuration.
Feb 28 11:30:50 ZBOX systemd[1]: Started Create Volatile Files and Directories.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Update UTMP about System Boot/Shutdown...
Feb 28 11:30:50 ZBOX systemd[1]: Reached target System Time Synchronized.
Feb 28 11:30:50 ZBOX sh[396]: Segmentation fault
Feb 28 11:30:50 ZBOX systemd[1]: Started Update UTMP about System Boot/Shutdown.
Feb 28 11:30:50 ZBOX apparmor[400]: * Starting AppArmor profiles
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modprobe.d/blacklist_linux_4.2.0-25-generic.conf: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modprobe.d/blacklist_linux_4.2.0-30-generic.conf: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/arch/x86/kvm/kvm-intel.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/arch/x86/kvm/kvm.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/char/lp.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/modules.dep.bin: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/modules.alias.bin: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/modules.softdep: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/modules.symbols.bin: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/modules.builtin.bin: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/char/ppdev.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/parport/parport_pc.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/input/input-leds.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/arch/x86/crypto/ghash-clmulni-intel.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/arch/x86/crypto/crc32-pclmul.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/arch/x86/crypto/crct10dif-pclmul.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/soundcore.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/seq/snd-seq-device.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/seq/snd-seq.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/snd-timer.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/snd.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/input/serio/serio_raw.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/crypto/cryptd.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/snd-rawmidi.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/seq/snd-seq-midi-event.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/seq/snd-seq-midi.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/snd-hwdep.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/core/snd-pcm.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/input/joydev.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/macintosh/mac_hid.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/mfd/lpc_ich.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/tty/serial/8250/8250_fintek.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/pci/hotplug/shpchp.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/hda/snd-hda-core.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/pci/hda/snd-hda-intel.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-generic.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/hwmon/coretemp.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/powercap/intel_rapl.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/memstick/core/memstick.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/memstick/host/rtsx_usb_ms.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/thermal/intel_powerclamp.ko: No such file or directory
Feb 28 11:30:50 ZBOX ureadahead[262]: ureadahead:/lib/modules/4.2.0-30-generic/kernel/drivers/thermal/x86_pkg_temp_thermal.ko: No such file or directory
Feb 28 11:30:50 ZBOX sh[396]: Segmentation fault
Feb 28 11:30:50 ZBOX sh[396]: message repeated 9 times: [ Segmentation fault]
Feb 28 11:30:50 ZBOX apparmor[400]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Feb 28 11:30:50 ZBOX apparmor[400]: ...done.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: AppArmor initialization.
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: Raise network interfaces....
Feb 28 11:30:50 ZBOX networking[522]: * Configuring network interfaces...
Feb 28 11:30:50 ZBOX dhclient: Internet Systems Consortium DHCP Client 4.3.1
Feb 28 11:30:50 ZBOX dhclient: Copyright 2004-2014 Internet Systems Consortium.
Feb 28 11:30:50 ZBOX dhclient: All rights reserved.
Feb 28 11:30:50 ZBOX dhclient: For info, please visit https://www.isc.org/software/dhcp/
Feb 28 11:30:50 ZBOX dhclient: 
Feb 28 11:30:50 ZBOX networking[522]: Internet Systems Consortium DHCP Client 4.3.1
Feb 28 11:30:50 ZBOX networking[522]: Copyright 2004-2014 Internet Systems Consortium.
Feb 28 11:30:50 ZBOX networking[522]: All rights reserved.
Feb 28 11:30:50 ZBOX networking[522]: For info, please visit https://www.isc.org/software/dhcp/
Feb 28 11:30:50 ZBOX networking[522]: Cannot find device "eth0"
Feb 28 11:30:50 ZBOX dhclient: Error getting hardware address for "eth0": No such device
Feb 28 11:30:50 ZBOX dhclient: 
Feb 28 11:30:50 ZBOX dhclient: If you think you have received this message due to a bug rather
Feb 28 11:30:50 ZBOX dhclient: than a configuration issue please read the section on submitting
Feb 28 11:30:50 ZBOX dhclient: bugs on either our web page at www.isc.org or in the README file
Feb 28 11:30:50 ZBOX dhclient: before submitting a bug.  These pages explain the proper
Feb 28 11:30:50 ZBOX dhclient: process and the information we find helpful for debugging..
Feb 28 11:30:50 ZBOX dhclient: 
Feb 28 11:30:50 ZBOX dhclient: exiting.
Feb 28 11:30:50 ZBOX networking[522]: Error getting hardware address for "eth0": No such device
Feb 28 11:30:50 ZBOX networking[522]: If you think you have received this message due to a bug rather
Feb 28 11:30:50 ZBOX networking[522]: than a configuration issue please read the section on submitting
Feb 28 11:30:50 ZBOX networking[522]: bugs on either our web page at www.isc.org or in the README file
Feb 28 11:30:50 ZBOX networking[522]: before submitting a bug.  These pages explain the proper
Feb 28 11:30:50 ZBOX networking[522]: process and the information we find helpful for debugging..
Feb 28 11:30:50 ZBOX networking[522]: exiting.
Feb 28 11:30:50 ZBOX networking[522]: Failed to bring up eth0.
Feb 28 11:30:50 ZBOX networking[522]: ...done.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: Raise network interfaces..
Feb 28 11:30:50 ZBOX systemd[1]: Reached target System Initialization.
Feb 28 11:30:50 ZBOX systemd[1]: Started CUPS Scheduler.
Feb 28 11:30:50 ZBOX systemd[1]: Listening on CUPS Scheduler.
Feb 28 11:30:50 ZBOX systemd[1]: Listening on UUID daemon activation socket.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Restore Sound Card State...
Feb 28 11:30:50 ZBOX systemd[1]: Listening on ACPID Listen Socket.
Feb 28 11:30:50 ZBOX systemd[1]: Listening on D-Bus System Message Bus Socket.
Feb 28 11:30:50 ZBOX systemd[1]: Started Daily Cleanup of Temporary Directories.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Timers.
Feb 28 11:30:50 ZBOX systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Sockets.
Feb 28 11:30:50 ZBOX systemd[1]: Started Trigger resolvconf update for networkd DNS.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Paths.
Feb 28 11:30:50 ZBOX systemd[1]: Reached target Basic System.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Feb 28 11:30:50 ZBOX systemd[1]: Started D-Bus System Message Bus.
Feb 28 11:30:50 ZBOX alsactl[632]: /usr/sbin/alsactl: load_state:1735: No soundcards found...
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Successfully dropped root privileges.
Feb 28 11:30:50 ZBOX avahi-daemon[633]: avahi-daemon 0.6.31 starting up.
Feb 28 11:30:50 ZBOX dbus[634]: [system] AppArmor D-Bus mediation is enabled
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Successfully called chroot().
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Successfully dropped remaining capabilities.
Feb 28 11:30:50 ZBOX systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Feb 28 11:30:50 ZBOX cron[659]: (CRON) INFO (pidfile fd = 3)
Feb 28 11:30:50 ZBOX systemd[1]: Started Regular background program processing daemon.
Feb 28 11:30:50 ZBOX systemd[1]: Started crash report submission daemon.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Modem Manager...
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: automatic crash report generation...
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: Speech Dispatcher...
Feb 28 11:30:50 ZBOX avahi-daemon[633]: No service file found in /etc/avahi/services.
Feb 28 11:30:50 ZBOX systemd[1]: Starting System Logging Service...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Permit User Sessions...
Feb 28 11:30:50 ZBOX speech-dispatcher[663]: * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Feb 28 11:30:50 ZBOX systemd[1]: Started Deferred execution scheduler.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Detect the available GPUs and deal with any system changes...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Accounts Service...
Feb 28 11:30:50 ZBOX systemd[1]: Starting Login Service...
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: daemon to balance interrupts for SMP systems...
Feb 28 11:30:50 ZBOX systemd[1]: Started CUPS Scheduler.
Feb 28 11:30:50 ZBOX apport[662]: * Starting automatic crash report generation: apport
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: Start or stop the inetd daemon....
Feb 28 11:30:50 ZBOX systemd[1]: Starting Thermal Daemon Service...
Feb 28 11:30:50 ZBOX systemd[1]: Started Make remote CUPS printers available locally.
Feb 28 11:30:50 ZBOX systemd[1]: Starting Network Manager...
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: Start the GNUstep distributed object mapper...
Feb 28 11:30:50 ZBOX openbsd-inetd[681]: * Starting internet superserver inetd
Feb 28 11:30:50 ZBOX systemd[1]: Started Run anacron jobs.
Feb 28 11:30:50 ZBOX irqbalance[677]: * Starting SMP IRQ Balancer: irqbalance
Feb 28 11:30:50 ZBOX systemd[1]: Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down....
Feb 28 11:30:50 ZBOX systemd[1]: Started Wait for all "auto" /etc/network/interfaces to be up for network-online.target.
Feb 28 11:30:50 ZBOX systemd[1]: Started Restore Sound Card State.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: Speech Dispatcher.
Feb 28 11:30:50 ZBOX systemd[1]: Started Permit User Sessions.
Feb 28 11:30:50 ZBOX anacron[697]: Anacron 2.3 started on 2016-02-28
Feb 28 11:30:50 ZBOX gdomap[692]: * GNUstep distributed object mapper disabled, see /etc/default/gdomap
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: Start the GNUstep distributed object mapper.
Feb 28 11:30:50 ZBOX systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down..
Feb 28 11:30:50 ZBOX apport[662]: ...done.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: automatic crash report generation.
Feb 28 11:30:50 ZBOX systemd[1]: Stopped LSB: Start NTP daemon.
Feb 28 11:30:50 ZBOX systemd[1]: Started Login Service.
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Network interface enumeration completed.
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Registering HINFO record with values 'X86_64'/'LINUX'.
Feb 28 11:30:50 ZBOX avahi-daemon[633]: Server startup complete. Host name is ZBOX.local. Local service cookie is 3990891944.
Feb 28 11:30:50 ZBOX cron[659]: (CRON) INFO (Running @reboot jobs)
Feb 28 11:30:50 ZBOX anacron[697]: Normal exit (0 jobs run)
Feb 28 11:30:50 ZBOX irqbalance[677]: ...done.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: daemon to balance interrupts for SMP systems.
Feb 28 11:30:50 ZBOX systemd[1]: Started System Logging Service.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Initializing cgroup subsys cpuacct
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Linux version 4.2.0-27-generic (buildd@lgw01-12) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 (Ubuntu 4.2.0-27.32-generic 4.2.8-ckt1)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.2.0-27-generic root=UUID=6f743047-b6f4-4f71-b3f2-e63354a4a897 ro quiet splash vt.handoff=7
Feb 28 11:30:50 ZBOX kernel: [    0.000000] KERNEL supported cpus:
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   Intel GenuineIntel
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   AMD AuthenticAMD
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   Centaur CentaurHauls
Feb 28 11:30:50 ZBOX kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
Feb 28 11:30:50 ZBOX kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
Feb 28 11:30:50 ZBOX kernel: [    0.000000] x86/fpu: Enabled xstate features 0x3, context size is 0x240 bytes, using 'standard' format.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] x86/fpu: Using 'eager' FPU context switches.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000006e982fff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000006e983000-0x000000006e9c5fff] ACPI NVS
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000006e9c6000-0x000000006f0b6fff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000006f0b7000-0x000000006f2ccfff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000006f2cd000-0x000000007e315fff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007e316000-0x000000007e615fff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007e616000-0x000000007e740fff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007e741000-0x000000007ea5efff] ACPI NVS
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007ea5f000-0x000000007effefff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007efff000-0x000000007effffff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x000000007f000000-0x00000000bf9fffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023f5fffff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 28 11:30:50 ZBOX kernel: [    0.000000] SMBIOS 2.7 present.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] DMI: ZOTAC ZBOX-ID18/ZBOX-ID18, BIOS B211P010 01/24/2014
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: last_pfn = 0x23f600 max_arch_pfn = 0x400000000
Feb 28 11:30:50 ZBOX kernel: [    0.000000] MTRR default type: uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   00000-9FFFF write-back
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   C0000-DBFFF write-protect
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DC000-E7FFF uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   E8000-FFFFF write-protect
Feb 28 11:30:50 ZBOX kernel: [    0.000000] MTRR variable ranges enabled:
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   1 base 200000000 mask FC0000000 write-back
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   2 base 080000000 mask F80000000 uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   3 base 07F800000 mask FFF800000 uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   4 base 23F800000 mask FFF800000 uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   5 base 23F600000 mask FFFE00000 uncachable
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   6 disabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   7 disabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   8 disabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   9 disabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Feb 28 11:30:50 ZBOX kernel: [    0.000000] original variable MTRRs
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 1, base: 8GB, range: 1GB, type WB
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 2, base: 2GB, range: 2GB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 3, base: 2040MB, range: 8MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 4, base: 9208MB, range: 8MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 5, base: 9206MB, range: 2MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] total RAM covered: 7150M
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Found optimal setting for mtrr clean up
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 6      lose cover RAM: 0G
Feb 28 11:30:50 ZBOX kernel: [    0.000000] New variable MTRRs
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 1, base: 2040MB, range: 8MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 2, base: 4GB, range: 4GB, type WB
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 3, base: 8GB, range: 1GB, type WB
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 4, base: 9206MB, range: 2MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] reg 5, base: 9208MB, range: 8MB, type UC
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: update [mem 0x7f800000-0xffffffff] usable ==> reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: last_pfn = 0x7f000 max_arch_pfn = 0x400000000
Feb 28 11:30:50 ZBOX kernel: [    0.000000] found SMP MP-table at [mem 0x000fd720-0x000fd72f] mapped at [ffff8800000fd720]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Scanning 1 areas for low memory corruption
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x23f400000-0x23f5fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x23f400000-0x23f5fffff] page 2M
Feb 28 11:30:50 ZBOX rsyslogd-2039: Could not open output pipe '/dev/xconsole':: Permission denied [v8.12.0 try http://www.rsyslog.com/e/2039 ]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x220000000-0x23f3fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x220000000-0x23f3fffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x21fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x200000000-0x21fffffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x40000000-0x40003fff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x40005000-0x6e982fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x40005000-0x401fffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x40200000-0x6e7fffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6e800000-0x6e982fff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x6e9c6000-0x6f0b6fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6e9c6000-0x6e9fffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6ea00000-0x6effffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6f000000-0x6f0b6fff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x6f2cd000-0x7e315fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6f2cd000-0x6f3fffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x6f400000-0x7e1fffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x7e200000-0x7e315fff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x7e616000-0x7e740fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x7e616000-0x7e740fff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x7efff000-0x7effffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x7efff000-0x7effffff] page 4k
Feb 28 11:30:50 ZBOX kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Feb 28 11:30:50 ZBOX rsyslogd-2007: action 'action 10' suspended, next retry is Sun Feb 28 11:31:20 2016 [v8.12.0 try http://www.rsyslog.com/e/2007 ]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
Feb 28 11:30:50 ZBOX kernel: [    0.000000] RAMDISK: [mem 0x36776000-0x373b2fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: Early table checksum verification disabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: RSDP 0x00000000000F0490 000024 (v02 ALASKA)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: XSDT 0x000000007E7C3070 000064 (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: FACP 0x000000007E7CC990 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: DSDT 0x000000007E7C3170 00981C (v02 ALASKA A M I    00000027 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: FACS 0x000000007EA5D080 000040
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: APIC 0x000000007E7CCAA0 000062 (v03 ALASKA A M I    01072009 AMI  00010013)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: FPDT 0x000000007E7CCB08 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: MCFG 0x000000007E7CCB50 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: HPET 0x000000007E7CCB90 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: SSDT 0x000000007E7CCBC8 000315 (v01 SataRe SataTabl 00001000 INTL 20091112)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: SSDT 0x000000007E7CCEE0 00079A (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: SSDT 0x000000007E7CD680 000B22 (v01 PmRef  CpuPm    00003000 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 28 11:30:50 ZBOX kernel: [    0.000000] No NUMA configuration found
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023f5fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x23f5f1000-0x23f5f5fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237c00000-ffff88023ebfffff] on node 0
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Zone ranges:
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   Normal   [mem 0x0000000100000000-0x000000023f5fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Movable zone start for each node
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Early memory node ranges
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x0000000020200000-0x0000000040003fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x0000000040005000-0x000000006e982fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x000000006e9c6000-0x000000006f0b6fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x000000006f2cd000-0x000000007e315fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x000000007e616000-0x000000007e740fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x000000007efff000-0x000000007effffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   node   0: [mem 0x0000000100000000-0x000000023f5fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000023f5fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] On node 0 totalpages: 1824132
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA zone: 21 pages reserved
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA32 zone: 8000 pages used for memmap
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   DMA32 zone: 511976 pages, LIFO batch:31
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   Normal zone: 20440 pages used for memmap
Feb 28 11:30:50 ZBOX kernel: [    0.000000]   Normal zone: 1308160 pages, LIFO batch:31
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Reserving Intel graphics stolen memory at 0x7fa00000-0xa19fffff
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Feb 28 11:30:50 ZBOX kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 28 11:30:50 ZBOX kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Feb 28 11:30:50 ZBOX kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x6e983000-0x6e9c5fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x6f0b7000-0x6f2ccfff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7e316000-0x7e615fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7e741000-0x7ea5efff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7ea5f000-0x7effefff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0x7f000000-0xbf9fffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbfa00000-0xf7ffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.000000] e820: [mem 0xbfa00000-0xf7ffffff] available for PCI devices
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 28 11:30:50 ZBOX kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Feb 28 11:30:50 ZBOX kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88023f200000 s96728 r8192 d30248 u1048576
Feb 28 11:30:50 ZBOX kernel: [    0.000000] pcpu-alloc: s96728 r8192 d30248 u1048576 alloc=1*2097152
Feb 28 11:30:50 ZBOX kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1795607
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Policy zone: Normal
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-4.2.0-27-generic root=UUID=6f743047-b6f4-4f71-b3f2-e63354a4a897 ro quiet splash vt.handoff=7
Feb 28 11:30:50 ZBOX kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Memory: 7086252K/7296528K available (8154K kernel code, 1238K rwdata, 3804K rodata, 1460K init, 1292K bss, 210276K reserved, 0K cma-reserved)
Feb 28 11:30:50 ZBOX kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Hierarchical RCU implementation.
Feb 28 11:30:50 ZBOX kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Feb 28 11:30:50 ZBOX kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=2
Feb 28 11:30:50 ZBOX kernel: [    0.000000] NR_IRQS:16640 nr_irqs:440 16
Feb 28 11:30:50 ZBOX kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Feb 28 11:30:50 ZBOX kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-1.
Feb 28 11:30:50 ZBOX kernel: [    0.000000] vt handoff: transparent VT on vt#7
Feb 28 11:30:50 ZBOX kernel: [    0.000000] Console: colour dummy device 80x25
Feb 28 11:30:50 ZBOX kernel: [    0.000000] console [tty0] enabled
Feb 28 11:30:50 ZBOX kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
Feb 28 11:30:50 ZBOX kernel: [    0.000000] hpet clockevent registered
Feb 28 11:30:50 ZBOX kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Feb 28 11:30:50 ZBOX kernel: [    0.000000] tsc: Detected 1496.661 MHz processor
Feb 28 11:30:50 ZBOX kernel: [    0.000053] Calibrating delay loop (skipped), value calculated using timer frequency.. 2993.32 BogoMIPS (lpj=5986644)
Feb 28 11:30:50 ZBOX kernel: [    0.000057] pid_max: default: 32768 minimum: 301
Feb 28 11:30:50 ZBOX kernel: [    0.000064] ACPI: Core revision 20150619
Feb 28 11:30:50 ZBOX kernel: [    0.010384] ACPI: All ACPI Tables successfully acquired
Feb 28 11:30:50 ZBOX kernel: [    0.010412] Security Framework initialized
Feb 28 11:30:50 ZBOX kernel: [    0.010423] AppArmor: AppArmor initialized
Feb 28 11:30:50 ZBOX kernel: [    0.010425] Yama: becoming mindful.
Feb 28 11:30:50 ZBOX kernel: [    0.011240] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.014482] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.015967] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.015982] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.016272] Initializing cgroup subsys blkio
Feb 28 11:30:50 ZBOX kernel: [    0.016276] Initializing cgroup subsys memory
Feb 28 11:30:50 ZBOX kernel: [    0.016286] Initializing cgroup subsys devices
Feb 28 11:30:50 ZBOX kernel: [    0.016289] Initializing cgroup subsys freezer
Feb 28 11:30:50 ZBOX kernel: [    0.016292] Initializing cgroup subsys net_cls
Feb 28 11:30:50 ZBOX kernel: [    0.016295] Initializing cgroup subsys perf_event
Feb 28 11:30:50 ZBOX kernel: [    0.016298] Initializing cgroup subsys net_prio
Feb 28 11:30:50 ZBOX kernel: [    0.016300] Initializing cgroup subsys hugetlb
Feb 28 11:30:50 ZBOX kernel: [    0.016331] CPU: Physical Processor ID: 0
Feb 28 11:30:50 ZBOX kernel: [    0.016333] CPU: Processor Core ID: 0
Feb 28 11:30:50 ZBOX kernel: [    0.016339] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Feb 28 11:30:50 ZBOX kernel: [    0.016341] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Feb 28 11:30:50 ZBOX kernel: [    0.016345] mce: CPU supports 7 MCE banks
Feb 28 11:30:50 ZBOX kernel: [    0.016361] CPU0: Thermal monitoring enabled (TM1)
Feb 28 11:30:50 ZBOX kernel: [    0.016370] process: using mwait in idle threads
Feb 28 11:30:50 ZBOX kernel: [    0.016374] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Feb 28 11:30:50 ZBOX kernel: [    0.016376] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
Feb 28 11:30:50 ZBOX kernel: [    0.017028] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
Feb 28 11:30:50 ZBOX kernel: [    0.023271] ftrace: allocating 30933 entries in 121 pages
Feb 28 11:30:50 ZBOX kernel: [    0.045501] x2apic: IRQ remapping doesn't support X2APIC mode
Feb 28 11:30:50 ZBOX kernel: [    0.045980] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 28 11:30:50 ZBOX kernel: [    0.085660] TSC deadline timer enabled
Feb 28 11:30:50 ZBOX kernel: [    0.085665] smpboot: CPU0: Intel(R) Celeron(R) CPU 1007U @ 1.50GHz (fam: 06, model: 3a, stepping: 09)
Feb 28 11:30:50 ZBOX kernel: [    0.085701] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
Feb 28 11:30:50 ZBOX kernel: [    0.085732] ... version:                3
Feb 28 11:30:50 ZBOX kernel: [    0.085733] ... bit width:              48
Feb 28 11:30:50 ZBOX kernel: [    0.085735] ... generic registers:      8
Feb 28 11:30:50 ZBOX kernel: [    0.085736] ... value mask:             0000ffffffffffff
Feb 28 11:30:50 ZBOX kernel: [    0.085737] ... max period:             0000ffffffffffff
Feb 28 11:30:50 ZBOX kernel: [    0.085739] ... fixed-purpose events:   3
Feb 28 11:30:50 ZBOX kernel: [    0.085740] ... event mask:             00000007000000ff
Feb 28 11:30:50 ZBOX kernel: [    0.086924] x86: Booting SMP configuration:
Feb 28 11:30:50 ZBOX kernel: [    0.086926] .... node  #0, CPUs:      #1
Feb 28 11:30:50 ZBOX kernel: [    0.090091] x86: Booted up 1 node, 2 CPUs
Feb 28 11:30:50 ZBOX kernel: [    0.090095] smpboot: Total of 2 processors activated (5986.64 BogoMIPS)
Feb 28 11:30:50 ZBOX kernel: [    0.090145] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Feb 28 11:30:50 ZBOX kernel: [    0.092015] devtmpfs: initialized
Feb 28 11:30:50 ZBOX kernel: [    0.096961] evm: security.selinux
Feb 28 11:30:50 ZBOX kernel: [    0.096964] evm: security.SMACK64
Feb 28 11:30:50 ZBOX kernel: [    0.096965] evm: security.SMACK64EXEC
Feb 28 11:30:50 ZBOX kernel: [    0.096966] evm: security.SMACK64TRANSMUTE
Feb 28 11:30:50 ZBOX kernel: [    0.096968] evm: security.SMACK64MMAP
Feb 28 11:30:50 ZBOX kernel: [    0.096969] evm: security.ima
Feb 28 11:30:50 ZBOX kernel: [    0.096970] evm: security.capability
Feb 28 11:30:50 ZBOX kernel: [    0.097065] PM: Registering ACPI NVS region [mem 0x6e983000-0x6e9c5fff] (274432 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.097073] PM: Registering ACPI NVS region [mem 0x7e741000-0x7ea5efff] (3268608 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.097227] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Feb 28 11:30:50 ZBOX kernel: [    0.097332] pinctrl core: initialized pinctrl subsystem
Feb 28 11:30:50 ZBOX kernel: [    0.097492] RTC time: 10:30:19, date: 02/28/16
Feb 28 11:30:50 ZBOX kernel: [    0.097641] NET: Registered protocol family 16
Feb 28 11:30:50 ZBOX kernel: [    0.102092] cpuidle: using governor ladder
Feb 28 11:30:50 ZBOX kernel: [    0.106092] cpuidle: using governor menu
Feb 28 11:30:50 ZBOX kernel: [    0.106195] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Feb 28 11:30:50 ZBOX kernel: [    0.106197] ACPI: bus type PCI registered
Feb 28 11:30:50 ZBOX kernel: [    0.106199] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb 28 11:30:50 ZBOX kernel: [    0.106296] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Feb 28 11:30:50 ZBOX kernel: [    0.106300] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Feb 28 11:30:50 ZBOX kernel: [    0.106313] PCI: Using configuration type 1 for base access
Feb 28 11:30:50 ZBOX kernel: [    0.106665] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Feb 28 11:30:50 ZBOX kernel: [    0.106681] perf_event_intel: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off
Feb 28 11:30:50 ZBOX kernel: [    0.114587] ACPI: Added _OSI(Module Device)
Feb 28 11:30:50 ZBOX kernel: [    0.114589] ACPI: Added _OSI(Processor Device)
Feb 28 11:30:50 ZBOX kernel: [    0.114591] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 28 11:30:50 ZBOX kernel: [    0.114593] ACPI: Added _OSI(Processor Aggregator Device)
Feb 28 11:30:50 ZBOX kernel: [    0.118660] ACPI: Executed 1 blocks of module-level executable AML code
Feb 28 11:30:50 ZBOX kernel: [    0.122372] ACPI: Dynamic OEM Table Load:
Feb 28 11:30:50 ZBOX kernel: [    0.122383] ACPI: SSDT 0xFFFF880236AFD000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.123156] ACPI: Dynamic OEM Table Load:
Feb 28 11:30:50 ZBOX kernel: [    0.123163] ACPI: SSDT 0xFFFF880236410000 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.123821] ACPI: Dynamic OEM Table Load:
Feb 28 11:30:50 ZBOX kernel: [    0.123825] ACPI: SSDT 0xFFFF880236BEC600 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
Feb 28 11:30:50 ZBOX kernel: [    0.124677] ACPI: Interpreter enabled
Feb 28 11:30:50 ZBOX kernel: [    0.124685] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
Feb 28 11:30:50 ZBOX kernel: [    0.124692] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
Feb 28 11:30:50 ZBOX kernel: [    0.124712] ACPI: (supports S0 S3 S4 S5)
Feb 28 11:30:50 ZBOX kernel: [    0.124714] ACPI: Using IOAPIC for interrupt routing
Feb 28 11:30:50 ZBOX kernel: [    0.124752] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 28 11:30:50 ZBOX kernel: [    0.133751] ACPI: Power Resource [FN00] (off)
Feb 28 11:30:50 ZBOX kernel: [    0.133874] ACPI: Power Resource [FN01] (off)
Feb 28 11:30:50 ZBOX kernel: [    0.133991] ACPI: Power Resource [FN02] (off)
Feb 28 11:30:50 ZBOX kernel: [    0.134114] ACPI: Power Resource [FN03] (off)
Feb 28 11:30:50 ZBOX kernel: [    0.134231] ACPI: Power Resource [FN04] (off)
Feb 28 11:30:50 ZBOX kernel: [    0.135059] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Feb 28 11:30:50 ZBOX kernel: [    0.135067] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Feb 28 11:30:50 ZBOX kernel: [    0.135376] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
Feb 28 11:30:50 ZBOX kernel: [    0.135560] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
Feb 28 11:30:50 ZBOX kernel: [    0.135562] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
Feb 28 11:30:50 ZBOX kernel: [    0.136209] PCI host bridge to bus 0000:00
Feb 28 11:30:50 ZBOX kernel: [    0.136214] pci_bus 0000:00: root bus resource [bus 00-3e]
Feb 28 11:30:50 ZBOX kernel: [    0.136217] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Feb 28 11:30:50 ZBOX kernel: [    0.136219] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136222] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136224] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136227] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136229] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136232] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfeafffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.136242] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
Feb 28 11:30:50 ZBOX kernel: [    0.136374] pci 0000:00:02.0: [8086:0156] type 00 class 0x030000
Feb 28 11:30:50 ZBOX kernel: [    0.136394] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
Feb 28 11:30:50 ZBOX kernel: [    0.136403] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xdfffffff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.136409] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Feb 28 11:30:50 ZBOX kernel: [    0.136606] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Feb 28 11:30:50 ZBOX kernel: [    0.136650] pci 0000:00:1a.0: reg 0x10: [mem 0xf7d08000-0xf7d083ff]
Feb 28 11:30:50 ZBOX kernel: [    0.136758] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.136840] pci 0000:00:1a.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.136902] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Feb 28 11:30:50 ZBOX kernel: [    0.136947] pci 0000:00:1b.0: reg 0x10: [mem 0xf7d00000-0xf7d03fff 64bit]
Feb 28 11:30:50 ZBOX kernel: [    0.137044] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.137110] pci 0000:00:1b.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.137168] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Feb 28 11:30:50 ZBOX kernel: [    0.137280] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.137347] pci 0000:00:1c.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.137401] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
Feb 28 11:30:50 ZBOX kernel: [    0.137506] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.137575] pci 0000:00:1c.1: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.137630] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
Feb 28 11:30:50 ZBOX kernel: [    0.137737] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.137804] pci 0000:00:1c.2: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.137870] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Feb 28 11:30:50 ZBOX kernel: [    0.137912] pci 0000:00:1d.0: reg 0x10: [mem 0xf7d07000-0xf7d073ff]
Feb 28 11:30:50 ZBOX kernel: [    0.138017] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.138103] pci 0000:00:1d.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.138161] pci 0000:00:1f.0: [8086:1e5f] type 00 class 0x060100
Feb 28 11:30:50 ZBOX kernel: [    0.138403] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
Feb 28 11:30:50 ZBOX kernel: [    0.138449] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Feb 28 11:30:50 ZBOX kernel: [    0.138464] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Feb 28 11:30:50 ZBOX kernel: [    0.138479] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Feb 28 11:30:50 ZBOX kernel: [    0.138493] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Feb 28 11:30:50 ZBOX kernel: [    0.138507] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Feb 28 11:30:50 ZBOX kernel: [    0.138521] pci 0000:00:1f.2: reg 0x24: [mem 0xf7d06000-0xf7d067ff]
Feb 28 11:30:50 ZBOX kernel: [    0.138566] pci 0000:00:1f.2: PME# supported from D3hot
Feb 28 11:30:50 ZBOX kernel: [    0.138677] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Feb 28 11:30:50 ZBOX kernel: [    0.138706] pci 0000:00:1f.3: reg 0x10: [mem 0xf7d05000-0xf7d050ff 64bit]
Feb 28 11:30:50 ZBOX kernel: [    0.138743] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Feb 28 11:30:50 ZBOX kernel: [    0.138945] pci 0000:00:1c.0: PCI bridge to [bus 01]
Feb 28 11:30:50 ZBOX kernel: [    0.139058] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Feb 28 11:30:50 ZBOX kernel: [    0.139119] pci 0000:02:00.0: reg 0x10: [io  0xe000-0xe0ff]
Feb 28 11:30:50 ZBOX kernel: [    0.139164] pci 0000:02:00.0: reg 0x18: [mem 0xe0004000-0xe0004fff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.139192] pci 0000:02:00.0: reg 0x20: [mem 0xe0000000-0xe0003fff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.139288] pci 0000:02:00.0: supports D1 D2
Feb 28 11:30:50 ZBOX kernel: [    0.139290] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.139332] pci 0000:02:00.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.146145] pci 0000:00:1c.1: PCI bridge to [bus 02]
Feb 28 11:30:50 ZBOX kernel: [    0.146150] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Feb 28 11:30:50 ZBOX kernel: [    0.146163] pci 0000:00:1c.1:   bridge window [mem 0xe0000000-0xe00fffff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.146268] pci 0000:03:00.0: [1912:0015] type 00 class 0x0c0330
Feb 28 11:30:50 ZBOX kernel: [    0.146335] pci 0000:03:00.0: reg 0x10: [mem 0xf7c00000-0xf7c01fff 64bit]
Feb 28 11:30:50 ZBOX kernel: [    0.146485] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Feb 28 11:30:50 ZBOX kernel: [    0.146522] pci 0000:03:00.0: System wakeup disabled by ACPI
Feb 28 11:30:50 ZBOX kernel: [    0.154144] pci 0000:00:1c.2: PCI bridge to [bus 03]
Feb 28 11:30:50 ZBOX kernel: [    0.154152] pci 0000:00:1c.2:   bridge window [mem 0xf7c00000-0xf7cfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.154803] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.154873] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.154941] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.155008] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.155074] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Feb 28 11:30:50 ZBOX kernel: [    0.155140] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Feb 28 11:30:50 ZBOX kernel: [    0.155208] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.155275] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
Feb 28 11:30:50 ZBOX kernel: [    0.155621] ACPI: Enabled 6 GPEs in block 00 to 3F
Feb 28 11:30:50 ZBOX kernel: [    0.155791] vgaarb: setting as boot device: PCI:0000:00:02.0
Feb 28 11:30:50 ZBOX kernel: [    0.155794] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Feb 28 11:30:50 ZBOX kernel: [    0.155798] vgaarb: loaded
Feb 28 11:30:50 ZBOX kernel: [    0.155799] vgaarb: bridge control possible 0000:00:02.0
Feb 28 11:30:50 ZBOX kernel: [    0.156129] SCSI subsystem initialized
Feb 28 11:30:50 ZBOX kernel: [    0.156190] libata version 3.00 loaded.
Feb 28 11:30:50 ZBOX kernel: [    0.156226] ACPI: bus type USB registered
Feb 28 11:30:50 ZBOX kernel: [    0.156251] usbcore: registered new interface driver usbfs
Feb 28 11:30:50 ZBOX kernel: [    0.156263] usbcore: registered new interface driver hub
Feb 28 11:30:50 ZBOX kernel: [    0.156281] usbcore: registered new device driver usb
Feb 28 11:30:50 ZBOX kernel: [    0.156501] PCI: Using ACPI for IRQ routing
Feb 28 11:30:50 ZBOX kernel: [    0.158441] PCI: pci_cache_line_size set to 64 bytes
Feb 28 11:30:50 ZBOX kernel: [    0.158503] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158506] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158507] e820: reserve RAM buffer [mem 0x6e983000-0x6fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158509] e820: reserve RAM buffer [mem 0x6f0b7000-0x6fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158511] e820: reserve RAM buffer [mem 0x7e316000-0x7fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158513] e820: reserve RAM buffer [mem 0x7e741000-0x7fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158516] e820: reserve RAM buffer [mem 0x7f000000-0x7fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158518] e820: reserve RAM buffer [mem 0x23f600000-0x23fffffff]
Feb 28 11:30:50 ZBOX kernel: [    0.158683] NetLabel: Initializing
Feb 28 11:30:50 ZBOX kernel: [    0.158684] NetLabel:  domain hash size = 128
Feb 28 11:30:50 ZBOX kernel: [    0.158686] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 28 11:30:50 ZBOX kernel: [    0.158704] NetLabel:  unlabeled traffic allowed by default
Feb 28 11:30:50 ZBOX kernel: [    0.158813] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Feb 28 11:30:50 ZBOX kernel: [    0.158821] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Feb 28 11:30:50 ZBOX kernel: [    0.160852] clocksource: Switched to clocksource hpet
Feb 28 11:30:50 ZBOX kernel: [    0.169232] AppArmor: AppArmor Filesystem Enabled
Feb 28 11:30:50 ZBOX kernel: [    0.169328] pnp: PnP ACPI init
Feb 28 11:30:50 ZBOX kernel: [    0.169464] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169471] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.169575] system 00:01: [io  0x0680-0x069f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169579] system 00:01: [io  0x1000-0x100f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169581] system 00:01: [io  0xffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169584] system 00:01: [io  0xffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169587] system 00:01: [io  0x0400-0x0453] could not be reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169590] system 00:01: [io  0x0458-0x047f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169592] system 00:01: [io  0x0500-0x057f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169595] system 00:01: [io  0x164e-0x164f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169599] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.169636] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.169703] system 00:03: [io  0x0454-0x0457] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169708] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.169852] system 00:04: [io  0x0a00-0x0a1f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169855] system 00:04: [io  0x0a30-0x0a3f] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169859] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.169970] system 00:05: [io  0x04d0-0x04d1] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.169974] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.170272] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170275] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170278] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170281] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170283] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170286] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170289] system 00:06: [mem 0xfed90000-0xfed93fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170291] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170294] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170297] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170300] system 00:06: [mem 0xbfa00000-0xbfa00fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170304] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.170500] system 00:07: [mem 0x20000000-0x201fffff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170504] system 00:07: [mem 0x40004000-0x40004fff] has been reserved
Feb 28 11:30:50 ZBOX kernel: [    0.170508] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 28 11:30:50 ZBOX kernel: [    0.170534] pnp: PnP ACPI: found 8 devices
Feb 28 11:30:50 ZBOX kernel: [    0.177608] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Feb 28 11:30:50 ZBOX kernel: [    0.177657] pci 0000:00:1c.0: PCI bridge to [bus 01]
Feb 28 11:30:50 ZBOX kernel: [    0.177678] pci 0000:00:1c.1: PCI bridge to [bus 02]
Feb 28 11:30:50 ZBOX kernel: [    0.177683] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
Feb 28 11:30:50 ZBOX kernel: [    0.177695] pci 0000:00:1c.1:   bridge window [mem 0xe0000000-0xe00fffff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.177706] pci 0000:00:1c.2: PCI bridge to [bus 03]
Feb 28 11:30:50 ZBOX kernel: [    0.177713] pci 0000:00:1c.2:   bridge window [mem 0xf7c00000-0xf7cfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.177729] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
Feb 28 11:30:50 ZBOX kernel: [    0.177731] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177734] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177737] pci_bus 0000:00: resource 7 [mem 0x000dc000-0x000dffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177739] pci_bus 0000:00: resource 8 [mem 0x000e0000-0x000e3fff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177742] pci_bus 0000:00: resource 9 [mem 0x000e4000-0x000e7fff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177744] pci_bus 0000:00: resource 10 [mem 0xbfa00000-0xfeafffff window]
Feb 28 11:30:50 ZBOX kernel: [    0.177747] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Feb 28 11:30:50 ZBOX kernel: [    0.177750] pci_bus 0000:02: resource 2 [mem 0xe0000000-0xe00fffff 64bit pref]
Feb 28 11:30:50 ZBOX kernel: [    0.177753] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
Feb 28 11:30:50 ZBOX kernel: [    0.177797] NET: Registered protocol family 2
Feb 28 11:30:50 ZBOX kernel: [    0.178016] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.178240] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.178399] TCP: Hash tables configured (established 65536 bind 65536)
Feb 28 11:30:50 ZBOX kernel: [    0.178446] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.178491] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.178580] NET: Registered protocol family 1
Feb 28 11:30:50 ZBOX kernel: [    0.178604] pci 0000:00:02.0: Video device with shadowed ROM
Feb 28 11:30:50 ZBOX kernel: [    0.216982] PCI: CLS mismatch (64 != 32), using 64 bytes
Feb 28 11:30:50 ZBOX kernel: [    0.217265] Trying to unpack rootfs image as initramfs...
Feb 28 11:30:50 ZBOX kernel: [    0.534685] Freeing initrd memory: 12532K (ffff880036776000 - ffff8800373b3000)
Feb 28 11:30:50 ZBOX kernel: [    0.534713] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 28 11:30:50 ZBOX kernel: [    0.534716] software IO TLB [mem 0x7a316000-0x7e316000] (64MB) mapped at [ffff88007a316000-ffff88007e315fff]
Feb 28 11:30:50 ZBOX kernel: [    0.534825] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
Feb 28 11:30:50 ZBOX kernel: [    0.534827] hw unit of domain pp0-core 2^-16 Joules
Feb 28 11:30:50 ZBOX kernel: [    0.534829] hw unit of domain package 2^-16 Joules
Feb 28 11:30:50 ZBOX kernel: [    0.534830] hw unit of domain pp1-gpu 2^-16 Joules
Feb 28 11:30:50 ZBOX kernel: [    0.534979] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x16
Feb 28 11:30:50 ZBOX kernel: [    0.534989] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x16
Feb 28 11:30:50 ZBOX kernel: [    0.535061] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Feb 28 11:30:50 ZBOX kernel: [    0.535183] Scanning for low memory corruption every 60 seconds
Feb 28 11:30:50 ZBOX kernel: [    0.535616] futex hash table entries: 512 (order: 3, 32768 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.535635] Initialise system trusted keyring
Feb 28 11:30:50 ZBOX kernel: [    0.535669] audit: initializing netlink subsys (disabled)
Feb 28 11:30:50 ZBOX kernel: [    0.535687] audit: type=2000 audit(1456655419.524:1): initialized
Feb 28 11:30:50 ZBOX kernel: [    0.536252] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 28 11:30:50 ZBOX kernel: [    0.538413] zpool: loaded
Feb 28 11:30:50 ZBOX kernel: [    0.538416] zbud: loaded
Feb 28 11:30:50 ZBOX kernel: [    0.538679] VFS: Disk quotas dquot_6.6.0
Feb 28 11:30:50 ZBOX kernel: [    0.538734] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 28 11:30:50 ZBOX kernel: [    0.539410] fuse init (API version 7.23)
Feb 28 11:30:50 ZBOX kernel: [    0.539614] Key type big_key registered
Feb 28 11:30:50 ZBOX kernel: [    0.540002] Key type asymmetric registered
Feb 28 11:30:50 ZBOX kernel: [    0.540007] Asymmetric key parser 'x509' registered
Feb 28 11:30:50 ZBOX kernel: [    0.540028] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Feb 28 11:30:50 ZBOX kernel: [    0.540068] io scheduler noop registered
Feb 28 11:30:50 ZBOX kernel: [    0.540072] io scheduler deadline registered (default)
Feb 28 11:30:50 ZBOX kernel: [    0.540118] io scheduler cfq registered
Feb 28 11:30:50 ZBOX kernel: [    0.540675] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 28 11:30:50 ZBOX kernel: [    0.540686] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 28 11:30:50 ZBOX kernel: [    0.540746] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
Feb 28 11:30:50 ZBOX kernel: [    0.540747] vesafb: scrolling: redraw
Feb 28 11:30:50 ZBOX kernel: [    0.540750] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Feb 28 11:30:50 ZBOX kernel: [    0.540768] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90001000000, using 8128k, total 8128k
Feb 28 11:30:50 ZBOX kernel: [    0.540921] Console: switching to colour frame buffer device 240x67
Feb 28 11:30:50 ZBOX kernel: [    0.540965] fb0: VESA VGA frame buffer device
Feb 28 11:30:50 ZBOX kernel: [    0.540993] intel_idle: MWAIT substates: 0x21120
Feb 28 11:30:50 ZBOX kernel: [    0.540995] intel_idle: v0.4 model 0x3A
Feb 28 11:30:50 ZBOX kernel: [    0.540997] intel_idle: lapic_timer_reliable_states 0xffffffff
Feb 28 11:30:50 ZBOX kernel: [    0.541209] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 28 11:30:50 ZBOX kernel: [    0.541214] ACPI: Power Button [PWRB]
Feb 28 11:30:50 ZBOX kernel: [    0.541269] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 28 11:30:50 ZBOX kernel: [    0.541272] ACPI: Power Button [PWRF]
Feb 28 11:30:50 ZBOX kernel: [    0.542299] thermal LNXTHERM:00: registered as thermal_zone0
Feb 28 11:30:50 ZBOX kernel: [    0.542302] ACPI: Thermal Zone [TZ00] (28 C)
Feb 28 11:30:50 ZBOX kernel: [    0.542594] thermal LNXTHERM:01: registered as thermal_zone1
Feb 28 11:30:50 ZBOX kernel: [    0.542596] ACPI: Thermal Zone [TZ01] (30 C)
Feb 28 11:30:50 ZBOX kernel: [    0.542661] GHES: HEST is not enabled!
Feb 28 11:30:50 ZBOX kernel: [    0.542792] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Feb 28 11:30:50 ZBOX kernel: [    0.545159] Linux agpgart interface v0.103
Feb 28 11:30:50 ZBOX kernel: [    0.548062] brd: module loaded
Feb 28 11:30:50 ZBOX kernel: [    0.549252] loop: module loaded
Feb 28 11:30:50 ZBOX kernel: [    0.549528] libphy: Fixed MDIO Bus: probed
Feb 28 11:30:50 ZBOX kernel: [    0.549533] tun: Universal TUN/TAP device driver, 1.6
Feb 28 11:30:50 ZBOX kernel: [    0.549534] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 28 11:30:50 ZBOX kernel: [    0.549605] PPP generic driver version 2.4.2
Feb 28 11:30:50 ZBOX kernel: [    0.549813] xhci_hcd 0000:03:00.0: xHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.549821] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 1
Feb 28 11:30:50 ZBOX kernel: [    0.660687] xhci_hcd 0000:03:00.0: hcc params 0x014051cf hci version 0x100 quirks 0x00000090
Feb 28 11:30:50 ZBOX kernel: [    0.660892] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb 28 11:30:50 ZBOX kernel: [    0.660895] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 28 11:30:50 ZBOX kernel: [    0.660898] usb usb1: Product: xHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.660900] usb usb1: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
Feb 28 11:30:50 ZBOX kernel: [    0.660902] usb usb1: SerialNumber: 0000:03:00.0
Feb 28 11:30:50 ZBOX kernel: [    0.661085] hub 1-0:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    0.661099] hub 1-0:1.0: 2 ports detected
Feb 28 11:30:50 ZBOX kernel: [    0.661221] xhci_hcd 0000:03:00.0: xHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.661226] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 2
Feb 28 11:30:50 ZBOX kernel: [    0.664207] usb usb2: We don't know the algorithms for LPM for this host, disabling LPM.
Feb 28 11:30:50 ZBOX kernel: [    0.664250] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Feb 28 11:30:50 ZBOX kernel: [    0.664252] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 28 11:30:50 ZBOX kernel: [    0.664254] usb usb2: Product: xHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.664257] usb usb2: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
Feb 28 11:30:50 ZBOX kernel: [    0.664259] usb usb2: SerialNumber: 0000:03:00.0
Feb 28 11:30:50 ZBOX kernel: [    0.664428] hub 2-0:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    0.664442] hub 2-0:1.0: 2 ports detected
Feb 28 11:30:50 ZBOX kernel: [    0.664572] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 28 11:30:50 ZBOX kernel: [    0.664581] ehci-pci: EHCI PCI platform driver
Feb 28 11:30:50 ZBOX kernel: [    0.664738] ehci-pci 0000:00:1a.0: EHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.664746] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
Feb 28 11:30:50 ZBOX kernel: [    0.664762] ehci-pci 0000:00:1a.0: debug port 2
Feb 28 11:30:50 ZBOX kernel: [    0.668660] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
Feb 28 11:30:50 ZBOX kernel: [    0.668674] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7d08000
Feb 28 11:30:50 ZBOX kernel: [    0.680718] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Feb 28 11:30:50 ZBOX kernel: [    0.680774] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Feb 28 11:30:50 ZBOX kernel: [    0.680776] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 28 11:30:50 ZBOX kernel: [    0.680779] usb usb3: Product: EHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.680781] usb usb3: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
Feb 28 11:30:50 ZBOX kernel: [    0.680783] usb usb3: SerialNumber: 0000:00:1a.0
Feb 28 11:30:50 ZBOX kernel: [    0.681001] hub 3-0:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    0.681013] hub 3-0:1.0: 2 ports detected
Feb 28 11:30:50 ZBOX kernel: [    0.681330] ehci-pci 0000:00:1d.0: EHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.681339] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
Feb 28 11:30:50 ZBOX kernel: [    0.681355] ehci-pci 0000:00:1d.0: debug port 2
Feb 28 11:30:50 ZBOX kernel: [    0.685257] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Feb 28 11:30:50 ZBOX kernel: [    0.685273] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7d07000
Feb 28 11:30:50 ZBOX kernel: [    0.696775] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Feb 28 11:30:50 ZBOX kernel: [    0.696868] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
Feb 28 11:30:50 ZBOX kernel: [    0.696872] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 28 11:30:50 ZBOX kernel: [    0.696874] usb usb4: Product: EHCI Host Controller
Feb 28 11:30:50 ZBOX kernel: [    0.696877] usb usb4: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
Feb 28 11:30:50 ZBOX kernel: [    0.696879] usb usb4: SerialNumber: 0000:00:1d.0
Feb 28 11:30:50 ZBOX kernel: [    0.697176] hub 4-0:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    0.697191] hub 4-0:1.0: 2 ports detected
Feb 28 11:30:50 ZBOX kernel: [    0.697436] ehci-platform: EHCI generic platform driver
Feb 28 11:30:50 ZBOX kernel: [    0.697459] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 28 11:30:50 ZBOX kernel: [    0.697471] ohci-pci: OHCI PCI platform driver
Feb 28 11:30:50 ZBOX kernel: [    0.697491] ohci-platform: OHCI generic platform driver
Feb 28 11:30:50 ZBOX kernel: [    0.697506] uhci_hcd: USB Universal Host Controller Interface driver
Feb 28 11:30:50 ZBOX kernel: [    0.697598] i8042: PNP: No PS/2 controller found. Probing ports directly.
Feb 28 11:30:50 ZBOX kernel: [    0.700124] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 28 11:30:50 ZBOX kernel: [    0.700135] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 28 11:30:50 ZBOX kernel: [    0.700454] mousedev: PS/2 mouse device common for all mice
Feb 28 11:30:50 ZBOX kernel: [    0.700655] rtc_cmos 00:02: RTC can wake from S4
Feb 28 11:30:50 ZBOX kernel: [    0.700864] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Feb 28 11:30:50 ZBOX kernel: [    0.700898] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Feb 28 11:30:50 ZBOX kernel: [    0.700912] i2c /dev entries driver
Feb 28 11:30:50 ZBOX kernel: [    0.701024] device-mapper: uevent: version 1.0.3
Feb 28 11:30:50 ZBOX kernel: [    0.701122] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
Feb 28 11:30:50 ZBOX kernel: [    0.701151] Intel P-state driver initializing.
Feb 28 11:30:50 ZBOX kernel: [    0.701293] ledtrig-cpu: registered to indicate activity on CPUs
Feb 28 11:30:50 ZBOX kernel: [    0.701582] PCCT header not found.
Feb 28 11:30:50 ZBOX kernel: [    0.702173] NET: Registered protocol family 10
Feb 28 11:30:50 ZBOX kernel: [    0.702579] NET: Registered protocol family 17
Feb 28 11:30:50 ZBOX kernel: [    0.702614] Key type dns_resolver registered
Feb 28 11:30:50 ZBOX kernel: [    0.703500] Loading compiled-in X.509 certificates
Feb 28 11:30:50 ZBOX kernel: [    0.706126] Loaded X.509 cert 'Build time autogenerated kernel key: 9421ce78f7dd6932d7a71d3bab89bb036afa29eb'
Feb 28 11:30:50 ZBOX kernel: [    0.706165] registered taskstats version 1
Feb 28 11:30:50 ZBOX kernel: [    0.706222] zswap: loading zswap
Feb 28 11:30:50 ZBOX kernel: [    0.706228] zswap: using zbud pool
Feb 28 11:30:50 ZBOX kernel: [    0.706239] zswap: using lzo compressor
Feb 28 11:30:50 ZBOX kernel: [    0.710253] Key type trusted registered
Feb 28 11:30:50 ZBOX kernel: [    0.715267] Key type encrypted registered
Feb 28 11:30:50 ZBOX kernel: [    0.715278] AppArmor: AppArmor sha1 policy hashing enabled
Feb 28 11:30:50 ZBOX kernel: [    0.715283] ima: No TPM chip found, activating TPM-bypass!
Feb 28 11:30:50 ZBOX kernel: [    0.715315] evm: HMAC attrs: 0x1
Feb 28 11:30:50 ZBOX kernel: [    0.715707]   Magic number: 4:616:528
Feb 28 11:30:50 ZBOX kernel: [    0.715827] rtc_cmos 00:02: setting system clock to 2016-02-28 10:30:19 UTC (1456655419)
Feb 28 11:30:50 ZBOX kernel: [    0.715910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 28 11:30:50 ZBOX kernel: [    0.715912] EDD information not available.
Feb 28 11:30:50 ZBOX kernel: [    0.716047] PM: Hibernation image not present or could not be loaded.
Feb 28 11:30:50 ZBOX kernel: [    0.716487] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
Feb 28 11:30:50 ZBOX kernel: [    0.716489] Write protecting the kernel read-only data: 12288k
Feb 28 11:30:50 ZBOX kernel: [    0.716697] Freeing unused kernel memory: 24K (ffff8800017fa000 - ffff880001800000)
Feb 28 11:30:50 ZBOX kernel: [    0.716812] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
Feb 28 11:30:50 ZBOX kernel: [    0.735890] random: systemd-udevd urandom read with 1 bits of entropy available
Feb 28 11:30:50 ZBOX kernel: [    0.813361] ahci 0000:00:1f.2: version 3.0
Feb 28 11:30:50 ZBOX kernel: [    0.813587] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
Feb 28 11:30:50 ZBOX kernel: [    0.828693] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
Feb 28 11:30:50 ZBOX kernel: [    0.828700] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part ems sxs apst 
Feb 28 11:30:50 ZBOX kernel: [    0.840946] scsi host0: ahci
Feb 28 11:30:50 ZBOX kernel: [    0.843681] scsi host1: ahci
Feb 28 11:30:50 ZBOX kernel: [    0.844674] scsi host2: ahci
Feb 28 11:30:50 ZBOX kernel: [    0.847495] scsi host3: ahci
Feb 28 11:30:50 ZBOX kernel: [    0.851497] scsi host4: ahci
Feb 28 11:30:50 ZBOX kernel: [    0.851581] ata1: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06100 irq 27
Feb 28 11:30:50 ZBOX kernel: [    0.851584] ata2: DUMMY
Feb 28 11:30:50 ZBOX kernel: [    0.851586] ata3: DUMMY
Feb 28 11:30:50 ZBOX kernel: [    0.851587] ata4: DUMMY
Feb 28 11:30:50 ZBOX kernel: [    0.851591] ata5: SATA max UDMA/133 abar m2048@0xf7d06000 port 0xf7d06300 irq 27
Feb 28 11:30:50 ZBOX kernel: [    0.973269] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
Feb 28 11:30:50 ZBOX kernel: [    0.993180] usb 2-1: New USB device found, idVendor=2537, idProduct=1066
Feb 28 11:30:50 ZBOX kernel: [    0.993186] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 28 11:30:50 ZBOX kernel: [    0.993189] usb 2-1: Product: NS1066
Feb 28 11:30:50 ZBOX kernel: [    0.993192] usb 2-1: Manufacturer: Norelsys
Feb 28 11:30:50 ZBOX kernel: [    0.993194] usb 2-1: SerialNumber: 0123456789ABCDE
Feb 28 11:30:50 ZBOX kernel: [    0.996639] usb 3-1: new high-speed USB device number 2 using ehci-pci
Feb 28 11:30:50 ZBOX kernel: [    1.008682] usb 4-1: new high-speed USB device number 2 using ehci-pci
Feb 28 11:30:50 ZBOX kernel: [    1.129289] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
Feb 28 11:30:50 ZBOX kernel: [    1.129295] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 28 11:30:50 ZBOX kernel: [    1.129703] hub 3-1:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    1.129856] hub 3-1:1.0: 4 ports detected
Feb 28 11:30:50 ZBOX kernel: [    1.141293] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
Feb 28 11:30:50 ZBOX kernel: [    1.141299] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 28 11:30:50 ZBOX kernel: [    1.141700] hub 4-1:1.0: USB hub found
Feb 28 11:30:50 ZBOX kernel: [    1.141852] hub 4-1:1.0: 4 ports detected
Feb 28 11:30:50 ZBOX kernel: [    1.168638] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 28 11:30:50 ZBOX kernel: [    1.169565] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
Feb 28 11:30:50 ZBOX kernel: [    1.169576] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802378b7ca8), AE_NOT_FOUND (20150619/psparse-536)
Feb 28 11:30:50 ZBOX kernel: [    1.169988] ata1.00: ATA-8: Hitachi HTS727550A9E364, JF3OA100, max UDMA/133
Feb 28 11:30:50 ZBOX kernel: [    1.169993] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Feb 28 11:30:50 ZBOX kernel: [    1.189493] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
Feb 28 11:30:50 ZBOX kernel: [    1.189504] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802378b7ca8), AE_NOT_FOUND (20150619/psparse-536)
Feb 28 11:30:50 ZBOX kernel: [    1.189945] ata1.00: configured for UDMA/133
Feb 28 11:30:50 ZBOX kernel: [    1.190226] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72755 A100 PQ: 0 ANSI: 5
Feb 28 11:30:50 ZBOX kernel: [    1.190753] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb 28 11:30:50 ZBOX kernel: [    1.190759] sd 0:0:0:0: [sda] 4096-byte physical blocks
Feb 28 11:30:50 ZBOX kernel: [    1.190823] sd 0:0:0:0: [sda] Write Protect is off
Feb 28 11:30:50 ZBOX kernel: [    1.190827] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 28 11:30:50 ZBOX kernel: [    1.190855] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 28 11:30:50 ZBOX kernel: [    1.191054] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 28 11:30:50 ZBOX kernel: [    1.228794]  sda: sda1 sda2 < sda5 >
Feb 28 11:30:50 ZBOX kernel: [    1.229568] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 28 11:30:50 ZBOX kernel: [    1.400552] usb 3-1.2: new full-speed USB device number 3 using ehci-pci
Feb 28 11:30:50 ZBOX kernel: [    1.496771] usb 3-1.2: New USB device found, idVendor=046d, idProduct=c52b
Feb 28 11:30:50 ZBOX kernel: [    1.496777] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Feb 28 11:30:50 ZBOX kernel: [    1.496780] usb 3-1.2: Product: USB Receiver
Feb 28 11:30:50 ZBOX kernel: [    1.496783] usb 3-1.2: Manufacturer: Logitech
Feb 28 11:30:50 ZBOX kernel: [    1.508507] ata5: SATA link down (SStatus 0 SControl 300)
Feb 28 11:30:50 ZBOX kernel: [    1.532480] tsc: Refined TSC clocksource calibration: 1496.602 MHz
Feb 28 11:30:50 ZBOX kernel: [    1.532487] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x159298a4d16, max_idle_ns: 440795254665 ns
Feb 28 11:30:50 ZBOX kernel: [    1.568504] usb 3-1.4: new high-speed USB device number 4 using ehci-pci
Feb 28 11:30:50 ZBOX kernel: [    1.661369] usb 3-1.4: New USB device found, idVendor=0bda, idProduct=0129
Feb 28 11:30:50 ZBOX kernel: [    1.661376] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 28 11:30:50 ZBOX kernel: [    1.661379] usb 3-1.4: Product: USB2.0-CRW
Feb 28 11:30:50 ZBOX kernel: [    1.661382] usb 3-1.4: Manufacturer: Generic
Feb 28 11:30:50 ZBOX kernel: [    1.661384] usb 3-1.4: SerialNumber: 20100201396000000
Feb 28 11:30:50 ZBOX kernel: [    2.532377] clocksource: Switched to clocksource tsc
Feb 28 11:30:50 ZBOX kernel: [    3.819135] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Feb 28 11:30:50 ZBOX kernel: [    4.318783] random: nonblocking pool is initialized
Feb 28 11:30:50 ZBOX kernel: [    9.539452] lp: driver loaded but no devices found
Feb 28 11:30:50 ZBOX kernel: [    9.553040] ppdev: user-space parallel port driver
Feb 28 11:30:50 ZBOX kernel: [   14.053759] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Feb 28 11:30:50 ZBOX kernel: [   15.413847] kvm: disabled by bios
Feb 28 11:30:50 ZBOX kernel: [   15.433415] kvm: disabled by bios
Feb 28 11:30:50 ZBOX kernel: [   15.647617] Adding 1789948k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:1789948k FS
Feb 28 11:30:50 ZBOX kernel: [   18.804648] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
Feb 28 11:30:50 ZBOX kernel: [   18.809302] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
Feb 28 11:30:50 ZBOX kernel: [   18.967347] ifquery[409]: segfault at 0 ip 00007fad6eb01327 sp 00007fff126d8a88 error 4 in libc-2.21.so[7fad6e9bc000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   19.969455] ifquery[437]: segfault at 0 ip 00007f2628c96327 sp 00007fff51485dc8 error 4 in libc-2.21.so[7f2628b51000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   20.971371] ifquery[496]: segfault at 0 ip 00007f92642a9327 sp 00007ffe69b8b928 error 4 in libc-2.21.so[7f9264164000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   21.973264] ifquery[498]: segfault at 0 ip 00007f7a96c22327 sp 00007ffcc51a1ab8 error 4 in libc-2.21.so[7f7a96add000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   22.975144] ifquery[500]: segfault at 0 ip 00007fc068786327 sp 00007ffdaed7d458 error 4 in libc-2.21.so[7fc068641000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   23.977115] ifquery[502]: segfault at 0 ip 00007f4f705ed327 sp 00007ffd03c8c038 error 4 in libc-2.21.so[7f4f704a8000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   24.979017] ifquery[504]: segfault at 0 ip 00007f8aa6612327 sp 00007ffda08e52b8 error 4 in libc-2.21.so[7f8aa64cd000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   25.981053] ifquery[506]: segfault at 0 ip 00007f7bbde4d327 sp 00007ffc7ef25e48 error 4 in libc-2.21.so[7f7bbdd08000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   26.982976] ifquery[508]: segfault at 0 ip 00007f57e7ef7327 sp 00007ffe9660ee18 error 4 in libc-2.21.so[7f57e7db2000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   27.736284] audit: type=1400 audit(1456655446.525:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX kernel: [   27.736296] audit: type=1400 audit(1456655446.525:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX kernel: [   27.984853] ifquery[510]: segfault at 0 ip 00007f9e716d2327 sp 00007fff51685e38 error 4 in libc-2.21.so[7f9e7158d000+1c0000]
Feb 28 11:30:50 ZBOX kernel: [   28.589471] audit: type=1400 audit(1456655447.377:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX kernel: [   28.589485] audit: type=1400 audit(1456655447.377:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX kernel: [   28.589494] audit: type=1400 audit(1456655447.377:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX kernel: [   28.589501] audit: type=1400 audit(1456655447.377:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=483 comm="apparmor_parser"
Feb 28 11:30:50 ZBOX openbsd-inetd[681]: ...done.
Feb 28 11:30:50 ZBOX systemd[1]: Started LSB: Start or stop the inetd daemon..
Feb 28 11:30:50 ZBOX ntpdate[708]: name server cannot be used: Temporary failure in name resolution (-3)
Feb 28 11:30:50 ZBOX systemd[1]: Starting LSB: Start NTP daemon...
Feb 28 11:30:50 ZBOX ntp[746]: * Starting NTP server ntpd
Feb 28 11:30:51 ZBOX ntpd[754]: ntpd 4.2.6p5@1.2349-o Thu Feb 11 18:27:01 UTC 2016 (1)
Feb 28 11:30:51 ZBOX ntpd[755]: proto: precision = 0.125 usec
Feb 28 11:30:51 ZBOX ntpd[755]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Feb 28 11:30:51 ZBOX ntpd[755]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Feb 28 11:30:51 ZBOX ntp[746]: ...done.
Feb 28 11:30:51 ZBOX systemd[1]: Started LSB: Start NTP daemon.
Feb 28 11:30:51 ZBOX ntpd[755]: Listen and drop on 1 v6wildcard :: UDP 123
Feb 28 11:30:51 ZBOX ntpd[755]: Listen normally on 2 lo 127.0.0.1 UDP 123
Feb 28 11:30:51 ZBOX ntpd[755]: Listen normally on 3 lo ::1 UDP 123
Feb 28 11:30:51 ZBOX ntpd[755]: peers refreshed
Feb 28 11:30:51 ZBOX ntpd[755]: Listening on routing socket on fd #20 for interface updates
Feb 28 11:30:51 ZBOX ntpd[755]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Feb 28 11:30:51 ZBOX ntpd[755]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Feb 28 11:30:51 ZBOX ntpd[755]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Feb 28 11:30:51 ZBOX ntpd[755]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Feb 28 11:30:51 ZBOX ntpd[755]: Deferring DNS for ntp.ubuntu.com 1
Feb 28 11:30:51 ZBOX ntpd[758]: signal_no_reset: signal 17 had flags 4000000
Feb 28 11:30:51 ZBOX ModemManager[661]: <info>  ModemManager (version 1.4.10) starting in system bus...
Feb 28 11:30:51 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkitd.service'
Feb 28 11:30:51 ZBOX systemd[1]: Starting Authenticate and Authorize Users to Run Privileged Tasks...
Feb 28 11:30:51 ZBOX systemd[1]: Started Thermal Daemon Service.
Feb 28 11:30:51 ZBOX thermald[685]: NO RAPL sysfs present
Feb 28 11:30:51 ZBOX thermald[685]: 13 CPUID levels; family:model:stepping 0x6:3a:9 (6:58:9)
Feb 28 11:30:51 ZBOX thermald[685]: Running on a vanilla kernel
Feb 28 11:30:51 ZBOX thermald[685]: Polling mode is enabled: 4
Feb 28 11:30:51 ZBOX thermald[685]: sensor_update: type acpitz
Feb 28 11:30:51 ZBOX thermald[685]: sensor_update: type acpitz
Feb 28 11:30:51 ZBOX thermald[685]: thd_read_default_thermal_sensors loaded 2 sensors
Feb 28 11:30:51 ZBOX thermald[685]: Thermal DTS: No coretemp sysfs found!!
Feb 28 11:30:51 ZBOX thermald[685]: failed to open /dev/acpi_thermal_rel
Feb 28 11:30:51 ZBOX thermald[685]: failed to open /dev/acpi_thermal_rel
Feb 28 11:30:51 ZBOX thermald[685]: TRT/ART read failed
Feb 28 11:30:51 ZBOX polkitd[766]: started daemon version 0.105 using authority implementation `local' version `0.105'
Feb 28 11:30:51 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Feb 28 11:30:51 ZBOX systemd[1]: Started Authenticate and Authorize Users to Run Privileged Tasks.
Feb 28 11:30:51 ZBOX systemd[1]: Started Modem Manager.
Feb 28 11:30:51 ZBOX NetworkManager[691]: <info>  NetworkManager (version 1.0.4) is starting...
Feb 28 11:30:51 ZBOX NetworkManager[691]: <info>  Read config: /etc/NetworkManager/NetworkManager.conf
Feb 28 11:30:51 ZBOX systemd[1]: Started Network Manager.
Feb 28 11:30:51 ZBOX systemd[1]: Starting Network Manager Wait Online...
Feb 28 11:30:51 ZBOX systemd[1]: Reached target Network.
Feb 28 11:30:51 ZBOX NetworkManager[691]: <info>  VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 28 11:30:51 ZBOX systemd[1]: Starting The PHP FastCGI Process Manager...
Feb 28 11:30:51 ZBOX NetworkManager[691]: <info>  DNS: loaded plugin dnsmasq
Feb 28 11:30:51 ZBOX systemd[1]: Starting OpenVPN service...
Feb 28 11:30:51 ZBOX systemd[1]: Started OpenBSD Secure Shell server.
Feb 28 11:30:51 ZBOX systemd[1]: Started OpenVPN service.
Feb 28 11:30:52 ZBOX accounts-daemon[675]: started daemon version 0.6.40
Feb 28 11:30:52 ZBOX systemd[1]: Started Accounts Service.
Feb 28 11:30:52 ZBOX thermald[685]: Dumping parsed XML Data
Feb 28 11:30:52 ZBOX thermald[685]: *** Index 0 ***
Feb 28 11:30:52 ZBOX thermald[685]: Name: GenericX86LaptopDevice
Feb 28 11:30:52 ZBOX thermald[685]: UUID:
Feb 28 11:30:52 ZBOX thermald[685]: type: 0
Feb 28 11:30:52 ZBOX thermald[685]: Sensor 0
Feb 28 11:30:52 ZBOX thermald[685]: Name: TSKN
Feb 28 11:30:52 ZBOX thermald[685]: Path:
Feb 28 11:30:52 ZBOX thermald[685]: Async Capable: 1
Feb 28 11:30:52 ZBOX thermald[685]: Virtual: 0
Feb 28 11:30:52 ZBOX thermald[685]: Zone 0
Feb 28 11:30:52 ZBOX thermald[685]: Name: SKIN
Feb 28 11:30:52 ZBOX thermald[685]: Trip Point 0
Feb 28 11:30:52 ZBOX thermald[685]: temp 55000
Feb 28 11:30:52 ZBOX thermald[685]: trip type 2
Feb 28 11:30:52 ZBOX thermald[685]: hyst id 0
Feb 28 11:30:52 ZBOX thermald[685]: sensor type TSKN
Feb 28 11:30:52 ZBOX thermald[685]: cdev index 0
Feb 28 11:30:52 ZBOX thermald[685]: type rapl_controller
Feb 28 11:30:52 ZBOX thermald[685]: influence 100
Feb 28 11:30:52 ZBOX thermald[685]: SamplingPeriod 16
Feb 28 11:30:52 ZBOX thermald[685]: cdev index 1
Feb 28 11:30:52 ZBOX thermald[685]: type intel_powerclamp
Feb 28 11:30:52 ZBOX thermald[685]: influence 100
Feb 28 11:30:52 ZBOX thermald[685]: SamplingPeriod 12
Feb 28 11:30:52 ZBOX thermald[685]: *** Index 1 ***
Feb 28 11:30:52 ZBOX thermald[685]: Name: ExamplePlatformName
Feb 28 11:30:52 ZBOX thermald[685]: UUID: ExampleUUID
Feb 28 11:30:52 ZBOX thermald[685]: type: 0
Feb 28 11:30:52 ZBOX thermald[685]: Sensor 0
Feb 28 11:30:52 ZBOX thermald[685]: Name: TSKN
Feb 28 11:30:52 ZBOX thermald[685]: Path:
Feb 28 11:30:52 ZBOX thermald[685]: Async Capable: 1
Feb 28 11:30:52 ZBOX thermald[685]: Virtual: 0
Feb 28 11:30:52 ZBOX thermald[685]: Sensor 1
Feb 28 11:30:52 ZBOX thermald[685]: Name: example_sensor_1
Feb 28 11:30:52 ZBOX thermald[685]: Path: /some_path
Feb 28 11:30:52 ZBOX thermald[685]: Async Capable: 0
Feb 28 11:30:52 ZBOX thermald[685]: Virtual: 0
Feb 28 11:30:52 ZBOX thermald[685]: Sensor 2
Feb 28 11:30:52 ZBOX thermald[685]: Name: example_thermal_sysfs_sensor
Feb 28 11:30:52 ZBOX thermald[685]: Path:
Feb 28 11:30:52 ZBOX thermald[685]: Async Capable: 1
Feb 28 11:30:52 ZBOX thermald[685]: Virtual: 0
Feb 28 11:30:52 ZBOX thermald[685]: Sensor 3
Feb 28 11:30:52 ZBOX thermald[685]: Name: example_virtual_sensor
Feb 28 11:30:52 ZBOX thermald[685]: Path:
Feb 28 11:30:52 ZBOX thermald[685]: Async Capable: 0
Feb 28 11:30:52 ZBOX thermald[685]: Virtual: 1
Feb 28 11:30:52 ZBOX thermald[685]: Link type: example_sensor_1
Feb 28 11:30:52 ZBOX thermald[685]: Link mult: 0,000000
Feb 28 11:30:52 ZBOX thermald[685]: Link offset: 10,000000
Feb 28 11:30:52 ZBOX thermald[685]: Zone 0
Feb 28 11:30:52 ZBOX thermald[685]: Name: ExampleZonetype
Feb 28 11:30:52 ZBOX thermald[685]: Trip Point 0
Feb 28 11:30:52 ZBOX thermald[685]: temp 75000
Feb 28 11:30:52 ZBOX thermald[685]: trip type 1
Feb 28 11:30:52 ZBOX thermald[685]: hyst id 0
Feb 28 11:30:52 ZBOX thermald[685]: sensor type example_sensor_1
Feb 28 11:30:52 ZBOX thermald[685]: cdev index 0
Feb 28 11:30:52 ZBOX thermald[685]: type example_cooling_device
Feb 28 11:30:52 ZBOX thermald[685]: influence 100
Feb 28 11:30:52 ZBOX thermald[685]: SamplingPeriod 12
Feb 28 11:30:52 ZBOX thermald[685]: Cooling Dev 0
Feb 28 11:30:52 ZBOX thermald[685]: Type: example_cooling_device
Feb 28 11:30:52 ZBOX thermald[685]: Path:
Feb 28 11:30:52 ZBOX thermald[685]: Min: 0
Feb 28 11:30:52 ZBOX thermald[685]: Max: 50
Feb 28 11:30:52 ZBOX thermald[685]: Step: 10
Feb 28 11:30:52 ZBOX thermald[685]: AutoDownControl: 0
Feb 28 11:30:52 ZBOX thermald[685]: PID: Kp 0,000000
Feb 28 11:30:52 ZBOX thermald[685]: PID: Ki 0,000000
Feb 28 11:30:52 ZBOX thermald[685]: PID: Kd 0,000000
Feb 28 11:30:52 ZBOX thermald[685]: Product Name matched [wildcard]
Feb 28 11:30:52 ZBOX thermald[685]: sensor id 2: No temp sysfs for reading raw temp
Feb 28 11:30:52 ZBOX thermald[685]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Feb 28 11:30:52 ZBOX thermald[685]: sensor index:1 acpitz /sys/class/thermal/thermal_zone1/ Async:0
Feb 28 11:30:52 ZBOX thermald[685]: thd_read_default_cooling devices loaded 7 cdevs
Feb 28 11:30:52 ZBOX thermald[685]: powercap RAPL no long term time window
Feb 28 11:30:52 ZBOX thermald[685]: RAPL device for cpu 0
Feb 28 11:30:52 ZBOX thermald[685]: MSR READ Failed
Feb 28 11:30:52 ZBOX thermald[685]: message repeated 5 times: [ MSR READ Failed]
Feb 28 11:30:52 ZBOX thermald[685]: Use Default pstate drv settings
Feb 28 11:30:52 ZBOX thermald[685]: Product Name matched [wildcard]
Feb 28 11:30:52 ZBOX thermald[685]: 0: Fan, C:0 MN: 0 MX:1 ST:1 pt:/sys/class/thermal/ rd_bk 1
Feb 28 11:30:52 ZBOX thermald[685]: 1: Fan, C:0 MN: 0 MX:1 ST:1 pt:/sys/class/thermal/ rd_bk 1
Feb 28 11:30:52 ZBOX thermald[685]: 2: Fan, C:1 MN: 0 MX:1 ST:1 pt:/sys/class/thermal/ rd_bk 1
Feb 28 11:30:52 ZBOX thermald[685]: 3: Fan, C:1 MN: 0 MX:1 ST:1 pt:/sys/class/thermal/ rd_bk 1
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  init!
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  update_system_hostname
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>        interface-parser: parsing file /etc/network/interfaces
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>        interface-parser: finished parsing file /etc/network/interfaces
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  guessed connection type (eth0) = 802-3-ethernet
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  adding eth0 to connections
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  adding iface eth0 to eni_ifaces
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  autoconnect
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  management mode: unmanaged
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  end _init.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded settings plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded settings plugin keyfile: (c) 2007 - 2015 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  SCPlugin-Ofono: init!
Feb 28 11:30:52 ZBOX NetworkManager[691]: <warn>  SCPlugin-Ofono: file doesn't exist: /var/lib/ofono
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  SCPlugin-Ofono: end _init.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded settings plugin ofono: (C) 2013 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  (42146880) ... get_connections.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  (42146880) ... get_connections (managed=false): return empty list.
Feb 28 11:30:52 ZBOX thermald[685]: 4: Fan, C:1 MN: 0 MX:1 ST:1 pt:/sys/class/thermal/ rd_bk 1
Feb 28 11:30:52 ZBOX thermald[685]: 5: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Feb 28 11:30:52 ZBOX thermald[685]: 6: Processor, C:0 MN: 0 MX:3 ST:1 pt:/sys/class/thermal/ rd_bk 0
Feb 28 11:30:52 ZBOX thermald[685]: 7: intel_pstate, C:0 MN: 0 MX:10 ST:1 pt:/sys/devices/system/cpu/intel_pstate/ rd_bk 1
Feb 28 11:30:52 ZBOX thermald[685]: zone acpitz bounded
Feb 28 11:30:52 ZBOX thermald[685]: zone acpitz bounded
Feb 28 11:30:52 ZBOX thermald[685]: Sorted trip dump :
Feb 28 11:30:52 ZBOX thermald[685]: index 2: type:active temp:55000 hyst:1 zone id:0 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Fan
Feb 28 11:30:52 ZBOX thermald[685]: index 1: type:active temp:87000 hyst:1 zone id:0 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Fan
Feb 28 11:30:52 ZBOX thermald[685]: index 0: type:critical temp:106000 hyst:1 zone id:0 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: trip type: 3 temp: 55000
Feb 28 11:30:52 ZBOX thermald[685]: trip type: 3 temp: 87000
Feb 28 11:30:52 ZBOX thermald[685]: trip type: 0 temp: 106000
Feb 28 11:30:52 ZBOX thermald[685]: sysfs write failed trip_point_0_temp
Feb 28 11:30:52 ZBOX thermald[685]: zone acpitz bounded
Feb 28 11:30:52 ZBOX thermald[685]: zone acpitz bounded
Feb 28 11:30:52 ZBOX thermald[685]: Sorted trip dump :
Feb 28 11:30:52 ZBOX thermald[685]: index 0: type:critical temp:106000 hyst:1 zone id:1 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: index 1: type:passive temp:106000 hyst:1 zone id:1 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Processor
Feb 28 11:30:52 ZBOX thermald[685]: trip type: 0 temp: 106000
Feb 28 11:30:52 ZBOX thermald[685]: trip type: 2 temp: 106000
Feb 28 11:30:52 ZBOX thermald[685]: sysfs write failed trip_point_0_temp
Feb 28 11:30:52 ZBOX thermald[685]: thd_read_default_thermal_zones loaded 2 zones
Feb 28 11:30:52 ZBOX thermald[685]: zone cpu will be created
Feb 28 11:30:52 ZBOX thermald[685]: /sys/class/hwmon/hwmon0/name->acpitz
Feb 28 11:30:52 ZBOX thermald[685]: Thermal DTS or hwmon: No Zones present Need to configure manually
Feb 28 11:30:52 ZBOX thermald[685]: Product Name matched [wildcard]
Feb 28 11:30:52 ZBOX thermald[685]: XML zone: invalid sensor type TSKN
Feb 28 11:30:52 ZBOX thermald[685]: Zone update failed: unable to bind
Feb 28 11:30:52 ZBOX thermald[685]: cthd_cpu_default_binding::do_default_binding: No relavent cpu cdevs
Feb 28 11:30:52 ZBOX thermald[685]: Zone 0: acpitz, Active:0 Bind:1 Sensor_cnt:1
Feb 28 11:30:52 ZBOX thermald[685]: ..sensors..
Feb 28 11:30:52 ZBOX thermald[685]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Feb 28 11:30:52 ZBOX thermald[685]: ..trips..
Feb 28 11:30:52 ZBOX thermald[685]: index 2: type:active temp:55000 hyst:1 zone id:0 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Fan
Feb 28 11:30:52 ZBOX thermald[685]: index 1: type:active temp:87000 hyst:1 zone id:0 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Fan
Feb 28 11:30:52 ZBOX thermald[685]: index 0: type:critical temp:106000 hyst:1 zone id:0 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: index 3: type:polling temp:50000 hyst:0 zone id:0 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: Zone 1: acpitz, Active:0 Bind:1 Sensor_cnt:1
Feb 28 11:30:52 ZBOX thermald[685]: ..sensors..
Feb 28 11:30:52 ZBOX thermald[685]: sensor index:0 acpitz /sys/class/thermal/thermal_zone0/ Async:1
Feb 28 11:30:52 ZBOX thermald[685]: ..trips..
Feb 28 11:30:52 ZBOX thermald[685]: index 0: type:critical temp:106000 hyst:1 zone id:1 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: index 1: type:passive temp:106000 hyst:1 zone id:1 sensor id:0 cdev size:1
Feb 28 11:30:52 ZBOX thermald[685]: cdev[0] Processor
Feb 28 11:30:52 ZBOX thermald[685]: index 2: type:polling temp:101000 hyst:0 zone id:1 sensor id:0 cdev size:0
Feb 28 11:30:52 ZBOX thermald[685]: FD = 8
Feb 28 11:30:52 ZBOX thermald[685]: Current user preference is 0
Feb 28 11:30:52 ZBOX thermald[685]: thd_engine_thread begin
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  SCPlugin-Ofono: (41968064) ... get_connections.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  SCPlugin-Ofono: (41968064) connections count: 0
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  get unmanaged devices count: 0
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  monitoring kernel firmware directory '/lib/firmware'.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMVxlanFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMVlanFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMVethFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMTunFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMMacvlanFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMInfinibandFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMGreFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMEthernetFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMBridgeFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMBondFactory (internal)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  WiFi enabled by radio killswitch; enabled by state file
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  WWAN enabled by radio killswitch; enabled by state file
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  WiMAX enabled by radio killswitch; enabled by state file
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  Networking is enabled by state file
Feb 28 11:30:52 ZBOX NetworkManager[691]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  (lo): link connected
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  (lo): new Generic device (carrier: ON, driver: 'unknown', ifindex: 1)
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  startup complete
Feb 28 11:30:52 ZBOX dbus[634]: [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
Feb 28 11:30:52 ZBOX systemd[1]: Starting WPA supplicant...
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  urfkill disappeared from the bus
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  ModemManager available in the bus
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  ofono is now available
Feb 28 11:30:52 ZBOX NetworkManager[691]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Feb 28 11:30:52 ZBOX dbus[634]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Feb 28 11:30:52 ZBOX wpa_supplicant[787]: Successfully initialized wpa_supplicant
Feb 28 11:30:52 ZBOX systemd[1]: Started WPA supplicant.
Feb 28 11:30:52 ZBOX NetworkManager[691]: <info>  wpa_supplicant running
Feb 28 11:30:52 ZBOX gpu-manager[674]: /etc/modprobe.d is not a file
Feb 28 11:30:52 ZBOX gpu-manager[674]: message repeated 3 times: [ /etc/modprobe.d is not a file]
Feb 28 11:30:52 ZBOX systemd[1]: Started Network Manager Wait Online.
Feb 28 11:30:52 ZBOX systemd[1]: Reached target Network is Online.
Feb 28 11:30:52 ZBOX systemd[1]: Starting LSB: start Samba NetBIOS nameserver (nmbd)...
Feb 28 11:30:52 ZBOX systemd[1]: Starting LSB: Tool to automatically collect and submit kernel crash signatures...
Feb 28 11:30:52 ZBOX systemd[1]: Starting /etc/rc.local Compatibility...
Feb 28 11:30:52 ZBOX systemd[1]: Starting LSB: start Samba daemons for the AD DC...
Feb 28 11:30:52 ZBOX systemd[1]: Starting LSB: Apache2 web server...
Feb 28 11:30:52 ZBOX systemd[1]: Starting TeamViewer remote control daemon...
Feb 28 11:30:52 ZBOX systemd[1]: Started /etc/rc.local Compatibility.
Feb 28 11:30:52 ZBOX systemd[1]: Starting Wait for Plymouth Boot Screen to Quit...
Feb 28 11:30:52 ZBOX apache2[817]: * Starting web server apache2
Feb 28 11:30:52 ZBOX systemd[1]: Started LSB: Tool to automatically collect and submit kernel crash signatures.
Feb 28 11:30:52 ZBOX whoopsie[660]: [11:30:52] Using lock path: /var/lock/whoopsie/lock
Feb 28 11:30:52 ZBOX whoopsie[660]: [11:30:52] offline
Feb 28 11:30:53 ZBOX systemd[1]: Started The PHP FastCGI Process Manager.
Feb 28 11:30:53 ZBOX systemd[1]: teamviewerd.service: PID file /var/run/teamviewerd.pid not readable (yet?) after start: No such file or directory
Feb 28 11:30:54 ZBOX systemd[1]: Started TeamViewer remote control daemon.
Feb 28 11:30:54 ZBOX apache2[817]: AH00548: NameVirtualHost has no effect and will be removed in the next release /etc/apache2/ports.conf:8
Feb 28 11:30:54 ZBOX systemd[1]: Started LSB: start Samba daemons for the AD DC.
Feb 28 11:30:54 ZBOX nmbd[804]: * Starting NetBIOS name server nmbd
Feb 28 11:30:54 ZBOX gpu-manager[674]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Feb 28 11:30:54 ZBOX systemd[1]: Started Detect the available GPUs and deal with any system changes.
Feb 28 11:30:54 ZBOX systemd[1]: Starting Light Display Manager...
Feb 28 11:30:54 ZBOX nmbd[804]: ...done.
Feb 28 11:30:54 ZBOX systemd[1]: Started LSB: start Samba NetBIOS nameserver (nmbd).
Feb 28 11:30:54 ZBOX systemd[1]: Received SIGRTMIN+21 from PID 186 (plymouthd).
Feb 28 11:30:55 ZBOX systemd[1]: Started Wait for Plymouth Boot Screen to Quit.
Feb 28 11:30:55 ZBOX systemd[1]: Started Getty on tty1.
Feb 28 11:30:55 ZBOX systemd[1]: Reached target Login Prompts.
Feb 28 11:30:55 ZBOX systemd[1]: Started Light Display Manager.
Feb 28 11:30:55 ZBOX apache2[817]: *
Feb 28 11:30:55 ZBOX systemd[1]: Started LSB: Apache2 web server.
Feb 28 11:30:55 ZBOX systemd[1]: Starting (null)...
Feb 28 11:30:55 ZBOX systemd[1]: Starting (null)...
Feb 28 11:30:55 ZBOX systemd[1]: Started (null).
Feb 28 11:30:55 ZBOX vncserver[932]: Starting VNC server: 1:vncserver No passwd entry for user 'vncserver'
Feb 28 11:30:55 ZBOX systemd[1]: vncserver.service: Control process exited, code=exited status=1
Feb 28 11:30:55 ZBOX systemd[1]: Failed to start (null).
Feb 28 11:30:55 ZBOX systemd[1]: vncserver.service: Unit entered failed state.
Feb 28 11:30:55 ZBOX systemd[1]: vncserver.service: Failed with result 'exit-code'.
Feb 28 11:30:55 ZBOX systemd[1]: Starting LSB: Record successful boot for GRUB...
Feb 28 11:30:55 ZBOX systemd[1]: Starting LSB: Set the CPU Frequency Scaling governor to "ondemand"...
Feb 28 11:30:55 ZBOX systemd[1]: Starting LSB: start Samba SMB/CIFS daemon (smbd)...
Feb 28 11:30:55 ZBOX systemd[1]: Starting LSB: Start the PulseAudio sound server...
Feb 28 11:30:55 ZBOX systemd[1]: Started LSB: Set the CPU Frequency Scaling governor to "ondemand".
Feb 28 11:30:55 ZBOX systemd[1]: Started LSB: Start the PulseAudio sound server.
Feb 28 11:30:55 ZBOX smbd[941]: * Starting SMB/CIFS daemon smbd
Feb 28 11:30:55 ZBOX systemd[1]: Started LSB: Record successful boot for GRUB.
Feb 28 11:30:55 ZBOX systemd[1]: Started LSB: start Samba SMB/CIFS daemon (smbd).
Feb 28 11:30:55 ZBOX systemd[1]: Reached target Multi-User System.
Feb 28 11:30:55 ZBOX systemd[1]: Reached target Graphical Interface.
Feb 28 11:30:55 ZBOX systemd[1]: Starting Update UTMP about System Runlevel Changes...
Feb 28 11:30:55 ZBOX systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
Feb 28 11:30:55 ZBOX smbd[941]: ...done.
Feb 28 11:30:55 ZBOX systemd[1]: Started Update UTMP about System Runlevel Changes.
Feb 28 11:30:55 ZBOX systemd[1]: Startup finished in 4.853s (kernel) + 31.988s (userspace) = 36.841s.
Feb 28 11:30:58 ZBOX systemd[1]: Created slice user-1000.slice.
Feb 28 11:30:58 ZBOX systemd[1]: Starting User Manager for UID 1000...
Feb 28 11:30:58 ZBOX systemd[1]: Started Session c1 of user wojcieh.
Feb 28 11:30:58 ZBOX systemd[996]: Reached target Sockets.
Feb 28 11:30:58 ZBOX systemd[996]: Reached target Paths.
Feb 28 11:30:58 ZBOX systemd[996]: Reached target Timers.
Feb 28 11:30:58 ZBOX systemd[996]: Reached target Basic System.
Feb 28 11:30:58 ZBOX systemd[996]: Reached target Default.
Feb 28 11:30:58 ZBOX systemd[996]: Startup finished in 42ms.
Feb 28 11:30:58 ZBOX systemd[1]: Started User Manager for UID 1000.
Feb 28 11:30:59 ZBOX systemd[1]: Started Session c2 of user wojcieh.
Feb 28 11:31:02 ZBOX NetworkManager[691]: <info>  WiFi hardware radio set enabled
Feb 28 11:31:02 ZBOX NetworkManager[691]: <info>  WWAN hardware radio set enabled
Feb 28 11:31:03 ZBOX org.a11y.atspi.Registry[1316]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Feb 28 11:31:03 ZBOX gnome-session[1314]: gnome-session-is-accelerated: llvmpipe detected.
Feb 28 11:31:03 ZBOX org.gnome.ScreenSaver[1216]: ** (gnome-screensaver:1396): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
Feb 28 11:31:03 ZBOX gnome-session[1314]: gnome-session[1314]: WARNING: Could not parse desktop file tracker-miner-fs.desktop or it references a not found TryExec binary
Feb 28 11:31:03 ZBOX gnome-session[1314]: WARNING: Could not parse desktop file tracker-miner-fs.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: gnome-session[1314]: WARNING: Could not parse desktop file caribou-autostart.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: WARNING: Could not parse desktop file caribou-autostart.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: gnome-session[1314]: WARNING: Could not parse desktop file tracker-store.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: WARNING: Could not parse desktop file tracker-store.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: WARNING: Could not parse desktop file xscreensaver.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: gnome-session[1314]: WARNING: Could not parse desktop file xscreensaver.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: gnome-session[1314]: WARNING: Could not parse desktop file indicator-printers.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: WARNING: Could not parse desktop file indicator-printers.desktop or it references a not found TryExec binary
Feb 28 11:31:04 ZBOX gnome-session[1314]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Feb 28 11:31:04 ZBOX gnome-session[1314]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Feb 28 11:31:04 ZBOX gnome-session[1314]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Feb 28 11:31:04 ZBOX dbus[634]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service'
Feb 28 11:31:04 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service'
Feb 28 11:31:04 ZBOX systemd[1]: Starting Daemon for power management...
Feb 28 11:31:05 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.UPower'
Feb 28 11:31:05 ZBOX systemd[1]: Started Daemon for power management.
Feb 28 11:31:06 ZBOX org.freedesktop.Geoclue.Master[1216]: Master options:
Feb 28 11:31:06 ZBOX org.freedesktop.Geoclue.Master[1216]: ** Message: GSettings key 'gps-baudrate' initialised to '0'
Feb 28 11:31:06 ZBOX org.freedesktop.Geoclue.Master[1216]: ** Message: GSettings key 'gps-device' initialised to '(null)'
Feb 28 11:31:06 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service'
Feb 28 11:31:06 ZBOX systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Feb 28 11:31:06 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Feb 28 11:31:06 ZBOX systemd[1]: Started RealtimeKit Scheduling Policy Service.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Successfully called chroot.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Successfully dropped privileges.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Successfully limited resources.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Running.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Watchdog thread running.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Canary thread running.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Successfully made thread 1539 of process 1539 (n/a) owned by '1000' high priority at nice level -11.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Supervising 1 threads of 1 processes of 1 users.
Feb 28 11:31:06 ZBOX org.freedesktop.Geoclue.Master[1216]: Found providers:
Feb 28 11:31:06 ZBOX org.freedesktop.Geoclue.Master[1216]: ubuntu-geoip.provider
Feb 28 11:31:06 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service'
Feb 28 11:31:06 ZBOX systemd[1]: Starting Manage, Install and Generate Color Profiles...
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Successfully made thread 1555 of process 1555 (n/a) owned by '1000' high priority at nice level -11.
Feb 28 11:31:06 ZBOX rtkit-daemon[1540]: Supervising 2 threads of 2 processes of 1 users.
Feb 28 11:31:06 ZBOX pulseaudio[1555]: [pulseaudio] pid.c: Daemon already running.
Feb 28 11:31:06 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Feb 28 11:31:06 ZBOX systemd[1]: Started Manage, Install and Generate Color Profiles.
Feb 28 11:31:06 ZBOX gnome-session[1314]: (process:1564): indicator-application-service-WARNING **: Name Lost
Feb 28 11:31:06 ZBOX gnome-session[1314]: Entering running state
Feb 28 11:31:06 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Feb 28 11:31:06 ZBOX gnome-session[1314]: Init...
Feb 28 11:31:06 ZBOX gnome-session[1314]: Checking setup...
Feb 28 11:31:06 ZBOX gnome-session[1314]: Launching TeamViewer ...
Feb 28 11:31:07 ZBOX systemd[1]: Starting Locale Service...
Feb 28 11:31:07 ZBOX dbus[634]: [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
Feb 28 11:31:07 ZBOX systemd[1]: Starting Disk Manager...
Feb 28 11:31:07 ZBOX gnome-session[1314]: (vino-server:1562): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion 'global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
Feb 28 11:31:08 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.locale1'
Feb 28 11:31:08 ZBOX systemd[1]: Started Locale Service.
Feb 28 11:31:08 ZBOX udisksd[1712]: udisks daemon version 2.1.6 starting
Feb 28 11:31:08 ZBOX dbus[634]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Feb 28 11:31:08 ZBOX systemd[1]: Started Disk Manager.
Feb 28 11:31:08 ZBOX udisksd[1712]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Feb 28 11:31:08 ZBOX gnome-session[1314]: FATAL: The application binary appears to be running setuid, this is a security hole.
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Autoprobing TCP port in (all) network interface
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv6://[::]:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv4://0.0.0.0:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Autoprobing selected port 5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising security type: 'TLS' (18)
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv6://[::]:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv4://0.0.0.0:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Clearing securityTypes
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising security type: 'TLS' (18)
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Clearing securityTypes
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising security type: 'TLS' (18)
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising authentication type: 'No Authentication' (1)
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv6://[::]:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Listening IPv4://0.0.0.0:5900
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Clearing securityTypes
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Clearing authTypes
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising security type: 'TLS' (18)
Feb 28 11:31:09 ZBOX gnome-session[1314]: 28/02/2016 11:31:09 Advertising authentication type: 'VNC Authentication' (2)
Feb 28 11:31:09 ZBOX org.gtk.Private.AfcVolumeMonitor[1216]: Volume monitor alive
Feb 28 11:31:16 ZBOX gnome-session[1314]: ** (unity-fallback-mount-helper:1571): WARNING **: Can't call IsLocked() on the Unity.Session object: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'com.canonical.Unity.Session' on object at path /com/canonical/Unity/Session
Feb 28 11:31:16 ZBOX org.gnome.ScreenSaver[1216]: ** Message: Lost the name, shutting down.
Feb 28 11:31:27 ZBOX gnome-session[1314]: (nm-applet:1574): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Feb 28 11:31:27 ZBOX org.gnome.zeitgeist.Engine[1216]: ** (zeitgeist-datahub:1966): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Feb 28 11:31:29 ZBOX pulseaudio[1539]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Feb 28 11:31:41 ZBOX systemd[1]: Starting Stop ureadahead data collection...
Feb 28 11:31:41 ZBOX systemd[1]: Stopped Read required files in advance.
Feb 28 11:31:41 ZBOX systemd[1]: Started Stop ureadahead data collection.
Feb 28 11:32:15 ZBOX gnome-session[1314]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Feb 28 11:35:52 ZBOX kernel: [  333.240801] usb 4-1.3: new low-speed USB device number 3 using ehci-pci
Feb 28 11:35:52 ZBOX kernel: [  333.336297] usb 4-1.3: New USB device found, idVendor=04b3, idProduct=310c
Feb 28 11:35:52 ZBOX kernel: [  333.336304] usb 4-1.3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Feb 28 11:35:52 ZBOX kernel: [  333.336307] usb 4-1.3: Product: USB Optical Mouse
Feb 28 11:35:52 ZBOX mtp-probe: checking bus 4, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.3"
Feb 28 11:35:52 ZBOX mtp-probe: bus: 4, device: 3 was not an MTP device
Feb 28 11:36:05 ZBOX kernel: [  346.498654] usb 4-1.3: USB disconnect, device number 3
Feb 28 11:36:08 ZBOX kernel: [  349.486094] usb 4-1.3: new high-speed USB device number 4 using ehci-pci
Feb 28 11:36:09 ZBOX kernel: [  350.361778] usb 4-1.3: New USB device found, idVendor=0325, idProduct=ac02
Feb 28 11:36:09 ZBOX kernel: [  350.361785] usb 4-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 28 11:36:09 ZBOX kernel: [  350.361788] usb 4-1.3: Product: RALLY2
Feb 28 11:36:09 ZBOX kernel: [  350.361791] usb 4-1.3: Manufacturer: OCZ Technology
Feb 28 11:36:09 ZBOX kernel: [  350.361794] usb 4-1.3: SerialNumber: AA04012700311413
Feb 28 11:36:09 ZBOX mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.3"
Feb 28 11:36:09 ZBOX mtp-probe: bus: 4, device: 4 was not an MTP device



```

---

### Post by HermanAB on 2016-02-28
The best and fastest way to recover is to reinstall.  It only takes about 30 minutes.

---

### Post by Wojciech_Marusiak on 2016-02-28
This I know but post configuration will take more than 2 or 3 hours :(

---

### Post by grahammechanical on 2016-02-28
I would like to be clear in my mind about the situation.

Did you remove all the previous kernels and then remove the only kernel left?

At the Grub menu we can select Advanced options for Ubuntu. That is a sub-menu and once we open that we can select previous kernels. That is if we have not removed all of them.

It is advisable to leave at least 2 kernels that we know are working. Then when we get a kernel upgrade that does not work so well we can use Advance options and last the last working kernel.

Also, what kernel did you install? Where did you get it from? You may have installed a kernel that was even newer than the one that was causing problems for you. It may also have its own problems.

Regards

---

### Post by Wojciech_Marusiak on 2016-02-28
Hi, 

The best way is to see it from log :)

```

2016-02-28 09:59:38 startup packages purge
2016-02-28 09:59:38 status installed linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:48 remove linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30 <none>
2016-02-28 09:59:48 status half-configured linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:48 status half-installed linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:55 status config-files linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:55 status config-files linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:55 status config-files linux-headers-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:55 status not-installed linux-headers-4.2.0-25-generic:amd64 <none>
2016-02-28 09:59:55 status installed linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:55 remove linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 09:59:55 status half-configured linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:55 status half-installed linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:57 status config-files linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:57 status config-files linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:57 status config-files linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 09:59:58 status not-installed linux-headers-4.2.0-27-generic:amd64 <none>
2016-02-28 09:59:58 status installed linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:58 remove linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30 <none>
2016-02-28 09:59:58 status half-configured linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 09:59:58 status half-installed linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:18 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:18 purge linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30 <none>
2016-02-28 10:00:18 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status config-files linux-image-extra-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status not-installed linux-image-extra-4.2.0-25-generic:amd64 <none>
2016-02-28 10:00:19 status installed linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 remove linux-image-4.2.0-25-generic:amd64 4.2.0-25.30 <none>
2016-02-28 10:00:19 status half-configured linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:19 status half-installed linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:22 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:22 purge linux-image-4.2.0-25-generic:amd64 4.2.0-25.30 <none>
2016-02-28 10:00:22 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:23 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:23 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:23 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:23 status config-files linux-image-4.2.0-25-generic:amd64 4.2.0-25.30
2016-02-28 10:00:23 status not-installed linux-image-4.2.0-25-generic:amd64 <none>
2016-02-28 10:00:23 status installed linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:23 remove linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 10:00:23 status half-configured linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:23 status half-installed linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:39 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:39 purge linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 10:00:39 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:39 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:39 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:39 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:40 status config-files linux-image-extra-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:40 status not-installed linux-image-extra-4.2.0-27-generic:amd64 <none>
2016-02-28 10:00:40 status installed linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:40 remove linux-image-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 10:00:40 status half-configured linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:40 status half-installed linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 purge linux-image-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status config-files linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:00:43 status not-installed linux-image-4.2.0-27-generic:amd64 <none>
2016-02-28 10:00:43 startup packages configure
2016-02-28 10:04:26 startup packages purge
2016-02-28 10:04:26 status installed linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:26 remove linux-generic:amd64 4.2.0.30.33 <none>
2016-02-28 10:04:26 status half-configured linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:26 status half-installed linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:26 status config-files linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:26 status config-files linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status config-files linux-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status not-installed linux-generic:amd64 <none>
2016-02-28 10:04:27 status installed linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 remove linux-image-generic:amd64 4.2.0.30.33 <none>
2016-02-28 10:04:27 status half-configured linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status half-installed linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status config-files linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status config-files linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status config-files linux-image-generic:amd64 4.2.0.30.33
2016-02-28 10:04:27 status not-installed linux-image-generic:amd64 <none>
2016-02-28 10:04:27 status installed linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:27 remove linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36 <none>
2016-02-28 10:04:27 status half-configured linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:27 status half-installed linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:41 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:41 purge linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36 <none>
2016-02-28 10:04:41 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:41 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:41 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:41 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:42 status config-files linux-image-extra-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:42 status not-installed linux-image-extra-4.2.0-30-generic:amd64 <none>
2016-02-28 10:04:42 status installed linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:42 remove linux-image-4.2.0-30-generic:amd64 4.2.0-30.36 <none>
2016-02-28 10:04:42 status half-configured linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:42 status half-installed linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:44 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:44 purge linux-image-4.2.0-30-generic:amd64 4.2.0-30.36 <none>
2016-02-28 10:04:44 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:44 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:44 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:45 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:45 status config-files linux-image-4.2.0-30-generic:amd64 4.2.0-30.36
2016-02-28 10:04:45 status not-installed linux-image-4.2.0-30-generic:amd64 <none>
2016-02-28 10:04:45 startup packages configure
2016-02-28 10:49:39 startup archives unpack
2016-02-28 10:49:49 install linux-image-4.2.0-27-generic:amd64 <none> 4.2.0-27.32
2016-02-28 10:49:49 status half-installed linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:49:55 status unpacked linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:49:55 status unpacked linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:49:56 startup packages configure
2016-02-28 10:49:56 configure linux-image-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 10:49:56 status unpacked linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:49:56 status half-configured linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:50:16 status installed linux-image-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 10:50:17 startup packages configure
2016-02-28 11:16:56 startup archives unpack
2016-02-28 11:17:06 install linux-headers-4.2.0-27-generic:amd64 <none> 4.2.0-27.32
2016-02-28 11:17:06 status half-installed linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:09 status unpacked linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:09 status unpacked linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:10 startup packages configure
2016-02-28 11:17:10 configure linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32 <none>
2016-02-28 11:17:10 status unpacked linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:10 status half-configured linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:10 status installed linux-headers-4.2.0-27-generic:amd64 4.2.0-27.32
2016-02-28 11:17:10 startup packages configure

```

I had this package installed where you specify how many kernels you want - I selected 2. When I removed latest kernel 4.2.0-30 I should have 4.2.0-27 - why it didn't stay I don't know. Anyway - I managed to mount previous partition and chroot there, install kernel and headers to existing installation just apt-get install bla bla. 

About advanced grub menu - after selection it loads but hangs. You can't control it. I don't have there last working kernel option.

---

### Post by Wojciech_Marusiak on 2016-03-03
I managed to fix issue. I chrooted again to Ubuntu and I installed latest available kernel. After updating GRUB it was working again.

---

