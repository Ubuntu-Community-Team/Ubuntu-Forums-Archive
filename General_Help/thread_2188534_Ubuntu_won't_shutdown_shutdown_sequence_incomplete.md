---
title: "Ubuntu won't shutdown: shutdown sequence incomplete; stripped init scripts?"
date: 2013-11-17
forum: General Help
---

### Post by quequotion on 2013-11-17
Recently, Ubuntu doesn't power off.

It's not an ACPI or APM issue (ie, changes to grub are unnecessary and irrelevant) as I haven't had any with the kernel I've been using for most of the last year and the shutdown problem started only a few weeks ago. I haven't changed any relevant system settings or kernel modules in the last few weeks either. I have upgraded several times, and I think that one of the upgrades caused this problem.

Attempting to shut down or reboot by any method (other than a Magic Key sequence) fails without error during the shutdown sequence. Ubuntu logs out, plymouth's shutdown splash appears, and I can see the shutdown script output with [F2], but I cannot type into any of the terminals [Ctrl]+[Alt]+[1~6].

There's no error displayed on the screen or in the logs, but it looks like some parts of the the shutdown sequence are not happening. Specifically: running tasks are not sent SIGTERM, disks are not spun down, and the system is not powered off, which I've gleaned from the the output of the Magic Key sequence [Alt]+[Shift]+[PrScrn]+[R],[E],[I],[S],[U],[B/O], which is the only way to actually perform reboot or shutdown.

I'm rather suspicious of something may have gone wrong during an update a few weeks ago: **it seems (nearly) all the init scripts on my system have been *stripped* of their LSB headers**.

At the time, I didn't think it was a big deal because the output didn't look dangerous. I've tried to recreate that output by reinstalling initscripts and lsb-base```
$ sudo apt-get install --reinstall initscripts lsb-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0 B/38.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 380892 files and directories currently installed.)
Preparing to replace lsb-base 4.0-0ubuntu20.3 (using .../lsb-base_4.0-0ubuntu20.3_all.deb) ...
Unpacking replacement lsb-base ...
Setting up lsb-base (4.0-0ubuntu20.3) ...
(Reading database ... 380892 files and directories currently installed.)
Preparing to replace initscripts 2.88dsf-13.10ubuntu11.1 (using .../initscripts_2.88dsf-13.10ubuntu11.1_amd64.deb) ...
Unpacking replacement initscripts ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up initscripts (2.88dsf-13.10ubuntu11.1) ...
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6 S) of script `urandom' overwrites defaults (S).
insserv: warning: current stop runlevel(s) (empty) of script `urandom' overwrites defaults (0 6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (empty) of script `halt' overwrites defaults (0).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (empty) of script `reboot' overwrites defaults (6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (empty) of script `umountroot' overwrites defaults (0 6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (empty) of script `umountfs' overwrites defaults (0 6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: current stop runlevel(s) (empty) of script `sendsigs' overwrites defaults (0 6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
insserv: warning: script 'fluidsynth' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
```For example, during the Magic Key sequence there is a struggle to kill modemmanager (one of the scripts now stripped of Default-Stop). I believe this shows the problem to be nothing is able to stop certain services and the shutdown sequence comes to a halt with nothing further to do. Perhaps this has something to do with the push to convert to upstart?

Is there a way to repair the init scripts?
At the very least, can someone tell me how to get more information logged?

I'd fix it myself, but I have nothing to go on other than the problem with init scripts.

---

### Post by quequotion on 2013-12-07
Let me put this another way:

One day Ubuntu inexplicably stopped entering runlevel 0. *It just won't*; no matter what kind of shutdown command is used.

So, fumbling around in the dark as I am, I'm going to try some random hacky fixes I found on the internet for similar, but not quite the same, problems.

Specifically the recommendaitons for [this bug]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122") which has a title that sounds like my problem, but a description that is totally unrelated to the title; and [this problem](http://www.linuxforums.org/forum/ubuntu-linux/147634-solved-ubuntu-does-not-umount-filesystems-shutdown-restart.html) which could, theoretically, be what's wrong but I have no way of knowing that since I have no idea how I'm supposed to find out what is causing Ubuntu not to shutdown.

Accordingly, I'm trying these commands:```
sudo update-rc.d -f umountroot remove
sudo update-rc.d -f umountfs remove
sudo update-rc.d -f umountnfs.sh remove
sudo update-rc.d -f halt remove
sudo update-rc.d -f reboot remove
sudo update-rc.d -f sendsigs remove
sudo update-rc.d sendsigs start 20 0 6 .
sudo update-rc.d umountnfs.sh start 31 0 6 .
sudo update-rc.d umountfs start 40 0 6 .
sudo update-rc.d umountroot start 60 0 6 .
sudo update-rc.d halt start 90 0 .
sudo update-rc.d reboot start 90 6 .
```

Once again, after every single one of those I got a whole lot of errors from insserv, which is very upset about missing LSB Headers:```
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `modemmanager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `modemmanager'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `pulseaudio'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `pulseaudio'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-container'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-container'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-restore'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-fallback-graphics'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-fallback-graphics'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `passwd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `passwd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `avahi-daemon'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `avahi-daemon'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `lightdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `lightdm'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `whoopsie'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `whoopsie'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `smbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `smbd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `nmbd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `nmbd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cups'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cups'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-store'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
```

I noticed also that update-rc.d mentions I am using dependency based boot sequencing. I have no idea how long that's been going on or if I ever was using legacy boot ordering. From the sound of it, I don't think I want to use legacy, but then I can't really tell which is "better" after hours of reading about both.

Going to try and reboot now, wish me luck!

---

### Post by quequotion on 2013-12-07
[SIZE=7]It WORKED![/SIZE]

My instincts were right. *Something* stripped my init scripts and *ruined* the shutdown sequence. I suppose I've been lucky, all this time, that anything worked at all.

So next up: How do I fix the rest of the init scripts / Do I need to fix the rest of the init scripts?

Things like udev are on the list of broken scripts (according to insserv), but udev is obviously functioning because all of my hardware devices are functioning...

---

