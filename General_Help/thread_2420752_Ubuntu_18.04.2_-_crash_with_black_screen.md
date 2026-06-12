---
title: "Ubuntu 18.04.2 - crash with black screen"
date: 2019-06-10
forum: General Help
---

### Post by soufl4ky on 2019-06-10
[COLOR=#1A1A1B][FONT=&amp]Hello everyone,[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I'm new to this forum and Ubuntu and I hope that I can find help here, because I'm starting to get desperate.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Since I'd like to get more into programming with python I decided to install Ubuntu 18.04.2 LTSas a secondary system next to my Windows 10. I have never really worked with a Linux system before so everything is pretty new to me.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][FONT=inherit]I encountered the following problem:[/FONT][/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]After installing the OS, I'd start the updating process and install pip, virtualenv and django as well as visual code studio. Also I'd install some software like Spotify and Skype.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]After a while of using Ubuntu (approx. 10 - 60 minutes) the computer freezes and my screen goes instantly black. It does'nt respond to any input and if there's music running or anything else it'd just stutter for a couple of seconds before going completely silent. The only escape is a hard reset.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]On Windows 10 everything is running fine.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]My specs:[/FONT][/COLOR]
```

Processor    Intel(R) Core(TM) i5-6600K CPU @ 3.50GHz, 3501 Mhz, 4 Core(s), 4 Logical Processor(s)    
BIOS Version/Date    American Megatrends Inc. F2, 7/23/2015    
SMBIOS Version    2.8    
Embedded Controller Version    255.255    
BIOS Mode    UEFI    
BaseBoard Manufacturer    Gigabyte Technology Co., Ltd.    
BaseBoard Product    Z170X-Gaming 5    
BaseBoard Version    x.x    
Platform Role    Mobile    
Secure Boot State    Off    
PCR7 Configuration    Binding Not Possible    
Windows Directory    C:\WINDOWS    
System Directory    C:\WINDOWS\system32    
Boot Device    \Device\HarddiskVolume4    
Locale    Germany    
Hardware Abstraction Layer    Version = "10.0.17763.503"    
User Name    DESKTOP-OS9GLMI\XXX    
Time Zone    W. Europe Daylight Time    
Installed Physical Memory (RAM)    16.0 GB    
Total Physical Memory    16.0 GB    
Available Physical Memory    11.7 GB    
Total Virtual Memory    21.2 GB    
Available Virtual Memory    16.2 GB    
Page File Space    5.25 GB    
Page File    C:\pagefile.sys    
Kernel DMA Protection    Off    
Virtualization-based security    Not enabled    
Device Encryption Support    Reasons for failed automatic device encryption: TPM is not usable, PCR7 binding is not supported, Hardware Security Test Interface failed and device is not InstantGo, Un-allowed DMA capable bus/device(s) detected, TPM is not usable    
Hyper-V - VM Monitor Mode Extensions    Yes    
Hyper-V - Second Level Address Translation Extensions    Yes    
Hyper-V - Virtualization Enabled in Firmware    Yes    
[COLOR=#1A1A1B][FONT=&amp][COLOR=#222222][FONT=Verdana]Hyper-V - Data Execution Protection[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]Yes
[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]```
[COLOR=#1A1A1B][FONT=&amp]SSD 1: 250 GB Samsung EVO 850 (Windows 10)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]SSD 2: 250 GB Samsung EVO 860 (Ubuntu 18.04.2)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]HDD: 1 TB NTFS (used by Windows)[/FONT][/COLOR]

```

[COLOR=#1A1A1B][FONT=&amp]The installation process is as follows:[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I'd unplug both the SSD with Windows and my HDD. Then I'd follow the standard installation process of Ubuntu. I use a bootable 32GB USB stick as installation source. After the installation I'd plug back in my Windows SSD and the HDD and update GRUB.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I already tried:[/FONT][/COLOR]

[LIST]
[*]varying the partition scheme between GPT and MBR. I tried Rufus and LinuxLive USB Creator
[*]not plugging back in the Windows SSD and HDD
[*]starting vscode with disabled gpu acceleration
[*]not installing anything except for the updates
[*]installing "sensors" and checking for a potential overheating issues
[/LIST]
[COLOR=#1A1A1B][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I really hope that somebody can help me with that problem.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thank you in advance!



EDIT[/FONT][/COLOR][COLOR=#1A1A1B]:

Here is the syslog right before the crash[/COLOR][COLOR=#1A1A1B]:
[/COLOR]> Jun 10 15:04:55 pascal systemd[1286]: Starting GNOME Terminal Server...Jun 10 15:04:55 pascal dbus-daemon[1320]: [session uid=1000 pid=1320] Successfully activated service 'org.gnome.Terminal'
Jun 10 15:04:55 pascal systemd[1286]: Started GNOME Terminal Server.
Jun 10 15:04:56 pascal systemd-timesyncd[634]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
Jun 10 15:05:18 pascal systemd[1]: Starting Stop ureadahead data collection...
Jun 10 15:05:18 pascal systemd[1]: Started Stop ureadahead data collection.
Jun 10 15:05:41 pascal gnome-software[2185]: enabled plugins: shell-extensions, packagekit-local, packagekit-refresh, os-release, systemd-updates, packagekit-refine-repos, packagekit-proxy, desktop-categories, packagekit-url-to-app, packagekit-offline, packagekit-upgrade, packagekit, fwupd, ubuntuone, appstream, hardcoded-featured, hardcoded-blacklist, packagekit-refine, hardcoded-popular, odrs, desktop-menu-path, rewrite-resource, modalias, steam, generic-updates, provenance, packagekit-history, snap, icons, provenance-license, key-colors, key-colors-metadata
Jun 10 15:05:41 pascal gnome-software[2185]: disabled plugins: dummy, repos, dpkg, epiphany
Jun 10 15:05:41 pascal dbus-daemon[731]: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.117' (uid=1000 pid=2185 comm="/usr/bin/gnome-software --gapplication-service " label="unconfined")
Jun 10 15:05:41 pascal systemd[1]: Starting Firmware update daemon...
Jun 10 15:05:42 pascal fwupd[2238]: disabling plugin because: failed to startup dell: Firmware updating not supported
Jun 10 15:05:42 pascal fwupd[2238]: disabling plugin because: failed to coldplug amt: ME refused connection
Jun 10 15:05:42 pascal boltd[1104]: power: setting force_power to ON
Jun 10 15:05:42 pascal boltd[1104]: power: guard '2' for 'fwupd' active
Jun 10 15:05:42 pascal fwupd[2238]: disabling plugin because: failed to coldplug synapticsmst: MST firmware updating not supported by OEM
Jun 10 15:05:42 pascal fwupd[2238]: using plugins: dfu, colorhug, upower, udev, csr, nitrokey, wacomhid, ebitdo, unifying, thunderbolt, altos, steelseries, uefi, thunderbolt_power
Jun 10 15:05:42 pascal fwupd[2238]: Daemon ready for requests
Jun 10 15:05:42 pascal PackageKit: get-updates transaction /54_bdadedcb from uid 1000 finished with success after 539ms
Jun 10 15:05:42 pascal dbus-daemon[731]: [system] Successfully activated service 'org.freedesktop.fwupd'
Jun 10 15:05:42 pascal systemd[1]: Started Firmware update daemon.
Jun 10 15:05:42 pascal gnome-software[2185]: Only 0 apps for recent list, hiding
Jun 10 15:05:43 pascal gnome-shell[1461]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.76/org/ayatana/NotificationItem/software_update_available
Jun 10 15:05:43 pascal gnome-shell[1461]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.76/org/ayatana/NotificationItem/livepatch
Jun 10 15:05:43 pascal PackageKit: resolve transaction /55_ccdebcec from uid 1000 finished with success after 365ms
Jun 10 15:05:43 pascal PackageKit: search-file transaction /56_bcdeebdb from uid 1000 finished with success after 592ms
Jun 10 15:05:44 pascal PackageKit: search-file transaction /57_abeecedd from uid 1000 finished with success after 386ms
Jun 10 15:05:44 pascal PackageKit: search-file transaction /58_accbccdb from uid 1000 finished with success after 347ms
Jun 10 15:05:44 pascal PackageKit: search-file transaction /59_ececcddc from uid 1000 finished with success after 397ms
Jun 10 15:05:45 pascal PackageKit: search-file transaction /60_bccabcac from uid 1000 finished with success after 384ms
Jun 10 15:05:45 pascal PackageKit: search-file transaction /61_eacbebad from uid 1000 finished with success after 397ms
Jun 10 15:05:46 pascal PackageKit: search-file transaction /62_aaaaaecc from uid 1000 finished with success after 402ms
Jun 10 15:05:46 pascal PackageKit: search-file transaction /63_aaadacbe from uid 1000 finished with success after 398ms
Jun 10 15:05:46 pascal PackageKit: search-file transaction /64_beaabcdc from uid 1000 finished with success after 378ms
Jun 10 15:05:47 pascal PackageKit: get-details transaction /65_ecccbaba from uid 1000 finished with success after 359ms
Jun 10 15:05:47 pascal gnome-software[2185]: Failed to load snap icon: local snap has no icon
Jun 10 15:06:02 pascal boltd[1104]: power: got event for guard '2' (10)
Jun 10 15:06:02 pascal boltd[1104]: power: guard '2' for 'fwupd' deactivated
Jun 10 15:06:02 pascal boltd[1104]: power: shutdown scheduled (T-20,00s)

Jun 10 15:06:22 pascal boltd[1104]: power: setting force_power to OFF
[COLOR=#1A1A1B]

[/COLOR]

---

### Post by dino99 on 2019-06-10
Before failing into trouble, open a terminal and run 'journalctl -b' to grab warnings (bright line) and errors (red line); that will give you some ideas about the problem.

---

### Post by soufl4ky on 2019-06-10
> **dino99 said:**
> Before failing into trouble, open a terminal and run 'journalctl -b' to grab warnings (bright line) and errors (red line); that will give you some ideas about the problem.

I just did this and here is the output:

```
Jun 10 15:27:08 pascal gnome-shell[1475]: JS WARNING: [/usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com/appIcons.js 1028]: unreachable code after return statement
Jun 10 15:27:08 pascal gnome-session[1338]: gnome-session-binary[1338]: WARNING: App 'spice-vdagent.desktop' exited with code 1
Jun 10 15:27:08 pascal gnome-session-binary[1338]: WARNING: App 'spice-vdagent.desktop' exited with code 1
Jun 10 15:27:08 pascal kernel: rfkill: input handler disabled
Jun 10 15:27:08 pascal gsd-xsettings[1615]: Failed to get current display configuration state: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.Mutter.DisplayConfig" does not exist
Jun 10 15:27:08 pascal gsd-sharing[1604]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Jun 10 15:27:08 pascal gsd-sharing[1604]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Jun 10 15:27:08 pascal gsd-sharing[1604]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Jun 10 15:27:08 pascal gnome-shell[1475]: JS WARNING: [resource:///org/gnome/shell/ui/workspaceThumbnail.js 891]: reference to undefined property "_switchWorkspaceNotifyId"
Jun 10 15:27:08 pascal gsd-color[1136]: failed to set screen _ICC_PROFILE: Failed to open file “/home/pascal/.local/share/icc/edid-ffe8d685f3eb52d7609865c990286909.icc”: Permission denied
Jun 10 15:27:08 pascal gnome-session-binary[1338]: Entering running state
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): EDID vendor "DEL", prod id 41124
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Using hsync ranges from config file
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Using vrefresh ranges from config file
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Printing DDC gathered Modelines:
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
Jun 10 15:27:08 pascal /usr/lib/gdm3/gdm-x-session[1319]: (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
Jun 10 15:27:08 pascal gnome-shell[1475]: Unable to connect to ibus: Could not connect: Connection refused
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Activating service name='org.freedesktop.FileManager1' requested by ':1.57' (uid=1000 pid=1695 comm="nautilus-desktop " label="unconfi
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar7' unit='evolution-calendar-factory.service' requested by
Jun 10 15:27:08 pascal systemd[1301]: Starting Evolution calendar service...
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Successfully activated service 'org.freedesktop.FileManager1'
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Activating service name='ca.desrt.dconf' requested by ':1.57' (uid=1000 pid=1695 comm="nautilus-desktop " label="unconfined")
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Successfully activated service 'ca.desrt.dconf'
Jun 10 15:27:08 pascal gnome-shell[1475]: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.PermissionStore was not provided by any .
Jun 10 15:27:08 pascal gsd-color[1136]: failed to set screen _ICC_PROFILE: Failed to open file “/home/pascal/.local/share/icc/edid-ffe8d685f3eb52d7609865c990286909.icc”: Permission denied
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Successfully activated service 'org.gnome.evolution.dataserver.Calendar7'
Jun 10 15:27:08 pascal systemd[1301]: Started Evolution calendar service.
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook9' unit='evolution-addressbook-factory.service' reques
Jun 10 15:27:08 pascal systemd[1301]: Starting Evolution address book service...
Jun 10 15:27:08 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook9'
Jun 10 15:27:08 pascal systemd[1301]: Started Evolution address book service.
Jun 10 15:27:09 pascal gnome-shell[1475]: GNOME Shell started at Mon Jun 10 2019 15:27:08 GMT+0200 (CEST)
Jun 10 15:27:10 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.67' (uid=1000 pid=1784
Jun 10 15:27:10 pascal systemd[1301]: Starting GNOME Terminal Server...
Jun 10 15:27:10 pascal dbus-daemon[1335]: [session uid=1000 pid=1335] Successfully activated service 'org.gnome.Terminal'
Jun 10 15:27:10 pascal systemd[1301]: Started GNOME Terminal Server.
Jun 10 15:27:24 pascal dbus-daemon[777]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Jun 10 15:27:24 pascal pulseaudio[1506]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeo
Jun 10 15:27:24 pascal boltd[1123]: power: setting force_power to OFF
Jun 10 15:27:25 pascal systemd-timesyncd[707]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
Jun 10 15:27:46 pascal systemd[1]: Starting Stop ureadahead data collection...
Jun 10 15:27:46 pascal systemd[1]: Started Stop ureadahead data collection.
Jun 10 15:28:08 pascal gnome-software[1812]: enabled plugins: shell-extensions, packagekit-local, packagekit-refresh, os-release, systemd-updates, packagekit-refine-repos, packagekit-proxy, desktop-catego
Jun 10 15:28:08 pascal gnome-software[1812]: disabled plugins: dummy, repos, dpkg, epiphany
Jun 10 15:28:09 pascal dbus-daemon[777]: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.119' (uid=1000 pid=1812 comm="/usr/bin/gnome-software -
Jun 10 15:28:09 pascal systemd[1]: Starting Firmware update daemon...
Jun 10 15:28:09 pascal fwupd[1831]: disabling plugin because: failed to startup dell: Firmware updating not supported
Jun 10 15:28:09 pascal fwupd[1831]: disabling plugin because: failed to coldplug amt: ME refused connection
Jun 10 15:28:09 pascal boltd[1123]: power: setting force_power to ON
Jun 10 15:28:09 pascal boltd[1123]: power: guard '2' for 'fwupd' active
Jun 10 15:28:09 pascal fwupd[1831]: disabling plugin because: failed to coldplug synapticsmst: MST firmware updating not supported by OEM
Jun 10 15:28:09 pascal fwupd[1831]: using plugins: dfu, colorhug, upower, udev, csr, nitrokey, wacomhid, ebitdo, unifying, thunderbolt, altos, steelseries, uefi, thunderbolt_power
Jun 10 15:28:09 pascal fwupd[1831]: Daemon ready for requests
Jun 10 15:28:09 pascal PackageKit[1125]: get-updates transaction /90_cebbeecb from uid 1000 finished with success after 509ms
Jun 10 15:28:09 pascal dbus-daemon[777]: [system] Successfully activated service 'org.freedesktop.fwupd'
Jun 10 15:28:09 pascal systemd[1]: Started Firmware update daemon.
Jun 10 15:28:09 pascal gnome-software[1812]: Only 0 apps for recent list, hiding
Jun 10 15:28:10 pascal gnome-shell[1475]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.69/org/ayatana/NotificationItem/software_update_available
Jun 10 15:28:10 pascal gnome-shell[1475]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.69/org/ayatana/NotificationItem/livepatch
Jun 10 15:28:10 pascal PackageKit[1125]: resolve transaction /91_dcdebaba from uid 1000 finished with success after 338ms
Jun 10 15:28:10 pascal PackageKit[1125]: search-file transaction /92_cdebbcaa from uid 1000 finished with success after 566ms
Jun 10 15:28:11 pascal PackageKit[1125]: search-file transaction /93_ecaaeabd from uid 1000 finished with success after 348ms
Jun 10 15:28:11 pascal PackageKit[1125]: search-file transaction /94_beaaeeca from uid 1000 finished with success after 329ms
Jun 10 15:28:11 pascal PackageKit[1125]: search-file transaction /95_eaebeeca from uid 1000 finished with success after 325ms
Jun 10 15:28:12 pascal PackageKit[1125]: search-file transaction /96_dbbbdaba from uid 1000 finished with success after 335ms
Jun 10 15:28:12 pascal PackageKit[1125]: search-file transaction /97_aedbaeed from uid 1000 finished with success after 329ms
Jun 10 15:28:12 pascal PackageKit[1125]: search-file transaction /98_deacaadc from uid 1000 finished with success after 331ms
Jun 10 15:28:13 pascal PackageKit[1125]: search-file transaction /99_abceecbd from uid 1000 finished with success after 327ms
Jun 10 15:28:13 pascal PackageKit[1125]: search-file transaction /100_deecaaee from uid 1000 finished with success after 329ms
Jun 10 15:28:13 pascal PackageKit[1125]: get-details transaction /101_cbcadcee from uid 1000 finished with success after 297ms
Jun 10 15:28:14 pascal gnome-software[1812]: Failed to load snap icon: local snap has no icon
Jun 10 15:28:29 pascal boltd[1123]: power: got event for guard '2' (10)
Jun 10 15:28:29 pascal boltd[1123]: power: guard '2' for 'fwupd' deactivated
Jun 10 15:28:29 pascal boltd[1123]: power: shutdown scheduled (T-20,00s)

```


I was also able to find these lines which are written during the boot process i suppose:
```
Jun 10 15:08:58 pascal systemd[1281]: Starting Virtual filesystem service...
Jun 10 15:08:58 pascal dbus-daemon[1315]: [session uid=1000 pid=1315] Successfully activated service 'org.gtk.vfs.Daemon'
Jun 10 15:08:58 pascal systemd[1281]: Started Virtual filesystem service.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1485 of process 1485 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 1 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 1 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1487 of process 1485 (n/a) owned by '1000' RT at priority 5.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 2 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal pulseaudio[1485]: [pulseaudio] alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0 to 0 which makes no sense.
Jun 10 15:08:58 pascal kernel: [   12.590767] usb 1-5: 2:1: cannot get freq at ep 0x1
Jun 10 15:08:58 pascal pulseaudio[1485]: [pulseaudio] alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0 to 0 which makes no sense.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 2 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1488 of process 1485 (n/a) owned by '1000' RT at priority 5.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 3 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 3 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1489 of process 1485 (n/a) owned by '1000' RT at priority 5.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 4 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 4 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1490 of process 1485 (n/a) owned by '1000' RT at priority 5.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 5 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 5 threads of 1 processes of 2 users.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Successfully made thread 1491 of process 1485 (n/a) owned by '1000' RT at priority 5.
Jun 10 15:08:58 pascal rtkit-daemon[1066]: Supervising 6 threads of 1 processes of 2 users.
Jun 10 15:08:59 pascal dbus-daemon[1315]: [session uid=1000 pid=1315] Activating service name='org.freedesktop.portal.IBus' requested by ':1.25' (uid=1000 pid=1501 comm="ibus-daemon --xim --panel disable " label="unconfined")
Jun 10 15:08:59 pascal dbus-daemon[1315]: [session uid=1000 pid=1315] Successfully activated service 'org.freedesktop.portal.IBus'
Jun 10 15:08:59 pascal dbus-daemon[1315]: [session uid=1000 pid=1315] Activating service name='org.gnome.Shell.CalendarServer' requested by ':1.21' (uid=1000 pid=1454 comm="/usr/bin/gnome-shell " label="unconfined")
Jun 10 15:08:59 pascal dbus-daemon[1315]: [session uid=1000 pid=1315] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution-source-registry.service' requested by ':1.29' (uid=1000 pid=1521 comm="/usr/lib/gnome-shell/gnome-shell-calendar-server " label="unconfined")
Jun 10 15:08:59 pascal systemd[1281]: Starting Evolution source registry...

```

---

