---
title: "tips for stablizing/locking down (L)ubuntu for public exhibit/kiosk use?"
date: 2022-11-26
forum: General Help
---

### Post by clepsdyrae on 2022-11-26
Hi -- I'm setting up a system that will be used for a museum exhibit: slideshow, some AV stuff, etc.

I installed Lubuntu 22.04. I've done some obvious stuff, but I want this to be as stable, predictable, and non-changing as possible, and I wonder if I have overlooked anything.

I want to avoid anything ever happening besides the scripts that are autostarting. E.g. I don't want a dialog popping up saying "you haven't cleaned up your Documents folder in a while", or "reminder: don't forget to X", or "new wireless network found", etc etc. I know that linux, and Lubuntu/LXDE specifically, is pretty good about that kind of thing, but I want to make sure I cover as many bases as possible.

**Importantly**, I also want to disable any background tasks that might cause real-time performance to suffer at random times. Part of this exhibit will be recording audio through an interface, and I don't want audio dropouts or hiccups, etc.

Security is not a concern -- it won't be networked and there is nothing important on it or direct user interaction with it.

Here's what I have done so far:

- disabled "idleness watcher" in power management, hibernation after X minutes, etc.
- disabled "Notification Daemon" in session settings
- disabled the screen saver
- in session autostarts, disabled AT-SPI D-Bus Bus, Geoclue Demo agent, Print Queue Applet, PulseAudio Sound System, upgNotifier, User folders update, Qlipper, XScreenSaver
- a custom autostart script disables the screensaver "like actually for real this time" using xset
- disabled checking for updates or distribution releases
- when development is complete I will also disable the network management applet

I'm tempted to remove the package apt-xapian-index as well. Thoughts on that? (I don't need muon, etc., just apt.)

Here what's in cron:

```
$ sudo find . -type f | grep cron
./pam.d/cron
./cron.weekly/0anacron
./cron.weekly/man-db
./cron.weekly/apt-xapian-index
./cron.weekly/.placeholder
./default/anacron
./default/cron
./init.d/anacron
./init.d/cron
./cron.monthly/0anacron
./cron.monthly/.placeholder
./cron.d/anacron
./cron.d/e2scrub_all
./cron.d/.placeholder
./cron.daily/0anacron
./cron.daily/logrotate
./cron.daily/man-db
./cron.daily/cracklib-runtime
./cron.daily/apt-compat
./cron.daily/dpkg
./cron.daily/apport
./cron.daily/.placeholder
./anacrontab
./crontab
./cron.hourly/.placeholder

```

...seems like log rotation and dpkg updates are unlikely to hurt anything... any thoughts on those or any of the other cron jobs?

systemd timers:

```
$ systemctl list-timers --all
NEXT                        LEFT           LAST                        PASSED       UNIT                           ACTIVATES
Sat 2022-11-26 14:30:53 PST 53min left     Sat 2022-11-26 13:34:41 PST 2min 59s ago anacron.timer                  anacron.service
Sat 2022-11-26 14:45:19 PST 1h 7min left   Thu 2022-11-24 13:17:38 PST 2 days ago   man-db.timer                   man-db.service
Sat 2022-11-26 15:28:49 PST 1h 51min left  Thu 2022-11-24 13:17:38 PST 2 days ago   apt-daily.timer                apt-daily.service
Sat 2022-11-26 16:15:57 PST 2h 38min left  Fri 2022-11-25 19:02:49 PST 18h ago      fwupd-refresh.timer            fwupd-refresh.service
Sat 2022-11-26 18:50:34 PST 5h 12min left  Sat 2022-11-26 12:00:00 PST 1h 37min ago ua-timer.timer                 ua-timer.service
Sun 2022-11-27 00:00:00 PST 10h left       n/a                         n/a          dpkg-db-backup.timer           dpkg-db-backup.service
Sun 2022-11-27 00:00:00 PST 10h left       Sat 2022-11-26 10:59:21 PST 2h 38min ago logrotate.timer                logrotate.service
Sun 2022-11-27 03:10:24 PST 13h left       Thu 2022-11-24 13:17:38 PST 2 days ago   e2scrub_all.timer              e2scrub_all.service
Sun 2022-11-27 06:11:53 PST 16h left       Sat 2022-11-26 11:33:42 PST 2h 3min ago  apt-daily-upgrade.timer        apt-daily-upgrade.service
Sun 2022-11-27 10:32:17 PST 20h left       Sat 2022-11-26 12:09:21 PST 1h 28min ago motd-news.timer                motd-news.service
Sun 2022-11-27 11:04:19 PST 21h left       Sat 2022-11-26 11:04:19 PST 2h 33min ago update-notifier-download.timer update-notifier-download.service
Sun 2022-11-27 11:14:21 PST 21h left       Sat 2022-11-26 11:14:21 PST 2h 23min ago systemd-tmpfiles-clean.timer   systemd-tmpfiles-clean.service
Mon 2022-11-28 00:32:09 PST 1 day 10h left Thu 2022-11-24 13:17:38 PST 2 days ago   fstrim.timer                   fstrim.service
Mon 2022-11-28 23:41:15 PST 2 days left    Thu 2022-11-24 13:17:44 PST 2 days ago   update-notifier-motd.timer     update-notifier-motd.service
n/a                         n/a            n/a                         n/a          apport-autoreport.timer        apport-autoreport.service
n/a                         n/a            n/a                         n/a          snapd.snap-repair.timer        snapd.snap-repair.service

```

...seems like I could disable a great many of those, no? I'm especially concerned about snap: I don't want it to be upgrading firefox or whatever in the background. Is there a risk of that?

Thanks for any tips!

EDIT: here are the services as well:

```
$ systemctl list-units --type=service
  UNIT                                                  LOAD   ACTIVE SUB     DESCRIPTION
  accounts-daemon.service                               loaded active running Accounts Service
  acpid.service                                         loaded active running ACPI event daemon
  alsa-restore.service                                  loaded active exited  Save/Restore Sound Card State
  apparmor.service                                      loaded active exited  Load AppArmor profiles
  apport.service                                        loaded active exited  LSB: automatic crash report generation
  avahi-daemon.service                                  loaded active running Avahi mDNS/DNS-SD Stack
  blk-availability.service                              loaded active exited  Availability of block devices
  bluetooth.service                                     loaded active running Bluetooth service
  console-setup.service                                 loaded active exited  Set console font and keymap
  cron.service                                          loaded active running Regular background program processing daemon
  cups-browsed.service                                  loaded active running Make remote CUPS printers available locally
  cups.service                                          loaded active running CUPS Scheduler
  dbus.service                                          loaded active running D-Bus System Message Bus
&#9679; fwupd-refresh.service                                 loaded failed failed  Refresh fwupd metadata and update motd
  haveged.service                                       loaded active running Entropy Daemon based on the HAVEGE algorithm
  irqbalance.service                                    loaded active running irqbalance daemon
  kerneloops.service                                    loaded active running Tool to automatically collect and submit kernel crash signatures
  keyboard-setup.service                                loaded active exited  Set the console keyboard layout
  kmod-static-nodes.service                             loaded active exited  Create List of Static Device Nodes
  lvm2-monitor.service                                  loaded active exited  Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling
  ModemManager.service                                  loaded active running Modem Manager
  networkd-dispatcher.service                           loaded active running Dispatcher daemon for systemd-networkd
  NetworkManager-wait-online.service                    loaded active exited  Network Manager Wait Online
  NetworkManager.service                                loaded active running Network Manager
  plymouth-quit.service                                 loaded active exited  Terminate Plymouth Boot Screen
  plymouth-read-write.service                           loaded active exited  Tell Plymouth To Write Out Runtime Data
  plymouth-start.service                                loaded active exited  Show Plymouth Boot Screen
  polkit.service                                        loaded active running Authorization Manager
  rsyslog.service                                       loaded active running System Logging Service
  rtkit-daemon.service                                  loaded active running RealtimeKit Scheduling Policy Service
  sddm.service                                          loaded active running Simple Desktop Display Manager
  setvtrgb.service                                      loaded active exited  Set console scheme
  snapd.apparmor.service                                loaded active exited  Load AppArmor profiles managed internally by snapd
  snapd.seeded.service                                  loaded active exited  Wait until snapd is fully seeded
  snapd.service                                         loaded active running Snap Daemon
  ssh.service                                           loaded active running OpenBSD Secure Shell server
  [EMAIL="systemd-fsck@dev-disk-by\x2duuid-DD0D\x2d1907.servic"]systemd-fsck@dev-disk-by\x2duuid-DD0D\x2d1907.servic[/EMAIL]e loaded active exited  File System Check on /dev/disk/by-uuid/DD0D-1907
  systemd-journal-flush.service                         loaded active exited  Flush Journal to Persistent Storage
  systemd-journald.service                              loaded active running Journal Service
  systemd-logind.service                                loaded active running User Login Management
  systemd-modules-load.service                          loaded active exited  Load Kernel Modules
  systemd-random-seed.service                           loaded active exited  Load/Save Random Seed
  systemd-remount-fs.service                            loaded active exited  Remount Root and Kernel File Systems
  systemd-resolved.service                              loaded active running Network Name Resolution
  systemd-sysctl.service                                loaded active exited  Apply Kernel Variables
  systemd-sysusers.service                              loaded active exited  Create System Users
  systemd-timesyncd.service                             loaded active running Network Time Synchronization
  systemd-tmpfiles-setup-dev.service                    loaded active exited  Create Static Device Nodes in /dev
  systemd-tmpfiles-setup.service                        loaded active exited  Create Volatile Files and Directories
  systemd-udev-trigger.service                          loaded active exited  Coldplug All udev Devices
  systemd-udevd.service                                 loaded active running Rule-based Manager for Device Events and Files
  systemd-update-utmp.service                           loaded active exited  Record System Boot/Shutdown in UTMP
  systemd-user-sessions.service                         loaded active exited  Permit User Sessions
  thermald.service                                      loaded active running Thermal Daemon Service
  udisks2.service                                       loaded active running Disk Manager
  ufw.service                                           loaded active exited  Uncomplicated firewall
  unattended-upgrades.service                           loaded active running Unattended Upgrades Shutdown
  upower.service                                        loaded active running Daemon for power management
  [EMAIL="user-runtime-dir@1000.servic"]user-runtime-dir@1000.servic[/EMAIL]e                         loaded active exited  User Runtime Directory /run/user/1000
  [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e                                     loaded active running User Manager for UID 1000
  wpa_supplicant.service                                loaded active running WPA supplicant
```

---

### Post by clepsdyrae on 2022-11-26
Update: I've now also done this:

```
sudo systemctl stop ua-timer.timer
sudo systemctl mask ua-timer.timer
sudo systemctl stop avahi-daemon.service
sudo systemctl mask avahi-daemon.service
sudo systemctl stop bluetooth.service
sudo systemctl mask bluetooth.service
sudo systemctl stop cups-browsed.service
sudo systemctl mask cups-browsed.service
sudo systemctl stop cups.service
sudo systemctl mask cups.service
```

...still have my eye on snap and xapian...

Update 2: removed snap/firefox/etc.

Update 3: disabled a ton of services... current list of timers:

```
$ sudo systemctl list-timers --all
[sudo] password for tp: 
NEXT                        LEFT          LAST                        PASSED       UNIT                           ACTIVATES                     
Sat 2022-11-26 15:24:04 PST 14min left    n/a                         n/a          systemd-tmpfiles-clean.timer   systemd-tmpfiles-clean.service
Sat 2022-11-26 15:33:27 PST 23min left    Sat 2022-11-26 14:34:24 PST 35min ago    anacron.timer                  anacron.service
Sun 2022-11-27 00:00:00 PST 8h left       Sat 2022-11-26 10:59:21 PST 4h 10min ago logrotate.timer                logrotate.service
Sun 2022-11-27 03:10:07 PST 12h left      Thu 2022-11-24 13:17:38 PST 2 days ago   e2scrub_all.timer              e2scrub_all.service
Sun 2022-11-27 04:54:52 PST 13h left      Sat 2022-11-26 14:01:12 PST 1h 8min ago  fwupd-refresh.timer            fwupd-refresh.service
Mon 2022-11-28 00:32:51 PST 1 day 9h left Thu 2022-11-24 13:17:38 PST 2 days ago   fstrim.timer                   fstrim.service
n/a                         n/a           n/a                         n/a          apport-autoreport.timer        
n/a                         n/a           n/a                         n/a          apt-daily-upgrade.timer        
n/a                         n/a           n/a                         n/a          apt-daily.timer                
n/a                         n/a           n/a                         n/a          dpkg-db-backup.timer           
n/a                         n/a           n/a                         n/a          man-db.timer                   
n/a                         n/a           n/a                         n/a          motd-news.timer                
n/a                         n/a           n/a                         n/a          ua-timer.timer                 
n/a                         n/a           n/a                         n/a          update-notifier-download.timer 
n/a                         n/a           n/a                         n/a          update-notifier-motd.timer
```

Current list of services:

```
$ sudo systemctl list-units --type=service
  UNIT                                                  LOAD   ACTIVE SUB     DESCRIPTION
  accounts-daemon.service                               loaded active running Accounts Service
  acpid.service                                         loaded active running ACPI event daemon
  alsa-restore.service                                  loaded active exited  Save/Restore Sound Card State
  apparmor.service                                      loaded active exited  Load AppArmor profiles
  blk-availability.service                              loaded active exited  Availability of block devices
  console-setup.service                                 loaded active exited  Set console font and keymap
  cron.service                                          loaded active running Regular background program processing daemon
  dbus.service                                          loaded active running D-Bus System Message Bus
  haveged.service                                       loaded active running Entropy Daemon based on the HAVEGE algorithm
  irqbalance.service                                    loaded active running irqbalance daemon
  kerneloops.service                                    loaded active running Tool to automatically collect and submit kernel crash signatures
  keyboard-setup.service                                loaded active exited  Set the console keyboard layout
  kmod-static-nodes.service                             loaded active exited  Create List of Static Device Nodes
  lvm2-monitor.service                                  loaded active exited  Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling
  ModemManager.service                                  loaded active running Modem Manager
  networkd-dispatcher.service                           loaded active running Dispatcher daemon for systemd-networkd
  NetworkManager.service                                loaded active running Network Manager
  plymouth-quit.service                                 loaded active exited  Terminate Plymouth Boot Screen
  plymouth-read-write.service                           loaded active exited  Tell Plymouth To Write Out Runtime Data
  plymouth-start.service                                loaded active exited  Show Plymouth Boot Screen
  polkit.service                                        loaded active running Authorization Manager
  rsyslog.service                                       loaded active running System Logging Service
  rtkit-daemon.service                                  loaded active running RealtimeKit Scheduling Policy Service
  sddm.service                                          loaded active running Simple Desktop Display Manager
  setvtrgb.service                                      loaded active exited  Set console scheme
  ssh.service                                           loaded active running OpenBSD Secure Shell server
  systemd-fsck@dev-disk-by\x2duuid-DD0D\x2d1907.service loaded active exited  File System Check on /dev/disk/by-uuid/DD0D-1907
  systemd-journal-flush.service                         loaded active exited  Flush Journal to Persistent Storage
  systemd-journald.service                              loaded active running Journal Service
  systemd-logind.service                                loaded active running User Login Management
  systemd-modules-load.service                          loaded active exited  Load Kernel Modules
  systemd-random-seed.service                           loaded active exited  Load/Save Random Seed
  systemd-remount-fs.service                            loaded active exited  Remount Root and Kernel File Systems
  systemd-resolved.service                              loaded active running Network Name Resolution
  systemd-sysctl.service                                loaded active exited  Apply Kernel Variables
  systemd-sysusers.service                              loaded active exited  Create System Users
  systemd-timesyncd.service                             loaded active running Network Time Synchronization
  systemd-tmpfiles-setup-dev.service                    loaded active exited  Create Static Device Nodes in /dev
  systemd-tmpfiles-setup.service                        loaded active exited  Create Volatile Files and Directories
  systemd-udev-trigger.service                          loaded active exited  Coldplug All udev Devices
  systemd-udevd.service                                 loaded active running Rule-based Manager for Device Events and Files
  systemd-update-utmp.service                           loaded active exited  Record System Boot/Shutdown in UTMP
  systemd-user-sessions.service                         loaded active exited  Permit User Sessions
  thermald.service                                      loaded active running Thermal Daemon Service
  udisks2.service                                       loaded active running Disk Manager
  ufw.service                                           loaded active exited  Uncomplicated firewall
  unattended-upgrades.service                           loaded active running Unattended Upgrades Shutdown
  upower.service                                        loaded active running Daemon for power management
  user-runtime-dir@1000.service                         loaded active exited  User Runtime Directory /run/user/1000
  user@1000.service                                     loaded active running User Manager for UID 1000
  wpa_supplicant.service                                loaded active running WPA supplicant
```

...that's starting to feel better. Also disabled the xapian cron script.

If there's anything I'm still missing, I'm all ears!

---

### Post by ne29914 on 2022-11-26
Did you check the shortcut keys?

---

### Post by ian-weisser on 2022-11-26
Consider looking into Ubuntu Frame ([https://snapcraft.io/ubuntu-frame](https://snapcraft.io/ubuntu-frame)) which is intended for this sort of use.

As a Snap, you can install it over Ubuntu Core, and dispense with a lot of your concerns.

---

### Post by guiverc on 2022-11-26
Lubuntu uses **LXQt** and not LXDE.

Lubuntu 18.04 LTS was the last release using LXDE, with releases starting with Lubuntu 18.10 being a new system with much of the software stack changed. Yes the Ubuntu base is the same, as is the use of `openbox` as WM, but *deprecated *GTK2 & LXDE were replaced with their replacements of Qt5 & LXQt  (*given the GTK3 port was abandoned upstream** as deemed heavy, with LXDE devs joining with Razor-Qt devs creating the newer replacement  LXQt* *long ago now*).

I'd have just stopped the lubuntu-update-notifier  ([https://packages.ubuntu.com/source/focal/lubuntu-update-notifier](https://packages.ubuntu.com/source/focal/lubuntu-update-notifier)) as documented in the manual ([https://manual.lubuntu.me/lts/3/3.2/3.2.13/session_settings.html](https://manual.lubuntu.me/lts/3/3.2/3.2.13/session_settings.html))

(In the long-gone past I've also disabled Ctrl-Alt combinations so people couldn't jump to text terminal & walk away, maybe even consider disabling the SysRq key combinations; though removing them also removes your ability to use it to shutdown/restart quickly etc - your decision.  Also note I only scanned your detail & may have missed you doing this)

---

### Post by clepsdyrae on 2022-11-26
Thanks! I'll check out Frame -- that does indeed look applicable and was the kind of thing I was looking for (but didn't have the search terms right).

Re: keyboard shortcuts, etc: there is no keyboard or mouse associated, so that's not a concern. The interactivity is provided through buttons/sensors via an Arduino running Telemetrix (at least that's the current approach... might change...)

Re: LXQt -- thanks -- I had read that but forgot.

---

### Post by HermanAB on 2022-11-28
I haven’t checked your list… Don’t forget to disable USB and SD card automount/execute functions.

You could also be evil and immediately erase anything plugged into the machine, or just put a glob of hot glue into every socket.

---

### Post by clepsdyrae on 2022-11-28
Thanks --

I've had some scripts running on it watching CPU usage, and the main offender at this point is the "pool-udisksd" process that takes 50% of a core every so often. Seems to run about every 10m... or at least today it's always at X:X6 (1:16, 4:36, etc.) I haven't yet tracked down what is triggering it... if anyone knows, that'd be great to find out. Perhaps the desktop file manager or other DE process is checking something on a loop?

---

### Post by TheFu on 2022-11-28
I'd purge snapd and anything related to snaps, since those will attempt to get updates 4x a day.
I'd setup a restricted shell for the normal kiosk userid and replace the normal menu with a custom menu that you create too.
Ensure there's no way to get to a shell using any of the programs you'll leave on the system. Same for terminals - don't allow any of them to be run.  You might want to prevent the F1-F12 keys from being pressed too.  I can do all sorts of fun things with access to those on almost any Linux system.

---

### Post by clepsdyrae on 2022-11-28
Thanks, yeah, snap is gone entirely at this point. And there's no keyboard/mouse or computer access for this machine, just the display will be visible.

Progress on the udisksd thing: correlating with the CPU usage is this message on the system dbus:

```
 signal time=1669672611.332288 sender=:1.5 -> destination=(null destination) serial=165 path=/org/freedesktop/UDisks2/drives/TS128GMTS952T_G997275120; interface=org.freedesktop.DBus.Properties; member=PropertiesChanged
   string "org.freedesktop.UDisks2.Drive.Ata"
   array [
      dict entry(
         string "SmartPowerOnSeconds"
         variant             uint64 291600
      )
      dict entry(
         string "SmartUpdated"
         variant             uint64 1669672611
      )
   ]
```

...so it seems that udisk is sending and/or receiving (?) a message every 10 minutes that the SSD SMART value SmartPowerOnSeconds has changed...

So I installed smartmontools, disbaled the smartmontools.service (which restarts SMART reporting now and then), and ran "smartctl -s off /dev/sda" in an effort to turn off smart reporting, to see if that would help.

 smartctl indeed turns off reporting for a while, but some other part of the system is turning it back on, and so the periodic CPU and dbus messages are still happening... any ideas on what's going on or how to stop it?

There's no way to turn of SMART in bios on this machine, unfortunately. (I know SMART is smart, I just don't want it running without me in control of when...)

---

### Post by TheFu on 2022-11-28
You don't need udisksd if you use the fstab or manually mount storage.
If you don't use a file manager to click USB flash storage to create a pseudo-mount (it isn't a real mount), then you don't need it at all.  Autofs can be configured to mount specific USB flash storage by UUID or LABEL, if you need that stuff.  Just use a unique label that nobody would guess to pull stuff off the system.

If there's no keyboard, most browsers have a kiosk mode that won't let them out of kiosk mode.

---

### Post by clepsdyrae on 2022-11-29
Thanks for that tip! -- I'm trying to get autofs going and am having some trouble. I actually want any USB plugged in (any UUID, etc) to get automounted at a specified dir (I'm aware it's risky). I have:

/etc/auto.master:
```
/mydir /etc/auto.mydir
+dir:/etc/auto.master.d
+auto.master
```
(the last two lines are just what was in the file already... I edited out the comments for brevity...)

/etc/auto.mydir:
```
 mydrive   -fstype=auto  :/dev/sdb1
```
...I tried without the -fstype option (which I understand to be optional) but same thing.

After reloading autofs and plugging in a USB drive (which comes up as /dev/sdb1), I see:
```
$ ls /mydir
$ mount | grep mydir
/etc/auto.mydir on /mydir type autofs (rw,relatime,fd=6,pgrp=1715,timeout=300,minproto=5,maxproto=5,indirect,pipe_ino=33253)
```

...but "ls /mydir" is empty... Anything obviously dumb that I'm doing? I did create /mydir ahead of time, but my understanding is that it doesn't matter if you do or not. Scratching my head here... seems pretty straightforward but it's not working...

---

### Post by TheFu on 2022-11-29
Don't use /dev/sdb1 in any mounts.  It is asking for problems, since the device name assigned isn't guaranteed.  Use the UUID or LABEL. If those cannot be used, then I think you need to use the crap that is gvfs and deal with the bad options. Sigh.

The power to mount is the power to destroy. Never forget that.

---

### Post by ActionParsnip on 2022-11-29
[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-moved](https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-moved)

---

### Post by clepsdyrae on 2022-11-29
Ah right, I forgot fstab can automount at boot based on label... maybe that's the better way. Still I wonder why the autofs didn't work... I followed their examples exactly... anyway, thanks!

ActionParsnip -- thanks for that link.

---

### Post by TheFu on 2022-11-29
> **clepsdyrae said:**
> Ah right, I forgot fstab can automount at boot based on label... maybe that's the better way. Still I wonder why the autofs didn't work... I followed their examples exactly... anyway, thanks!

ActionParsnip -- thanks for that link.

I use autofs daily, constantly.  In my auto.nfs file, 
```
/TV   -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/TV
```

And the line in the auto.master:
```
/-      /etc/auto.nfs
```

If I wanted to use a GUI to force the mount, I'd make that:
```
/-      /etc/auto.nfs  --timeout=60 --ghost 
```
so the directories are there before any mount happens.

Ooops. You are mounting local storage .... examples for that:
/etc/auto.master:
```
/-     /etc/auto.misc --timeout=60 --ghost
```

and
```
/misc/250G    -nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002    LABEL=250G
```

Sorry, confused an NFS + autofs thread with yours.

---

### Post by clepsdyrae on 2022-11-29
Thanks! That's helpful.

---

### Post by clepsdyrae on 2022-11-30
Is there any reason the assorted GVFS services should be running? (As a reminder, this system won't be using any standard desktop software, or dynamically mounting drives or other hardware, etc, just running a script of its own.) There will be some hardware plugged in via USB (audio interface, arduino, etc, but no storage devices except a USB key that will be plugged in before booting and mounted via fstab).

Reading about it, it doesn't seem like any of its features are useful to me, but if I suddenly can't do some basic task like mount an external drive (CLI is fine) that would be good to know first. :-)

```
 $ systemctl --user | grep gvfs
  run-user-1000-gvfs.mount                                                                 loaded active mounted   /run/user/1000/gvfs
  gvfs-afc-volume-monitor.service                                                          loaded active running   Virtual filesystem service - Apple File Conduit monitor
  gvfs-daemon.service                                                                      loaded active running   Virtual filesystem service
  gvfs-goa-volume-monitor.service                                                          loaded active running   Virtual filesystem service - GNOME Online Accounts monitor
  gvfs-gphoto2-volume-monitor.service                                                      loaded active running   Virtual filesystem service - digital camera monitor
  gvfs-mtp-volume-monitor.service                                                          loaded active running   Virtual filesystem service - Media Transfer Protocol monitor
  gvfs-udisks2-volume-monitor.service                                                      loaded active running   Virtual filesystem service - disk device monitor

```

---

### Post by TheFu on 2022-11-30
> **clepsdyrae said:**
> Is there any reason the assorted GVFS services should be running?  

I can't answer that since we all have different expectations.  Try it. See what does and doesn't work in the way you want.
DEs can be flaky.  If you don't use any DE (why would you for a kioks setup?), then you can have less junk code running and more control using a pure WM setup.  Over the decades, I've used WM-only setups and DEs. I'm back to WM-only again the last 2-3 yrs to stop a number of things I didn't want.  Of course, there's no GUI to setup the stuff you do want, so be prepared to edit text files and restart the WM directly.  I've used openbox for a few years in this way, but I'm back to my beloved fvwm again after a long time away.

---

### Post by clepsdyrae on 2022-11-30
Thanks, I'm slowly learning where the lines between the window manager, DE, etc. are. At this point I have the lxqt-desktop and -panel stopped and just a blank screen with a mouse pointer. So far so good.

I guess what I'm really asking is "does GVFS do anything that a kiosk-type latchkey install might need". When I try to look this kind of stuff up, the descriptions I find are so vague as to be hard to understand. E.g. udisks2 is "used to query and manipulate storage devices", which sounds like a crucial part of the kernel, but nope, totally expendable. GVFS is similar, in that its basic descriptions are hard to parse for a beginner... "GVFS is [GNOME]("https://en.wikipedia.org/wiki/GNOME")'s userspace [virtual filesystem]("https://en.wikipedia.org/wiki/Virtual_filesystem") designed to work with the I/O abstraction of [GIO]("https://en.wikipedia.org/wiki/GIO_(software)"), a library available in [GLib]("https://en.wikipedia.org/wiki/GLib") since version 2.15.1. It installs several modules that are automatically used by applications using the APIs of libgio." ...yeah, still no idea what it actually does, so it'll take me another week to decode all of that. :-)

I'll try disabling or uninstalling. I'm just afraid of bricking the system and not having an easy path back to where it is now. Maybe it's time to start imaging the partition.

---

### Post by TheFu on 2022-11-30
Anything with "gnome" in it is optional, unless the distro specifically made it mandatory.

Lubuntu 20.04 and later uses the Qt framework (kde), not GTK+ (gnome), so it is most definitely optional.  Worst case, something in the GUI doesn't work and you can ssh into the system from another box and re-enable it from the shell.

I used Lubuntu for a few years - 10.04 - 14.04, I think. Then I did openbox, then Mate and finally I'm back to fvwm.  What does this all mean?  
a) I don't know much about Lubuntu that is current.
b) I don't worry about the GUI much.  The GUI is just a program, usually bloated, and 100% optional.

---

### Post by clepsdyrae on 2022-12-01
Uninstalled! Thanks, I'll see how it goes.

Seems like a window-manager-only setup is definitely how I should have started this (or one of the kiosk frameworks). Lesson learned. When you build such a system, are you using pre-built WM-only distros (recommend any?) or are you building it up yourself from a server-only distro?

---

### Post by TheFu on 2022-12-01
If it were me, I wouldn't use Ubuntu. I'd use tiny core with only the software specifically needed, nothing else.  Why have 8G of possible bugs when 32MB will do the job?  Less is more when the public is involved.  Don't put anything extra on the system.

---

### Post by ActionParsnip on 2022-12-01
Indeed. I use Chrome browser and a terminal in my Ubuntu install. I use the minimal install then install openbox and the apps I need. Super trim. Very fast

---

### Post by clepsdyrae on 2022-12-01
Yeah totally agreed; I know 95% of what comes with an *ubuntu distro I'm not wanting, I just don't know anything about configuring bare bones systems to have X or Wayland or whatever is needed to enable the graphical stuff, so I always end up with one of the kid glove distributions and then try to tame it. So when you say you start with a "tiny core" what exactly are you reaching for when you start putting a system like that together? E.g. a WM-only distro?

---

### Post by tea for one on 2022-12-01
Just offering information rather than a solution:-
[https://porteus-kiosk.org/](https://porteus-kiosk.org/)

---

### Post by clepsdyrae on 2022-12-01
> **ActionParsnip said:**
> I use the minimal install then install openbox and the apps I need. Super trim. Very fast

Good to know it's that simple... somehow I got into my head that getting a server-style minimal install and trying to get X going on it, as well as setting up stuff like alsa, etc, was an eldritch nightmare that could only be attempted by trained sysadmins. Guess I need to reassess that presumption. :-)

---

### Post by TheFu on 2022-12-02
> **clepsdyrae said:**
> Yeah totally agreed; I know 95% of what comes with an *ubuntu distro I'm not wanting, I just don't know anything about configuring bare bones systems to have X or Wayland or whatever is needed to enable the graphical stuff, so I always end up with one of the kid glove distributions and then try to tame it. So when you say you start with a "tiny core" what exactly are you reaching for when you start putting a system like that together? E.g. a WM-only distro?

They have different levels of bloat in the three TinyCore distros. Pick the smallest with a GUI.  I think it should be 21MB or so. 
[http://www.tinycorelinux.net/downloads.html](http://www.tinycorelinux.net/downloads.html)

---

### Post by ian-weisser on 2022-12-02
> **clepsdyrae said:**
> Yeah totally agreed; I know 95% of what comes with an *ubuntu distro I'm not wanting, I just don't know anything about configuring bare bones systems to have X or Wayland or whatever is needed to enable the graphical stuff.

This is precisely the use case for Ubuntu Core (bare bones) with Ubuntu Frame snap (locked down GUI designed for kiosks)

Here's a step-by-step for any release of Ubuntu (including Server and Core): [https://discourse.ubuntu.com/t/run-ubuntu-frame-on-your-device/29377](https://discourse.ubuntu.com/t/run-ubuntu-frame-on-your-device/29377). There are very few steps.

---

### Post by TheFu on 2022-12-02
> **ian-weisser said:**
> This is precisely the use case for Ubuntu Core (bare bones) with Ubuntu Frame snap (locked down GUI designed for kiosks)

Here's a step-by-step for any release of Ubuntu (including Server and Core): [https://discourse.ubuntu.com/t/run-ubuntu-frame-on-your-device/29377](https://discourse.ubuntu.com/t/run-ubuntu-frame-on-your-device/29377). There are very few steps.

Did Ubuntu remove the mandated SSO to do anything related to "Core"?  That was the main reason I've avoided it. Why should updating software that I packaged for internal use only need Canonical in the middle of the logins and updates?

[https://ubuntu.com/core/docs/using-ubuntu-core](https://ubuntu.com/core/docs/using-ubuntu-core) still says that the Canonical SSO login is needed.

---

### Post by ian-weisser on 2022-12-02
> **TheFu said:**
> Did Ubuntu remove the mandated SSO to do anything related to "Core"?  That was the main reason I've avoided it. Why should updating software that I packaged for internal use only need Canonical in the middle of the logins and updates?

FUD control: SSO is used ONLY to populate the ssh key onto the new system during the  first boot. SSO is never used (nor accessed) again by the installed  Ubuntu Core system. Canonical is not "in the middle" of logins. Snap updates do not use SSO. Yes, Canonical servers host Snap updates...just like they host Apt updates.

In this case, Ubuntu Core + Ubuntu Frame is one solution (among many) that solves a lot of the OP's described problems. It's already bare bones. It requires very little configuration....and most of that configuration is handled by the snap automatically. Sandboxed. Secure. 100% automatic updates (who remembers to manually update blinky boxes that are hidden away?). Completely open source software. Active development.

And it's quite easy and safe to try. Maybe the OP will like it. Maybe they won't. Test it, kick the tires, and find out.

---

### Post by TheFu on 2022-12-02
> **ian-weisser said:**
> FUD control: SSO is used ONLY to populate the ssh key onto the new system during the  first boot. SSO is never used (nor accessed) again by the installed  Ubuntu Core system. Canonical is not "in the middle" of logins. Snap updates do not use SSO. Yes, Canonical servers host Snap updates...just like they host Apt updates.

In this case, Ubuntu Core + Ubuntu Frame is one solution (among many) that solves a lot of the OP's described problems. It's already bare bones. It requires very little configuration....and most of that configuration is handled by the snap automatically. Sandboxed. Secure. 100% automatic updates (who remembers to manually update blinky boxes that are hidden away?). Completely open source software. Active development.

And it's quite easy and safe to try. Maybe the OP will like it. Maybe they won't. Test it, kick the tires, and find out.

I'm happy to be wrong.  Would be nice if Canonical clarified that the SSO push of public ssh keys is a one-time thing and provided a "remove keys from our servers" checkbox pre-install.  Or if they provide a more typical solution for logins and putting ssh keys onto the systems, that would be nice.  I'm not interested in remote SSO options and their name "

I'm definitely suffering from Canonical FUD.
>  A user is added by entering an Ubuntu SSO registered email address with one or more registered SSH keys. This user can then access the device over SSH to perform various management and configuration functions.   
99% of the users I want on systems do not have email addresses, certainly not public email addresses.  I haven't tried mike@localhost or [email]mike@localhost.local[/email] or [email]mike@localhost.lan[/email].
BTW, the OP specifically says in the thread that the kiosk won't be connected to any network or am I confused?

>    Security is not a concern -- it won't be networked and there is nothing important on it or direct user interaction with it.   
If the user isn't touching it and there isn't any network, maybe an empty shoe box would work instead?  Call me confused.  [https://en.wikipedia.org/wiki/Useless_machine](https://en.wikipedia.org/wiki/Useless_machine)  got one of those for a relative a few years ago. When the switched it flipped, it opens, an actuator comes out and turns off the switch.  That's it. Oh ... there's a red LED lit for the 2 seconds that it takes to turn the switch back off.  Oddly, it was hours of fun.

Of course, some people don't mind using Ubuntu Core and the SSO.  That's fine and their choice. Could be an excellent option for some situations.

---

### Post by ian-weisser on 2022-12-02
> **TheFu said:**
> BTW, the OP specifically says in the thread that the kiosk won't be connected to any network or am I confused?

You're one of the LEAST confused people I pay attention to.
Totally right about being offline for deployment. My squinty guess was online to prepare and test, offline to deploy when ready.

---

### Post by TheFu on 2022-12-02
> **ian-weisser said:**
> You're one of the LEAST confused people I pay attention to.
Totally right about being offline for deployment. My squinty guess was online to prepare and test, offline to deploy when ready.

I also pay attention to your posts.  

I've worked in air-gapped deployment environments where the systems were never connected to the internet, ever.  Because of my physical access to the server-floor, I could have bypassed some of the requirements, but I didn't want to end up in jail, so I never, ever, did it.
[https://getyarn.io/yarn-clip/0c73619b-5b68-4704-ae0d-29d9ce80b42a](https://getyarn.io/yarn-clip/0c73619b-5b68-4704-ae0d-29d9ce80b42a) - "Listen man. I'm not going to jail for you or anybody!"

---

### Post by clepsdyrae on 2022-12-02
> **TheFu said:**
> They have different levels of bloat in the three TinyCore distros. Pick the smallest with a GUI.

Aha! Thanks.

> **ian-weisser said:**
> This is precisely the use case for Ubuntu  Core (bare bones) with Ubuntu Frame snap (locked down GUI designed for  kiosks)

Yeah I can see how that'd be perfect in the right context; as you both have discussed my application is more "install it and it never changes / minimize background processes" so a TinyCore style distro sounds more like what I'm looking for, but it's great to know about Frame for future projects.

Side question: I'm forever caught between "do the project on a microcontroller because it can handle power cuts without getting corrupted" and "do the project on a SBC because we need more CPU / storage / whatever, but now it's vulnerable to power cuts, disk corruption, unpredictable software in the background, etc." The TinyCore style distros would seem to solve some of those problems, but not the power cuts. Are there distros for embedded linux that are easy to set into "hardened" mode, where e.g. filesystems are mounted read-only, maybe a user-writeable filesystem is tuned for minimal corruption on power loss, etc? Or is that category pretty much up to an implementer to figure out themselves? It just feels like if I just edit fstab to mount root as read-only, it's not going to be nearly that simple. :-) I'd love to be able to have something going on a Pi where I can just cut the power any old time and not worry about it... maybe that's crazy.

---

### Post by TheFu on 2022-12-02
Last time I worked on embedded systems, we were using these computers: [https://researcher.watson.ibm.com/researcher/view_group.php?id=7356](https://researcher.watson.ibm.com/researcher/view_group.php?id=7356) . They were powered by hydrogen fuel cells most of the time and only drew 550W each (we used 5), but would power down 2 outside critical phases. They didn't have any OS, just a few programs that launched other functions in a loop on different priorities.  Today, you can think of them as different threads, since many of the same ideas apply, except that in a priority system, higher priority programs can interrupt lower priority programs mid-instruction, so we had strict data homogeneity requirements to ensure that data on different priorities only got swapped at approved points in the execution.  Adding more complexity, the higher priority programs ran at 25Hz and the lowest priority ran at 0.5Hz and the mid-priority  running at 6.25Hz (required 2 cycles to complete some guidance calculations).   These were man-rated systems, btw. A software error could kill the crew, which never happened. 2 crews were lost, due to hardware failures, not software, though I doubt the crews cared about that distinction.  I started on the AP101B, but did most of my work targeting the AP-101S version which didn't have core memory, finally, but effectively nearly doubled the RAM available for software.  Sadly, the performance of the CPUs wasn't modified.  In the 5 yrs I worked there, I was responsible for 1 bug being introduced.  The single line of code with the bug was scrutinized and I even asked the "experts" for help on it.  About a year later, when the bug was found in the last level of independent testing, everyone on the review team (about 20 people) had selective memory. Fortunately, I had retained the emails with my question and their responses, which included asking other experts and their opinion on the specific code too.  It was very odd to need to ask for help like that. In fact, it was 1 of 2 times where I did.  The other time, I was writing some really nasty, but hand-optimized boolean logic. Only 1 person of the 20 that reviewed the code check those specific lines of code and found ZERO errors.  Testing found none as well, and we tested every possible combination of input values. I heard that nobody touched the code after I left out of fear they'd break it.  It was ugly and not the best code for maintainability.

So, perhaps I'm not the best person to ask about current embedded development.  Simple is always better in my book.  Less code usually means fewer chances for bugs. All software has bugs.  I wouldn't deploy on a Raspberry-pi anything to an industrial solution. There **are** better, more and less capable SBCs, which are a good fit.

As for which parts of Linux can be mounted read-only, there is a Linux File System Hierarchy Standards document, which explains that.  Probably don't need to read it all, but at least reading the section with the table that explains what goes where and the table that has which areas can be read-only wouldn't hurt.  A typical Ubuntu install doesn't bother setting up separate file systems for the read-only vs read-write areas.  If you want those, it is a manual storage config for you and you'll want to control the mount options in the fstab manually as well.  Most of the OS can be mounted read-only. Actually, some should be mounted with different mount options to increase security, but keeping it simple seems to be the new rule for Ubuntu default installations.  It is a trade-off.

---

### Post by clepsdyrae on 2022-12-04
Wow, wild. Back in my CS class days when we were doing basic "proving" of algorithms and the like, they spoke of the legendary Shuttle code where every line was tracked with a binder of documentation and everything was algorithmically proven and tested ten different ways. Might have been when I decided that professional software engineering wasn't going to be my thing. :-)

---

### Post by TheFu on 2022-12-05
Very few CS people liked working in the heavy process oriented environment.  I suspect you heard wild stories about "every line was tracked with a binder of documentation".  That simply wasn't true.  Every line was tracked to a change management authorization and to a specific person's name.  The CR/DR would have a notebook, not each line.  A CR might need 1 or 5000 lines of code added/changed/removed.

---

