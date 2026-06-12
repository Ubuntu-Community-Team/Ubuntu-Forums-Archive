---
title: "Eight boot log files and can't open/read them ???"
date: 2023-10-14
forum: General Help
---

### Post by diablo2222 on 2023-10-14
I'm trying to check the boot log but something seems weird. I went to var/log/ and there I have not one, but** eight** boot log.
boot.log
boot.log.1
boot.log.2
boot.log.3
boot.log.4
boot.log.5
boot.log.6
boot.log.7


Is this normal? Also, I tried to open them but I can't. There's an "X" on the icons so the files are locked. Is this normal? How to open and read those files?


Thanks for helping!

---

### Post by MAFoElffen on 2023-10-14
From the command line, do 
```

mafoelffen@Mikes-ThinkPad-T520:~$ file /var/log/boot.log.*
/var/log/boot.log.1: regular file, no read permission
/var/log/boot.log.2: regular file, no read permission
/var/log/boot.log.3: regular file, no read permission
/var/log/boot.log.4: regular file, no read permission
/var/log/boot.log.5: regular file, no read permission
/var/log/boot.log.6: regular file, no read permission
/var/log/boot.log.7: regular file, no read permission
mafoelffen@Mikes-ThinkPad-T520:~$ sudo file /var/log/boot.log.*
[sudo] password for mafoelffen: 
/var/log/boot.log.1: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.2: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.3: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.4: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.5: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.6: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences
/var/log/boot.log.7: Unicode text, UTF-8 text, with CRLF, LF line terminators, with escape sequences

```
You can see that a user does not have read permissions to see those extended logs. But root does.

So in reading those, I filter through them with 'grep'. Be aware that the contents does have escape sequences for how it displays on a console... It you try to use more or less with that, it will include un-interpretted escape sequences. Do not use it with those two utilities.
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo grep -A50 -e '.' /var/log/boot.log.1
------------ Sat Jul 08 12:31:37 PDT 2023 ------------
[  OK  ] Finished Flush Journal to Persistent Storage.
[  OK  ] Started Show Plymouth Boot Screen.
[  OK  ] Started Forward Password R&#8230;s to Plymouth Directory Watch.
[  OK  ] Reached target Local Encrypted Volumes.
[  OK  ] Found device Samsung_SSD_870_QVO_2TB 2.
         Mounting /home/mafoelffen/Disk2...
[  OK  ] Found device Samsung_SSD_870_QVO_2TB _SYSTEM_.
         Starting File System Check&#8230;/dev/disk/by-uuid/281F-B438...
[  OK  ] Started File System Check Daemon to report status.
[  OK  ] Mounted /home/mafoelffen/Disk2.
[  OK  ] Listening on Load/Save RF &#8230;itch Status /dev/rfkill Watch.
         Starting Load/Save RF Kill Switch Status...
[  OK  ] Finished File System Check&#8230;n /dev/disk/by-uuid/281F-B438.
         Mounting /boot/efi...
[  OK  ] Mounted /boot/efi.
         Starting Load Kernel Module chromeos_pstore...
         Starting Load Kernel Module efi_pstore...
         Starting Load Kernel Module pstore_blk...
         Starting Load Kernel Module pstore_zone...
         Starting Load Kernel Module ramoops...
[  OK  ] Finished Load Kernel Module pstore_blk.
[  OK  ] Finished Load Kernel Module efi_pstore.
[  OK  ] Finished Load Kernel Module pstore_zone.
[  OK  ] Finished Load Kernel Module ramoops.
         Starting Load Kernel Module efi_pstore...
         Starting Load Kernel Module pstore_blk...
         Starting Load Kernel Module pstore_zone...
         Starting Load Kernel Module ramoops...
[  OK  ] Finished Load Kernel Module efi_pstore.
[  OK  ] Finished Load Kernel Module pstore_blk.
[  OK  ] Finished Load Kernel Module pstore_zone.
[  OK  ] Finished Load Kernel Module ramoops.
[  OK  ] Started Load/Save RF Kill Switch Status.
         Starting Load Kernel Module efi_pstore...
         Starting Load Kernel Module pstore_blk...
         Starting Load Kernel Module pstore_zone...
         Starting Load Kernel Module ramoops...
[  OK  ] Finished Load Kernel Module efi_pstore.
[  OK  ] Finished Load Kernel Module pstore_blk.
[  OK  ] Finished Load Kernel Module pstore_zone.
[  OK  ] Finished Load Kernel Module ramoops.
[  OK  ] Found device Dogfish_SSD_1TB mSATA1.
[  OK  ] Finished Load Kernel Module chromeos_pstore.
         Mounting /home/mafoelffen/mSATA...
[  OK  ] Created slice Slice /system/systemd-backlight.
         Starting Load/Save Screen Backlight Brightness of backlight:acpi_video1...
[  OK  ] Mounted /home/mafoelffen/mSATA.
[  OK  ] Finished Load/Save Screen Backlight Brightness of backlight:acpi_video1.
         Starting Load Kernel Module chromeos_pstore...
         Starting Load Kernel Module efi_pstore...
         Starting Load Kernel Module pstore_blk...
         Starting Load Kernel Module pstore_zone...
         Starting Load Kernel Module ramoops...
         Starting Load/Save Screen Backlight Brightness of backlight:acpi_video0...
         Starting Load/Save Screen Backlight Brightness of backlight:intel_backlight...
[  OK  ] Reached target Local File Systems.
         Starting Load AppArmor profiles...
         Starting Enable support for additional executable binary formats...
         Starting Set console font and keymap...
         Starting Create final runtime dir for shutdown pivot root...
         Starting Tell Plymouth To Write Out Runtime Data...
         Starting QEMU KVM preparation - module, ksm, hugepages...
         Starting Create Volatile Files and Directories...
         Starting Uncomplicated firewall...
[  OK  ] Finished Load Kernel Module efi_pstore.
[  OK  ] Finished Load Kernel Module pstore_blk.
[  OK  ] Finished Load Kernel Module pstore_zone.
[  OK  ] Finished Load Kernel Module ramoops.
[  OK  ] Finished Load/Save Screen Backlight Brightness of backlight:acpi_video0.
[  OK  ] Finished Load/Save Screen Backlight Brightness of backlight:intel_backlight.
[  OK  ] Finished Set console font and keymap.
[  OK  ] Finished Create final runtime dir for shutdown pivot root.
[  OK  ] Finished Tell Plymouth To Write Out Runtime Data.
[  OK  ] Finished Uncomplicated firewall.
[  OK  ] Reached target Preparation for Network.
         Mounting Arbitrary Executable File Formats File System...
[  OK  ] Finished QEMU KVM preparation - module, ksm, hugepages.
[  OK  ] Finished Create Volatile Files and Directories.
         Mounting RPC Pipe File System...
         Starting RPC bind portmap service...
         Starting Network Name Resolution...
         Starting Network Time Synchronization...
         Starting Record System Boot/Shutdown in UTMP...
[  OK  ] Finished Load Kernel Module chromeos_pstore.
[  OK  ] Mounted Arbitrary Executable File Formats File System.
[  OK  ] Started RPC bind portmap service.
[  OK  ] Finished Enable support for additional executable binary formats.
[  OK  ] Reached target RPC Port Mapper.
[  OK  ] Finished Record System Boot/Shutdown in UTMP.
[  OK  ] Mounted RPC Pipe File System.
[  OK  ] Reached target rpc_pipefs.target.
[  OK  ] Reached target NFS client services.
[  OK  ] Reached target Preparation for Remote File Systems.
[  OK  ] Reached target Remote File Systems.
[  OK  ] Finished Load AppArmor profiles.
         Starting Load AppArmor profiles managed internally by snapd...
[  OK  ] Started Network Time Synchronization.
[  OK  ] Reached target System Time Set.
[  OK  ] Started Network Name Resolution.
[  OK  ] Reached target Host and Network Name Lookups.
[  OK  ] Finished Load AppArmor profiles managed internally by snapd.
[  OK  ] Reached target System Initialization.
[  OK  ] Started ACPI Events Check.
[  OK  ] Started CUPS Scheduler.
[  OK  ] Started Start whoopsie on modification of the /var/crash directory.
[  OK  ] Started Trigger anacron every hour.
[  OK  ] Started Daily apt download activities.
[  OK  ] Started Daily apt upgrade and clean activities.
[  OK  ] Started Daily dpkg database backup timer.
[  OK  ] Started Periodic ext4 Online Metadata Check for All Filesystems.
[  OK  ] Started Discard unused blocks once a week.
[  OK  ] Started Refresh fwupd metadata regularly.
[  OK  ] Started Daily rotation of log files.
[  OK  ] Started Daily man-db regeneration.
[  OK  ] Started Message of the Day.
[  OK  ] Started Daily Cleanup of Temporary Directories.
[  OK  ] Started Ubuntu Advantage Timer for running repeated jobs.
[  OK  ] Reached target Path Units.
[  OK  ] Listening on ACPID Listen Socket.
[  OK  ] Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
         Starting Cockpit Web Service Socket...
[  OK  ] Listening on CUPS Scheduler.
[  OK  ] Listening on D-Bus System Message Bus Socket.
         Starting Libvirt local socket...
[  OK  ] Listening on Socket unix for snap application lxd.daemon.
[  OK  ] Listening on Socket unix for snap application lxd.user-daemon.
         Starting Socket activation for snappy daemon...
[  OK  ] Listening on UUID daemon activation socket.
[  OK  ] Listening on Virtual machine lock manager socket.
[  OK  ] Listening on Virtual machine lock manager admin socket.
[  OK  ] Listening on Virtual machine log manager socket.
[  OK  ] Listening on Virtual machine log manager socket.
[  OK  ] Listening on Libvirt local socket.
[  OK  ] Listening on Socket activation for snappy daemon.
[  OK  ] Listening on Libvirt admin socket.
[  OK  ] Listening on Libvirt local read-only socket.
[  OK  ] Listening on Cockpit Web Service Socket.
[  OK  ] Reached target Socket Units.
[  OK  ] Reached target Basic System.
[  OK  ] Started ACPI event daemon.
[  OK  ] Started Run anacron jobs.
         Starting LSB: automatic crash report generation...
         Starting Avahi mDNS/DNS-SD Stack...
         Starting Bluetooth service...
[  OK  ] Started D-Bus System Message Bus.
         Starting Network Manager...
[  OK  ] Started Save initial kernel messages after boot.
         Starting Remove Stale Online ext4 Metadata Check Snapshots...
         Starting LSB: EPSON Custom Backend Daemon...
         Starting Detect the available GPUs and deal with any system changes...
         Starting Record successful boot for GRUB...
[  OK  ] Started irqbalance daemon.
         Starting Initialize hardware monitoring sensors...
[  OK  ] Started FUSE filesystem for LXC.
         Starting Dispatcher daemon for systemd-networkd...
         Starting Authorization Manager...
         Starting Power Profiles daemon...
         Starting System Logging Service...
         Starting Self Monitoring and Reporting Technology (SMART) Daemon...
[  OK  ] Reached target Preparation for Logins.
         Starting Snap Daemon...
[  OK  ] Reached target User and Group Name Lookups.
[DEPEND] Dependency failed for SSSD NSS Service responder socket.
[DEPEND] Dependency failed for SSSD AutoFS Service responder socket.
[DEPEND] Dependency failed for SSSD PAC Service responder socket.
[DEPEND] Dependency failed for SSSD PAM Service responder private socket.
[DEPEND] Dependency failed for SSSD PAM Service responder socket.
[DEPEND] Dependency failed for SSSD SSH Service responder socket.
[DEPEND] Dependency failed for SSSD Sudo Service responder socket.
         Starting Accounts Service...
         Starting Deferred execution scheduler...
[  OK  ] Started Regular background program processing daemon.
         Starting Switcheroo Control Proxy service...
         Starting User Login Management...
         Starting Virtual Machine and Container Registration Service...
         Starting Thermal Daemon Service...
         Starting Disk Manager...
         Starting LSB: start and stop UML networking services...
         Starting WPA supplicant...
[  OK  ] Started LSB: EPSON Custom Backend Daemon.
[  OK  ] Started Deferred execution scheduler.
[  OK  ] Started System Logging Service.
[  OK  ] Finished Initialize hardware monitoring sensors.
[  OK  ] Finished Record successful boot for GRUB.
         Starting GRUB failed boot detection...
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Finished Remove Stale Online ext4 Metadata Check Snapshots.
[  OK  ] Finished Detect the available GPUs and deal with any system changes.
[  OK  ] Finished GRUB failed boot detection.
[  OK  ] Started Virtual Machine and Container Registration Service.
[  OK  ] Started Avahi mDNS/DNS-SD Stack.
[  OK  ] Started WPA supplicant.
[  OK  ] Started Thermal Daemon Service.
[  OK  ] Started Network Manager.
[  OK  ] Started Switcheroo Control Proxy service.
[  OK  ] Reached target Network.
         Starting Network Manager Wait Online...
         Starting Save/Restore Sound Card State...
         Starting CUPS Scheduler...
[  OK  ] Started LXC Container Monitoring Daemon.
         Starting OpenVPN service...
[  OK  ] Started Service for snap application canonical-livepatch.canonical-livepatchd.
         Starting Service for snap application lxd.activate...
         Starting OpenBSD Secure Shell server...
         Starting Permit User Sessions...
         Starting xrdp session manager...
[  OK  ] Finished OpenVPN service.
[  OK  ] Finished Permit User Sessions.
[  OK  ] Started Bluetooth service.
[  OK  ] Started Authorization Manager.
[  OK  ] Started Power Profiles daemon.
[  OK  ] Started User Login Management.
[  OK  ] Reached target Bluetooth Support.
         Starting Modem Manager...
         Starting Virtualization daemon...
         Starting Light Display Manager...
         Starting Hold until boot process finishes up...
         Starting Hostname Service...
[  OK  ] Started Unattended Upgrades Shutdown.
[  OK  ] Started Self Monitoring and Reporting Technology (SMART) Daemon.
[  OK  ] Finished Save/Restore Sound Card State.
[  OK  ] Reached target Sound Card.
[  OK  ] Started xrdp session manager.
         Starting xrdp daemon...
[  OK  ] Started OpenBSD Secure Shell server.
         Starting Manage, Install and Generate Color Profiles...

```

---

### Post by Impavidus on 2023-10-15
Log files are rotated. So, somewhat regularly (although I find that I have 5 boot.log* from August, 2 from September and 1 from October) boot.log.7 is deleted, boot.log.6 is renamed boot.log.7, boot.log.5 is renamed boot.log.6, ..., boot.log is renamed boot.log.1 and a new boot.log is started. This happens for all the log files in /var/log, but the frequency at which they are rotated and the number of old logs retained varies. For some log files, the old ones get compressed and get a .gz suffix.

Some logs contain information you don't want to share with ordinary users, so those have read permission only for the root user or (somewhat less restrictive) for members of the adm group.

So what you see is completely normal.

---

