---
title: "Init scripts missing LSB headers; how to restore?"
date: 2014-01-12
forum: General Help
---

### Post by quequotion on 2014-01-12
I've actually posted about this before, when it caused my computer to be unable to shutdown. In that case I got lucky, in that I was able to find proper start and stop runlevels for the shutdown scripts and learn how to fix them by hand.

Today I decided to finally go ahead and do a full distribution upgrade, only insserv won't let it happen and has a million problems with these stripped init scripts. I say *stripped*, because at one time they all had proper headers and they all functioned properly. I can't say exactly when I started to notice this very long list of warnings during upgrade, but it's been going on for a very long time now.

I know *how* to fix this, but I'm lacking information: I need someone to check the init scripts on a *working* (saucy) installation and tell me what the correct start and stop runlevels for these scripts are. Otherwise, what start and stop runlevels would make safe defaults for all of them?

I can't get the information from my own computer and it doesn't seem to be available in any documentation anywhere. ```
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
initctl: Unknown job: console-font
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
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
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
```

---

### Post by ian-weisser on 2014-01-12
> **quequotion said:**
> ```
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: script 'smbd' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: script 'nmbd' missing LSB tags and overrides
```
Hmmm. I don't have those in my saucy, sorry.

> **quequotion said:**
> ```
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'modemmanager' missing LSB tags and overrides
insserv: warning: script 'pulseaudio' missing LSB tags and overrides
initctl: Unknown job: console-font
insserv: warning: script 'network-interface-container' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'alsa-restore' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: script 'udev-fallback-graphics' missing LSB tags and overrides
insserv: warning: script 'passwd' missing LSB tags and overrides
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'lightdm' missing LSB tags and overrides
insserv: warning: script 'whoopsie' missing LSB tags and overrides
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: warning: script 'alsa-store' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: script 'irqbalance' missing LSB tags and overrides'
```

These init scripts were not "stripped." They were replaced by Upstart jobs in /etc/init.
Are you saying that these warnings are preventing a dist-upgrade? Mere warnings shouldn't prevent upgrade.

---

### Post by quequotion on 2014-01-12
> **ian-weisser said:**
> These init scripts were not "stripped." They were replaced by Upstart jobs in /etc/init.
Are you saying that these warnings are preventing a dist-upgrade? Mere warnings shouldn't prevent upgrade.

Then what happened to the LSB headers they used to have? Those should NOT be removed, even if the job was converted to upstart. My entire init system is in pieces and insserv won't allow me to upgrade because of several initscript conflicts and failures.

example:

dbus is one of the scripts missing a LSB header; blueman would not upgrade because dbus failed to "reload"```
Setting up blueman (1.23+update1-2ubuntu1) ...
reload: Not running
invoke-rc.d: initscript dbus, action "reload" failed.
dpkg: error processing blueman (--configure):
 subprocess installed post-installation script returned error exit status 1
```dbus *is* running but the "reload" action is invalid; i even tried adding it to the initscript by hand but that wouldn't satisfy insserv. Temporary and nonviable solution: remove blueman (*bluetooth now unusable*)

The further I get into the installation the more things like this are coming up. I can't say how many problems there will be in total.

I also have a lot of problems with insserv related to scripts that aren't in the list of stripped ones, for which I will make other threads.

---

### Post by quequotion on 2014-01-13
What I really need is to know what the header for each of those scripts looks like on a working system. That is how this problem gets fixed. It doesn't matter what's going on with upstart at all.

---

### Post by quequotion on 2014-06-12
Well, there was never going to be a solution to this problem because it is caused by the existence of upstart.

Resolved by switching to Archlinux, which uses systemd instead. It may not be perfect, but it's a lot better.

---

