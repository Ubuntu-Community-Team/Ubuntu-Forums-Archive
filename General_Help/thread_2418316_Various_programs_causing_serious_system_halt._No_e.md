---
title: "Various programs causing serious system halt. No experience with this. 18.04 version."
date: 2019-05-05
forum: General Help
---

### Post by brill700 on 2019-05-05
Admittedly, I don't think I spent enough time on Ubuntu. I had 16.xx and just upgraded to Bionic Beaver. Maybe I don't know what Ubuntu crashes look like, but I'll describe what I keep seeing in the third paragraph. I'll be using Gimp, or some video editor (name of which I forgot), and both of these programs produced the same crash. I briefly endured these constant crashes, until I decided to attempt to use the proprietary driver for my Nvidia GeForce 210, as I felt the Nouvau driver might possibly not be fantastic, and could have been causing issues. When I did this, it rebooted into a black screen loop. Seeing the major crash issue, and now the boot loop that I couldn't readily resolve, I reinstalled the entire o/s from scratch. It's worth noting that I dual boot with Windows 10, which I'm currently using to write this. 

The re-install was successful. I installed Gimp, but could not remember what I was editing videos with. I opted against editing videos on here again, as my cpu fans run fast during exports, and I need a bigger sink. I opened Gimp, began editing, and the system wigged out again, same way as before the re-install, and the same way it did with the video editor. It will not occur at any other time. Browsers are good, multimedia apps are good. Only picture and video manipulation apps seem to trigger the failure. 

On to the failure: Basically, the screen goes black for several seconds without warning (usually after selecting a Gimp menu item; crop, scale, etc). The same was true with the video editor that I can't name for you anymore. After a few moments in the dark, the login screen pops up. I login and encounter another black screen for a few moments. Once my desktop shows again, all applications are terminated, and consequently, all unsaved work is lost. Now... this is not a restart, as the time required to reboot would be considerably longer. It's almost as if it went to sleep, came right back, logged me in, and closed all my work to mess with me. I've never seen this happen before, but as I said, I may not have logged enough hours on the o/s to recognize this behavior. Checked logs, the last log before the "event" were along the lines of major dependency/access issues with PulseAudio. If anyone would like to see the log of the last disastrous event, I saved a text version somewhere on the drive, and I'll furnish it next time I boot Ubuntu on request. 

In closing, I'm new to this forum, as Ubuntu has generally been an okay o/s for the 8 years I've been using it. SUMMARY: Nvidia GeForce 210, ASUS 970 Game board, Ubuntu 18.04. Thanks for reading.

---

### Post by donbcilly on 2019-05-05
> **brill700 said:**
>  If anyone would like to see the log of the last disastrous event, I saved a text version somewhere on the drive, and I'll furnish it next time I boot Ubuntu on request. 


You **can** get to your log file from Windows... look for "accessing Linux partition from Windows" or similar.

---

### Post by HermanAB on 2019-05-05
Note that the good video editors (Blender) are very hard to use, while the simple ones (Kdenlive) are buggy and crashy.

Such is life...

---

### Post by brill700 on 2019-05-12
I know Kden is pretty buggy. But lately any program I use causes major crashes. I can no longer safely use it, as the o/s has destabilized very badly. I would re-install at this stage, but the process will begin again as it did previously. I'll basically get here again. I enjoy 18.04, and I'd feel like crap running back to 16.xx. Anyway... I saved today's disaster logs too. So I'll retrieve those in a minute.

This is the system log. Today's crash occured at 11:47 p.m. 

```
&#65279;11:48:14 PM kernel: audit: type=1400 audit(1557632894.908:61): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/proc/3399/mounts" pid=3399 comm="gnome-logs" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
11:48:14 PM kernel: kauditd_printk_skb: 6 callbacks suppressed
11:48:09 PM kernel: audit: type=1400 audit(1557632889.716:53): apparmor="DENIED" operation="open" profile="snap.gnome-logs.gnome-logs" name="/home/[omitted]/.bash_logout" pid=3399 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
11:48:09 PM kernel: kauditd_printk_skb: 32 callbacks suppressed
11:47:14 PM kernel: rfkill: input handler disabled
11:46:12 PM kernel: nouveau 0000:01:00.0: msvld: init failed, -19
11:25:50 PM kernel: rfkill: input handler disabled
11:23:48 PM kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
11:23:48 PM kernel: igb 0000:04:00.0 enp4s0: igb: enp4s0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
11:23:46 PM kernel: IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
11:23:44 PM kernel: audit: type=1400 audit(1557631424.020:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=816 comm="apparmor_parser"
11:23:42 PM kernel: [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
11:23:42 PM kernel: nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
11:23:42 PM kernel: Console: switching to colour frame buffer device 240x67
11:23:42 PM kernel: fbcon: nouveaufb (fb0) is primary device
11:23:42 PM kernel: nouveau 0000:01:00.0: DRM: allocated 1920x1080 fb: 0x70000, bo 000000001d4f5b6d
11:23:42 PM kernel: [drm] Driver supports precise vblank timestamp query.
11:23:42 PM kernel: nouveau 0000:01:00.0: DRM: DCB conn 02: 00000200
11:23:42 PM kernel: [TTM] Initializing DMA pool allocator
11:23:42 PM kernel: input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input18
11:23:42 PM kernel: nouveau 0000:01:00.0: fb: 1024 MiB DDR3
11:23:42 PM kernel: Console: switching to colour dummy device 80x25
11:23:42 PM kernel: fb: switching to nouveaufb from EFI VGA
11:23:42 PM kernel: checking generic (d1000000 300000) vs hw (d0000000 2000000)
11:23:42 PM kernel: MXM: GUID detected in BIOS
11:23:42 PM kernel: asus_wmi: Number of fans: 1
11:23:42 PM kernel: input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input14
11:23:42 PM kernel: asus_wmi: SFUN value: 0x0
11:23:42 PM kernel: EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
 Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
 (Note that use of the override may cause unknown side effects.)
11:23:42 PM kernel: MCE: In-kernel MCE decoding enabled.
11:23:42 PM kernel: kvm: Nested Paging enabled
11:23:42 PM kernel: input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
11:23:42 PM kernel: snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
11:23:42 PM kernel: AES CTR mode by8 optimization enabled
11:23:42 PM kernel: AVX version of gcm_enc/dec engaged.
11:23:42 PM kernel: snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
11:23:42 PM kernel: cryptd: max_cpu_qlen set to 1000
11:23:42 PM kernel: Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k FS
11:23:35 PM kernel: EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
11:23:35 PM kernel: ppdev: user-space parallel port driver
11:23:35 PM kernel: lp: driver loaded but no devices found
11:23:35 PM kernel: Created slice system-systemd\x2dfsck.slice.
11:23:35 PM kernel: Started Forward Password Requests to Wall Directory Watch.
11:23:35 PM kernel: Set up automount Arbitrary Executable File Formats File System Automount Point.
11:23:35 PM kernel: Created slice User and Session Slice.
11:23:35 PM kernel: Proceeding WITHOUT firewalling in effect! (This warning is only shown for the first loaded unit using IP firewalling.)
11:23:35 PM kernel: File /lib/systemd/system/systemd-journald.service:36 configures an IP firewall (IPAddressDeny=any), but the local system does not support BPF/cgroup based firewalling.
11:23:35 PM kernel: Lockdown: systemd: BPF is restricted; see man kernel_lockdown.7
11:23:35 PM kernel: Set hostname to <MP12Lx>.
11:23:35 PM kernel: Detected architecture x86-64.
11:23:35 PM kernel: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
```

This is the applications log. Again, 11:47 p.m. is the time of the event. 

```
11:48:47 PM gnome-logs: Error creating IO channel for /proc/self/mountinfo: Permission denied (g-file-error-quark, 2)
11:48:16 PM gnome-shell: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.80/org/ayatana/NotificationItem/software_update_available
11:48:14 PM gnome-software: Unable to acquire bus name 'org.gnome.Software'
11:48:09 PM gnome-logs: Error creating IO channel for /proc/self/mountinfo: Permission denied (g-file-error-quark, 2)
11:47:38 PM pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
11:47:34 PM gnome-software: Failed to load snap icon: local snap has no icon
11:47:25 PM systemd: Started flatpak document portal service.
11:47:25 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.freedesktop.portal.Documents'
11:47:25 PM systemd: Starting flatpak document portal service...
11:47:25 PM dbus-daemon: [session uid=1000 pid=2858] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.77' (uid=1000 pid=3399 comm="/snap/bin/gnome-logs " label="unconfined")
11:47:25 PM nautilus: g_queue_free: assertion 'queue != NULL' failed
11:47:25 PM gnome-software: disabled plugins: dpkg, dummy, repos, epiphany
11:47:25 PM nautilus: g_queue_pop_head: assertion 'queue != NULL' failed
11:47:24 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gnome.seahorse.Application'
11:47:24 PM systemd: Started GNOME Terminal Server.
11:47:24 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gnome.Terminal'
11:47:24 PM nautilus: g_queue_pop_head: assertion 'queue != NULL' failed
11:47:24 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gnome.ControlCenter.SearchProvider'
11:47:23 PM systemd: Starting GNOME Terminal Server...
11:47:23 PM dbus-daemon: [session uid=1000 pid=2858] Activating service name='org.gnome.Software' requested by ':1.23' (uid=1000 pid=2994 comm="/usr/bin/gnome-shell " label="unconfined")
11:47:23 PM nautilus: Could not establish a connection to Tracker: Failed to load SPARQL backend: Key file does not have group “DomainOntology”
11:47:23 PM dbus-daemon: [session uid=1000 pid=2858] Activating service name='org.gnome.seahorse.Application' requested by ':1.23' (uid=1000 pid=2994 comm="/usr/bin/gnome-shell " label="unconfined")
11:47:23 PM nautilus: g_key_file_load_from_file: assertion 'file != NULL' failed
11:47:23 PM dbus-daemon: [session uid=1000 pid=2858] Activating service name='org.gnome.Calendar' requested by ':1.23' (uid=1000 pid=2994 comm="/usr/bin/gnome-shell " label="unconfined")
11:47:15 PM systemd: Started Virtual filesystem metadata service.
11:47:15 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gtk.vfs.Metadata'
11:47:15 PM systemd: Starting Virtual filesystem metadata service...
11:47:15 PM dbus-daemon: [session uid=1000 pid=2858] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.60' (uid=1000 pid=3197 comm="nautilus-desktop " label="unconfined")
11:47:15 PM gnome-shell: GNOME Shell started at Sat May 11 2019 23:47:13 GMT-0400 (EDT)
11:47:14 PM systemd: Started Evolution address book service.
11:47:14 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook9'
11:47:14 PM systemd: Starting Evolution address book service...
11:47:14 PM dbus-daemon: [session uid=1000 pid=2858] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook9' unit='evolution-addressbook-factory.service' requested by ':1.68' (uid=1000 pid=3255 comm="/usr/lib/evolution/evolution-calendar-factory-subp" label="unconfined")
11:47:14 PM gnome-shell: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
11:47:14 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'ca.desrt.dconf'
11:47:14 PM systemd: Started Evolution calendar service.
11:47:14 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gnome.evolution.dataserver.Calendar7'
11:47:14 PM systemd: Starting Evolution calendar service...
11:47:14 PM dbus-daemon: [session uid=1000 pid=2858] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar7' unit='evolution-calendar-factory.service' requested by ':1.31' (uid=1000 pid=3047 comm="/usr/lib/gnome-shell/gnome-shell-calendar-server " label="unconfined")
11:47:13 PM gnome-session-b: Entering running state
11:47:13 PM gsd-sharing: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
11:47:13 PM gnome-shell: JS WARNING: [/usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com/appIcons.js 1028]: unreachable code after return statement
11:47:13 PM gnome-session-b: WARNING: App 'spice-vdagent.desktop' exited with code 1
11:47:13 PM spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
11:47:13 PM systemd: Started Virtual filesystem service - Media Transfer Protocol monitor.
11:47:13 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
11:47:13 PM systemd: Starting Virtual filesystem service - Media Transfer Protocol monitor...
11:47:13 PM dbus-daemon: [session uid=1000 pid=2858] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.23' (uid=1000 pid=2994 comm="/usr/bin/gnome-shell " label="unconfined")
11:47:13 PM systemd: Started Virtual filesystem service - GNOME Online Accounts monitor.
11:47:13 PM dbus-daemon: [session uid=1000 pid=2858] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
11:47:13 PM systemd: Starting Virtual filesystem service - GNOME Online Accounts monitor...
```

11:47 p.m. was time of crash. "All" tab of log.

---

### Post by brill700 on 2019-05-12
Getting forbidden errors on the forum, so this is all I can post. I'll furnish important and all tabs on request.

---

### Post by CatKiller on 2019-05-12
> **brill700 said:**
> On to the failure: Basically, the screen goes black for several seconds without warning (usually after selecting a Gimp menu item; crop, scale, etc). The same was true with the video editor that I can't name for you anymore. After a few moments in the dark, the login screen pops up. I login and encounter another black screen for a few moments. Once my desktop shows again, all applications are terminated, and consequently, all unsaved work is lost. Now... this is not a restart, as the time required to reboot would be considerably longer. It's almost as if it went to sleep, came right back, logged me in, and closed all my work to mess with me.

This is a crash of the X server.

The login screen is the first thing that gets displayed when the X server (re)starts.

Nothing that has a window can survive the X server restarting; that's why all your programs have closed.

The blank screen between logging in and getting the desktop suggests that your desktop is running at a different resolution to your login screen, which probably isn't optimal.

The X server log is at /var/log/Xorg.0.log.

The proprietary nvidia driver is generally more tested and more performant than the open source nouveau driver. The problem you're having could be caused elsewhere, though; there are a lot of moving parts to actually getting things displayed on a screen.

---

### Post by dragonfly41 on 2019-05-12
Installing petit *might* help in making some sense of your log files.

[http://crunchtools.com/software/petit/](http://crunchtools.com/software/petit/)

---

### Post by oldos2er on 2019-05-12
> **brill700 said:**
> Getting forbidden errors on the forum, so this is all I can post. I'll furnish important and all tabs on request.

If it's larger than 50KB, post it on paste.ubuntu.com and post the link to it here. The forum software can't handle that much text, which is why you see the error you reported.

---

### Post by brill700 on 2019-05-22
> **CatKiller said:**
> This is a crash of the X server.

The proprietary nvidia driver is generally more tested and more performant than the open source nouveau driver. The problem you're having could be caused elsewhere, though; there are a lot of moving parts to actually getting things displayed on a screen. 

I had a terrible time trying to resort to the prop driver. I tried this several weeks ago, and it crashed and burned miserably. Essentially broke the o/s and I reinstalled everything. I'll see about the x server stuff in a bit.

---

### Post by CatKiller on 2019-05-23
> **brill700 said:**
> I had a terrible time trying to resort to the prop driver. I tried this several weeks ago, and it crashed and burned miserably. Essentially broke the o/s and I reinstalled everything. I'll see about the x server stuff in a bit.

It can be scary to have no graphical display, but it doesn't mean that the OS is irreparably broken. It's often just a config file that needs tweaking when that happens. Using the TTYs by using Ctrl-Alt and the F-keys, or booting from a live disc/USB are both useful tools.

In any case, it seems that the 340 branch of the Nvidia driver is the last that supports the GeForce 210, so don't try a higher number than that.

---

