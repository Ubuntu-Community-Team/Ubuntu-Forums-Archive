---
title: "System Freeze after sometime"
date: 2021-10-08
forum: General Help
---

### Post by waffen on 2021-10-08
Hello,

My PC constantly freezes to the point that I have to restart it. This happens after leaving the PC doing nothing or in the middle of daily tasks.

I was thinking it was a possible motherboard or other component problem so I bought a new PC, I took the HD out of the old PC and put it in the new one and it still gives the same problem, so I guess the problem is in some software installed.

However reading the logs I am unable to discover what is failing, if you could give me a help I would be very grateful.

If you tell me what log file you need to determine the error, I would upload it right here, thanks!

I'm using:
Ubuntu 20.04.3 uptodate
Ci5 10th Gen
16 GB RAM
3TB == 2TB HD + 1TB HD
Nvidia GeForce GTX 1650

---

### Post by dragonfly41 on 2021-10-08
Here is one troubleshooting idea.  It is just detective work / guess work.
Clearly you have transferred the problem between PC's.
A costly test but at least you now have a dual PC.

In your current configuration I would try creating a guest account and in that
account enable only minimum functionality. 
No extensions in browsers.
Minimum applications in use.
I do recommend Stacer as one GUI tool to monitor resources, but you can do that
also through command line.
I use glogg as a log file viewer.

---

### Post by aug7744 on 2021-10-08
CPU and GPU cooler are working correctly ?
Test your RAM with Memtest.

---

### Post by waffen on 2021-10-08
> **aug7744 said:**
> CPU and GPU cooler are working correctly ?
Test your RAM with Memtest.

I already did it all fine, its a new PC

---

### Post by waffen on 2021-10-08
> **dragonfly41 said:**
> Here is one troubleshooting idea.  It is just detective work / guess work.
Clearly you have transferred the problem between PC's.
A costly test but at least you now have a dual PC.

In your current configuration I would try creating a guest account and in that
account enable only minimum functionality. 
No extensions in browsers.
Minimum applications in use.
I do recommend Stacer as one GUI tool to monitor resources, but you can do that
also through command line.
I use glogg as a log file viewer.

Ok I'll check it thanks

Just in case this is the log of the last freeze today in the morning, PC freeze after 15 minutes. Let me know if you can detect some problem...

```

10:49:36 Xorg: (--) NVIDIA(GPU-0):
10:49:33 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:49:15 systemd: Finished Cleanup of Temporary Directories.
10:48:35 GeckoMain: ###!!! [Parent][RunMessage] Error: Channel closing: too late to send/recv, messages will be lost
10:48:05 systemd: packagekit.service: Succeeded.
10:48:05 packagekitd: daemon quit
10:47:54 GeckoMain: ###!!! [Parent][RunMessage] Error: Channel closing: too late to send/recv, messages will be lost
10:47:32 rtkit-daemon: Supervising 10 threads of 6 processes of 2 users.
10:46:27 WebExtensions: [GFX1-]: Failed to connect WebRenderBridgeChild.
10:46:04 gnome-shell: Usage of object.actor is deprecated for PanelMenuButton
get@resource:///org/gnome/shell/ui/environment.js:287:29
updateState@/home/mario/.local/share/gnome-shell/extensions/lockkeys@fawtytoo/extension.js:29:10

10:45:01 cron: pam_unix(cron:session): session closed for user root
10:45:01 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.ChromeGnomeShell'
10:44:50 rtkit-daemon: Supervising 7 threads of 3 processes of 2 users.
10:44:35 systemd: Started Application launched by gnome-shell.
10:43:27 tracker-store: OK
10:43:19 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:43:12 systemd: tracker-extract.service: Succeeded.
10:43:02 aptd: 10:43:02 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/92f98b0cc9f34f71a0b2d13dca496a3d
10:42:57 systemd: Started Tracker metadata extractor.
10:42:57 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:57 tracker-extract: Setting priority nice level to 19
10:42:57 systemd: Starting Tracker metadata extractor...
10:42:57 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:56 systemd: tracker-extract.service: Succeeded.
10:42:56 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.freedesktop.Tracker1'
10:42:56 systemd: Starting Tracker metadata database store and lookup manager...
10:42:56 dbus-daemon: [session uid=125 pid=1486] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.2' (uid=125 pid=1467 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:55 systemd: pk-debconf-helper.service: Succeeded.
10:42:55 pk-debconf-help: No active connections, exiting
10:42:54 systemd: tracker-store.service: Succeeded.
10:42:54 tracker-store: OK
10:42:51 systemd: /etc/systemd/system/teamviewerd.service:9: PIDFile= references a path below legacy directory /var/run/, updating /var/run/teamviewerd.pid &#8594; /run/teamviewerd.pid; please update the unit file accordingly.
10:42:50 apache2: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
10:42:50 systemd: Starting The Apache HTTP Server...
10:42:50 apache2: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
10:42:50 systemd: Stopping The Apache HTTP Server...
10:42:46 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:46 tracker-extract: Setting priority nice level to 19
10:42:46 systemd: Starting Tracker metadata extractor...
10:42:46 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:45 systemd: tracker-extract.service: Succeeded.
10:42:35 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:35 tracker-extract: Setting priority nice level to 19
10:42:35 systemd: Starting Tracker metadata extractor...
10:42:35 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:34 systemd: tracker-extract.service: Succeeded.
10:42:24 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:24 tracker-extract: Setting priority nice level to 19
10:42:24 systemd: Starting Tracker metadata extractor...
10:42:24 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:23 systemd: tracker-extract.service: Succeeded.
10:42:19 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:42:13 systemd: Started Tracker metadata extractor.
10:42:13 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:13 tracker-extract: Setting priority nice level to 19
10:42:13 systemd: Starting Tracker metadata extractor...
10:42:13 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:12 systemd: Started Virtual filesystem metadata service.
10:42:12 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.gtk.vfs.Metadata'
10:42:12 systemd: Starting Virtual filesystem metadata service...
10:42:12 dbus-daemon: [session uid=125 pid=1486] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.16' (uid=125 pid=6059 comm="/usr/libexec/tracker-extract " label="unconfined")
10:42:12 systemd: Started Tracker metadata extractor.
10:42:12 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.freedesktop.Tracker1.Miner.Extract'
10:42:12 tracker-extract: Setting priority nice level to 19
10:42:12 systemd: Starting Tracker metadata extractor...
10:42:12 dbus-daemon: [session uid=125 pid=1486] Activating via systemd: service name='org.freedesktop.Tracker1.Miner.Extract' unit='tracker-extract.service' requested by ':1.2' (uid=125 pid=1467 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:42:11 systemd: Started Tracker metadata database store and lookup manager.
10:42:11 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1'
10:42:11 systemd: Started Tracker metadata database store and lookup manager.
10:42:11 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.freedesktop.Tracker1'
10:42:11 systemd: Starting Tracker metadata database store and lookup manager...
10:42:11 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:41:55 systemd: Started debconf communication service.
10:41:48 aptd: 10:41:48 AptDaemon.Worker [INFO]: Processing transaction /org/debian/apt/transaction/92f98b0cc9f34f71a0b2d13dca496a3d
10:40:46 snap-store: automatically prevented from changing kind on system/snap/*/runtime/io.snapcraft.core18-CSO04Jhav2yK0uz97cr0ipQRyqg0qQL6/latest/stable from runtime to unknown!
10:40:41 packagekitd: get-details transaction /1032_cdeaaeec from uid 1000 finished with success after 188ms
10:40:08 systemd: snap.canonical-livepatch.canonical-livepatch.1bd5456a-44a3-4888-baa9-2ee2e45c98fe.scope: Succeeded.
10:40:05 anacron: Normal exit (1 job run)
10:40:03 pkexec: mario: Executing command [USER=root] [TTY=unknown] [CWD=/home/mario] [COMMAND=/usr/lib/update-notifier/package-system-locked]
10:40:00 snapd: snap not found: "y2mate"
10:40:00 xdg-desktop-por: Error from gnome-shell: GDBus.Error:org.gtk.Notifications.InvalidApp: The app by ID "snap.snap-store" could not be found
10:40:00 packagekitd: get-updates transaction /1029_cdcbaeab from uid 1000 finished with success after 254ms
10:39:59 logger: no dictionary update necessary.
10:39:59 packagekitd: resolve transaction /1028_bbcbdcaa from uid 1000 finished with success after 198ms
10:39:59 snapd: snap not found: "y2mate"
10:39:58 aptd: 10:39:58 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/d407b9c4968647c286d0deb74825315a
10:39:58 snap-store: automatically prevented from changing kind on system/package/*/generic/org.a11y.brltty/* from generic to unknown!
10:39:58 anacron: Updated timestamp for job `cron.daily' to 2021-10-08
10:39:58 snap-store: FIXME: Unknown progress handling is not yet implemented for GsProgressButton
10:39:58 anacron: Job `cron.daily' started
10:39:57 snap-store: hiding category audio-video featured applications: found only 0 to show, need at least 9
10:39:55 kernel: audit: type=1326 audit(1633707595.960:87): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2638 comm="pool-org.gnome." exe="/snap/snap-store/547/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7fa677d964e7 code=0x50000
10:39:55 pool-org.gnome.: SECCOMP auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2638 comm="pool-org.gnome." exe="/snap/snap-store/547/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7fa677d964e7 code=0x50000
10:39:55 systemd: geoclue.service: Succeeded.
10:39:55 geoclue: Service not used for 60 seconds. Shutting down..
10:39:55 snap-store: xb_builder_node_unlink: assertion 'XB_IS_BUILDER_NODE (self)' failed
10:39:55 kernel: audit: type=1400 audit(1633707595.592:86): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2638 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
10:39:55 pool-org.gnome.: AVC apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2638 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
10:39:55 kernel: audit: type=1400 audit(1633707595.568:85): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2638 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
10:39:55 pool-org.gnome.: AVC apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2638 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
10:39:54 snap-store: not handling error download-failed for action refresh: E: No se pudo obtener un bloqueo /var/lib/apt/lists/lock. Lo mantiene el proceso 4031 (aptd)
W: Tenga en cuenta que eliminar el archivo de bloqueo no es una solución y puede dañar su sistema.
E: No se pudo bloquear el directorio /var/lib/apt/lists/

10:39:54 packagekitd: refresh-cache transaction /1027_bcaeaeea from uid 1000 finished with failed after 194ms
10:39:54 aptd: 10:39:54 AptDaemon.Worker [INFO]: Updating cache
10:39:54 snap-store: not handling error download-failed for action refresh: E: No se pudo obtener un bloqueo /var/lib/apt/lists/lock. Lo mantiene el proceso 4031 (aptd)
W: Tenga en cuenta que eliminar el archivo de bloqueo no es una solución y puede dañar su sistema.
E: No se pudo bloquear el directorio /var/lib/apt/lists/

10:39:54 packagekitd: refresh-cache transaction /1026_beaeeebd from uid 1000 finished with failed after 1105ms
10:39:53 aptd: 10:39:53 AptDaemon.Worker [INFO]: Processing transaction /org/debian/apt/transaction/d407b9c4968647c286d0deb74825315a
10:39:53 packagekitd: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
10:39:52 dbus-daemon: [system] Successfully activated service 'org.debian.apt'
10:39:52 aptd: 10:39:52 AptDaemon [INFO]: Initializing daemon
10:39:52 dbus-daemon: [system] Activating service name='org.debian.apt' requested by ':1.571' (uid=1000 pid=3967 comm="/usr/bin/python3 /usr/bin/update-manager " label="unconfined") (using servicehelper)
10:39:41 systemd: Started Application launched by gnome-shell.
10:39:32 packagekitd: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
10:39:32 kernel: audit: type=1400 audit(1633707572.719:84): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/etc/PackageKit/Vendor.conf" pid=2638 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
10:39:32 snap-store: /etc/PackageKit/Vendor.conf file not found
10:39:31 kernel: audit: type=1107 audit(1633707571.555:83): pid=939 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=2638 label="snap.snap-store.ubuntu-software" peer_pid=970 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
10:39:31 snap-store: enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blocklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
10:39:31 kernel: USER_AVC pid=939 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=2638 label="snap.snap-store.ubuntu-software" peer_pid=970 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
10:39:31 snap-store: plugin appstream took 1,2 seconds to do setup
10:39:30 systemd: systemd-hostnamed.service: Succeeded.
10:39:30 kernel: audit: type=1107 audit(1633707570.295:81): pid=939 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=2638 label="snap.snap-store.ubuntu-software" peer_pid=970 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
10:39:30 kernel: USER_AVC pid=939 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=2638 label="snap.snap-store.ubuntu-software" peer_pid=970 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
10:39:30 snap-store: plugin fwupd took 3,9 seconds to do setup
10:39:30 systemd: Started Firmware update daemon.
10:39:30 dbus-daemon: [system] Successfully activated service 'org.freedesktop.fwupd'
10:39:26 systemd: Starting Firmware update daemon...
10:39:26 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.fwupd' unit='fwupd.service' requested by ':1.568' (uid=1000 pid=2638 comm="/snap/snap-store/547/usr/bin/snap-store --gapplica" label="snap.snap-store.ubuntu-software (enforce)")
10:39:25 systemd: Started Portal service.
10:39:25 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.portal.Desktop'
10:39:25 systemd: Started Portal service (GTK+/GNOME implementation).
10:39:25 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.impl.portal.desktop.gtk'
10:39:25 systemd: Starting Portal service (GTK+/GNOME implementation)...
10:39:25 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.impl.portal.desktop.gtk' unit='xdg-desktop-portal-gtk.service' requested by ':1.82' (uid=1000 pid=2885 comm="/usr/libexec/xdg-desktop-portal " label="unconfined")
10:39:24 systemd: Starting Portal service...
10:39:24 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.portal.Desktop' unit='xdg-desktop-portal.service' requested by ':1.81' (uid=1000 pid=2638 comm="/snap/snap-store/547/usr/bin/snap-store --gapplica" label="snap.snap-store.ubuntu-software (enforce)")
10:39:23 kernel: audit: type=1326 audit(1633707563.851:79): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2638 comm="snap-store" exe="/snap/snap-store/547/usr/bin/snap-store" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7fa677da0639 code=0x50000
10:39:23 snap-store: SECCOMP auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2638 comm="snap-store" exe="/snap/snap-store/547/usr/bin/snap-store" sig=0 arch=c000003e syscall=314 compat=0 ip=0x7fa677da0639 code=0x50000
10:39:17 nautilus: connect() failed
10:39:14 systemd: tracker-store.service: Succeeded.
10:39:14 tracker-store: OK
10:39:13 nautilus: connect() failed
10:39:09 gnome-shell: Registering session with GDM
10:39:09 nautilus: connect() failed
10:39:09 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.Shell.CalendarServer'
10:39:09 systemd: Started Evolution address book service.
10:39:09 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.evolution.dataserver.AddressBook10'
10:39:08 systemd: tmp-snap.rootfs_qWwiUE.mount: Succeeded.
10:39:08 kernel: audit: type=1400 audit(1633707548.758:78): apparmor="DENIED" operation="capable" profile="/snap/snapd/13170/usr/lib/snapd/snap-confine" pid=2638 comm="snap-confine" capability=4  capname="fsetid"
10:39:08 snap-confine: AVC apparmor="DENIED" operation="capable" profile="/snap/snapd/13170/usr/lib/snapd/snap-confine" pid=2638 comm="snap-confine" capability=4  capname="fsetid"
10:39:08 systemd: Starting Evolution address book service...
10:39:08 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gnome.evolution.dataserver.AddressBook10' unit='evolution-addressbook-factory.service' requested by ':1.77' (uid=1000 pid=2566 comm="/usr/libexec/evolution-calendar-factory " label="unconfined")
10:39:08 systemd: Started Evolution calendar service.
10:39:08 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.evolution.dataserver.Calendar8'
10:39:08 nautilus: connect() failed
10:39:08 systemd: Started snap.snap-store.ubuntu-software.08be3554-2ee8-4e4b-b0bf-b913305c3fbb.scope.
10:39:08 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.portal.Documents'
10:39:07 systemd: Starting flatpak document portal service...
10:39:07 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.portal.Documents' unit='xdg-document-portal.service' requested by ':1.78' (uid=1000 pid=2638 comm="/snap/bin/snap-store.ubuntu-software --gapplicatio" label="unconfined")
10:39:03 conky: conky: drawing to double buffer
10:39:02 systemd: Starting Evolution calendar service...
10:39:02 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gnome.evolution.dataserver.Calendar8' unit='evolution-calendar-factory.service' requested by ':1.47' (uid=1000 pid=2273 comm="/usr/libexec/gnome-shell-calendar-server " label="unconfined")
10:39:02 systemd: Condition check resulted in GNOME Welcome Tour being skipped.
10:39:02 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.evolution.dataserver.Sources5'
10:39:02 systemd: tracker-extract.service: Succeeded.
10:39:02 colord: failed to get session [pid 2390]: No hay datos disponibles
10:39:02 gnome-shell: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
10:39:02 systemd: Started Virtual filesystem metadata service.
10:39:02 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.Metadata'
10:39:01 cron: pam_unix(cron:session): session closed for user root
10:39:01 systemd: Starting Virtual filesystem metadata service...
10:39:01 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.48' (uid=1000 pid=2316 comm="/usr/libexec/evolution-source-registry " label="unconfined")
10:39:01 systemd: Reached target GNOME WWan management.
10:39:00 gdbus: (uint32 2,)
10:39:00 gnome-shell: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
10:39:00 gsd-media-keys: Failed to grab accelerator for keybinding settings:playback-random
10:39:00 kernel: rfkill: input handler disabled
10:39:00 systemd: Started Locale Service.
10:39:00 dbus-daemon: [system] Successfully activated service 'org.freedesktop.locale1'
10:39:00 systemd: Started Hostname Service.
10:39:00 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
10:39:00 NetworkManager: <info>  [1633707540.7164] agent-manager: agent[74fae8518637a4e4,:1.544/org.gnome.Shell.NetworkAgent/1000]: agent registered
10:39:00 systemd: Starting Locale Service...
10:39:00 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.555' (uid=1000 pid=2396 comm="/usr/libexec/gsd-keyboard " label="unconfined")
10:39:00 systemd: Reached target GNOME Keyboard handling.
10:39:00 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.553' (uid=1000 pid=2408 comm="/usr/libexec/gsd-rfkill " label="unconfined")
10:39:00 systemd: Reached target GNOME Smartcard handling.
10:39:00 gnome-session-b: Entering running state
10:39:00 systemd: Reached target GNOME Maintenance of expirable data.
10:39:00 Xorg: (--) NVIDIA(GPU-0):
10:39:00 systemd: Finished Clean php session files.
10:39:00 Xorg: (--) NVIDIA(GPU-0):
10:39:00 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.Shell.Notifications'
10:39:00 Xorg: (--) NVIDIA(GPU-0):
10:39:00 dbus-daemon: [session uid=1000 pid=2005] Activating service name='org.gnome.Shell.Notifications' requested by ':1.38' (uid=1000 pid=2242 comm="/usr/bin/gnome-shell " label="unconfined")
10:39:00 systemd: Starting Clean php session files...
10:39:00 dbus-daemon: [session uid=1000 pid=2005] Activating service name='org.freedesktop.FileManager1' requested by ':1.38' (uid=1000 pid=2242 comm="/usr/bin/gnome-shell " label="unconfined")
10:38:56 systemd: Starting Evolution source registry...
10:38:56 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gnome.evolution.dataserver.Sources5' unit='evolution-source-registry.service' requested by ':1.47' (uid=1000 pid=2273 comm="/usr/libexec/gnome-shell-calendar-server " label="unconfined")
10:38:56 gnome-shell: Usage of object.actor is deprecated for PanelMenuButton
get@resource:///org/gnome/shell/ui/environment.js:287:29
updateState@/home/mario/.local/share/gnome-shell/extensions/lockkeys@fawtytoo/extension.js:29:10
enable@/home/mario/.local/share/gnome-shell/extensions/lockkeys@fawtytoo/extension.js:56:5
_callExtensionEnable@resource:///org/gnome/shell/ui/extensionSystem.js:167:32
loadExtension@resource:///org/gnome/shell/ui/extensionSystem.js:351:26
_loadExtensions/<@resource:///org/gnome/shell/ui/extensionSystem.js:601:18
collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17
_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:576:19
_enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:610:18
_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:641:18
init@resource:///org/gnome/shell/ui/extensionSystem.js:56:14
_initializeUI@resource:///org/gnome/shell/ui/main.js:257:22
start@resource:///org/gnome/shell/ui/main.js:146:5
@<main>:1:47

10:38:56 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'ca.desrt.dconf'
10:38:55 at-spi2-registr: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
10:38:55 dbus-daemon: dbus-daemon[2214]: Successfully activated service 'org.a11y.atspi.Registry'
10:38:55 gnome-shell: Telepathy is not available, chat integration will be disabled.
10:38:55 polkitd: Registered Authentication Agent for unix-session:2 (system bus name :1.544 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale es_PE.UTF-8)
10:38:55 dbus-daemon: [session uid=1000 pid=2005] Activating service name='ca.desrt.dconf' requested by ':1.38' (uid=1000 pid=2242 comm="/usr/bin/gnome-shell " label="unconfined")
10:38:55 systemd: Started Location Lookup Service.
10:38:55 dbus-daemon: [system] Successfully activated service 'org.freedesktop.GeoClue2'
10:38:55 systemd: Starting Location Lookup Service...
10:38:55 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.544' (uid=1000 pid=2242 comm="/usr/bin/gnome-shell " label="unconfined")
10:38:55 systemd: Started sandboxed app permission store.
10:38:55 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.impl.portal.PermissionStore'
10:38:55 systemd: Starting sandboxed app permission store...
10:38:55 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.impl.portal.PermissionStore' unit='xdg-permission-store.service' requested by ':1.38' (uid=1000 pid=2242 comm="/usr/bin/gnome-shell " label="unconfined")
10:38:54 gnome-shell: Will monitor session 2
10:38:49 Xorg: (--) NVIDIA(GPU-0):
10:38:49 systemd: Starting GNOME Shell on X11...
10:38:49 gnome-keyring-d: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
10:38:49 kernel: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
10:38:46 systemd: Starting GNOME Session Manager (session: ubuntu)...
10:38:46 gnome-session-c: Error creating FIFO: El archivo ya existe
10:38:46 systemd: Started Monitor Session leader for GNOME Session.
10:38:46 gnome-keyring-d: The Secret Service was already initialized
10:38:46 systemd: Started OpenSSH Agent.
10:38:35 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
10:38:35 dbus-daemon: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
10:38:34 systemd: Started Accessibility services bus.
10:38:34 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.a11y.Bus'
10:38:34 systemd: Starting Accessibility services bus...
10:38:34 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.21' (uid=1000 pid=2208 comm="/usr/libexec/gnome-session-check-accelerated " label="unconfined")
10:38:33 dbus-update-act: dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment
10:38:29 xhost: localuser:mario being added to access control list
10:38:28 dbus-update-act: dbus-update-activation-environment: setting XAUTHORITY=/run/user/1000/gdm/Xauthority
10:38:27 xhost: localuser:mario being added to access control list
10:38:27 systemd: fprintd.service: Succeeded.
10:38:23 Xsession: /etc/gdm3/Xsession: Beginning session setup...
10:38:22 kernel: /sbin/prime-offload: 29: cannot create /var/log/prime-offload.log: Permission denied
10:38:22 prime-supported: /usr/bin/prime-supported: 38: cannot create /var/log/prime-supported.log: Permission denied
10:38:22 Xorg: (**) Option "xkb_layout" "es"
10:38:22 systemd: geoclue.service: Succeeded.
10:38:22 gnome-keyring-d: asked to register item /org/freedesktop/secrets/collection/login/4, but it's already registered
10:38:22 kernel: Service not used for 60 seconds. Shutting down..
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.Tracker1'
10:38:22 systemd: Startup finished in 5.078s.
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:22 systemd: Reached target Main User Target.
10:38:22 gnome-keyring-d: asked to register item /org/freedesktop/secrets/collection/login/1, but it's already registered
10:38:22 systemd: Started Tracker file system data miner.
10:38:22 gnome-keyring-d: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
10:38:22 systemd: Started Tracker metadata extractor.
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.freedesktop.secrets'
10:38:22 systemd: Started Tracker metadata database store and lookup manager.
10:38:22 rtkit-daemon: Supervising 7 threads of 2 processes of 2 users.
10:38:22 systemd: Starting Tracker metadata database store and lookup manager...
10:38:22 rtkit-daemon: Successfully made thread 2088 of process 1999 owned by '1000' RT at priority 5.
10:38:22 systemd: Started Virtual filesystem service - Apple File Conduit monitor.
10:38:22 rtkit-daemon: Supervising 6 threads of 2 processes of 2 users.
10:38:22 systemd: Starting Virtual filesystem service - Apple File Conduit monitor...
10:38:22 acpid: 1 client rule loaded
10:38:22 systemd: Started Virtual filesystem service - digital camera monitor.
10:38:22 acpid: client connected from 2081[0:0]
10:38:22 systemd: Starting Virtual filesystem service - digital camera monitor...
10:38:22 acpid: client 1473[0:0] has disconnected
10:38:22 systemd: Started Virtual filesystem service - GNOME Online Accounts monitor.
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Activating service name='org.freedesktop.secrets' requested by ':1.9' (uid=1000 pid=2052 comm="/usr/libexec/goa-daemon " label="unconfined")
10:38:22 goa-daemon: goa-daemon version 3.36.1 starting
10:38:22 rtkit-daemon: Supervising 6 threads of 2 processes of 2 users.
10:38:22 systemd: Starting Virtual filesystem service - GNOME Online Accounts monitor...
10:38:22 rtkit-daemon: Successfully made thread 2082 of process 1999 owned by '1000' RT at priority 5.
10:38:22 systemd: Started Virtual filesystem service - Media Transfer Protocol monitor.
10:38:22 rtkit-daemon: Supervising 5 threads of 2 processes of 2 users.
10:38:22 systemd: Starting Virtual filesystem service - Media Transfer Protocol monitor...
10:38:22 rtkit-daemon: Supervising 5 threads of 2 processes of 2 users.
10:38:22 systemd: Started Virtual filesystem service - disk device monitor.
10:38:22 rtkit-daemon: Successfully made thread 2077 of process 1465 owned by '125' RT at priority 5.
10:38:22 systemd: Starting Virtual filesystem service - disk device monitor...
10:38:22 rtkit-daemon: Supervising 4 threads of 2 processes of 2 users.
10:38:22 systemd: Started Virtual filesystem service.
10:38:22 rtkit-daemon: Supervising 5 threads of 2 processes of 2 users.
10:38:22 systemd: Starting Virtual filesystem service...
10:38:22 Xorg: (II) Using input driver 'libinput' for 'Logitech Wireless Keyboard PID:4023'
10:38:22 rtkit-daemon: Successfully made thread 2076 of process 1465 owned by '125' RT at priority 5.
10:38:22 systemd: Started Sound Service.
10:38:22 Xorg: (II) config/udev: Adding input device Logitech Wireless Keyboard PID:4023 (/dev/input/event3)
10:38:22 rtkit-daemon: Supervising 4 threads of 2 processes of 2 users.
10:38:22 systemd: Condition check resulted in Bluetooth service being skipped.
10:38:22 Xorg: (II) event0  - Sleep Button: device is a keyboard
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
10:38:22 systemd: Started D-Bus User Message Bus.
10:38:22 Xorg: (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:22 tracker-extract: Setting priority nice level to 19
10:38:22 Xorg: (II) Initializing extension SYNC
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
10:38:22 tracker-extract: Set scheduler policy to SCHED_IDLE
10:38:22 Xorg: (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:22 tracker-miner-f: Setting priority nice level to 19
10:38:22 Xorg: (II) LoadModule: "wfb"
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
10:38:22 tracker-miner-f: Set scheduler policy to SCHED_IDLE
10:38:22 Xorg: 	compiled for 1.20.3, module version = 1.0.16
10:38:22 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.OnlineAccounts'
10:38:22 systemd: Starting Tracker file system data miner...
10:38:21 Xorg: 	Entry deleted from font path.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gnome.Identity'
10:38:21 systemd: Starting Tracker metadata extractor...
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Activating service name='org.gnome.Identity' requested by ':1.9' (uid=1000 pid=2052 comm="/usr/libexec/goa-daemon " label="unconfined")
10:38:21 systemd: Started Session 2 of user mario.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Activating service name='org.gnome.OnlineAccounts' requested by ':1.8' (uid=1000 pid=2048 comm="/usr/libexec/gvfs-goa-volume-monitor " label="unconfined")
10:38:21 systemd: Starting Sound Service...
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:21 systemd: Started User Manager for UID 1000.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
10:38:21 systemd: Reached target Basic System.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:21 systemd: Reached target Sockets.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
10:38:21 systemd: Listening on D-Bus User Message Bus Socket.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:21 systemd: Listening on REST API socket for snapd user session agent.
10:38:21 dbus-daemon: [session uid=1000 pid=2005] Successfully activated service 'org.gtk.vfs.Daemon'
10:38:21 systemd: Listening on Sound System.
10:38:20 dbus-daemon: [session uid=1000 pid=2005] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.2' (uid=1000 pid=2001 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:38:20 systemd: Listening on debconf communication socket.
10:38:20 gdm-session-wor: gkr-pam: gnome-keyring-daemon started properly and unlocked keyring
10:38:20 systemd: Listening on GnuPG cryptographic agent and passphrase cache.
10:38:20 rtkit-daemon: Supervising 5 threads of 2 processes of 2 users.
10:38:20 systemd: Listening on GnuPG cryptographic agent (ssh-agent emulation).
10:38:20 rtkit-daemon: Successfully made thread 2012 of process 1999 owned by '1000' RT at priority 5.
10:38:20 systemd: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
10:38:20 rtkit-daemon: Supervising 4 threads of 2 processes of 2 users.
10:38:20 systemd: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
10:38:20 dbus-daemon: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.113' (uid=1000 pid=1999 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
10:38:20 systemd: Listening on GnuPG network certificate management daemon.
10:38:20 rtkit-daemon: Supervising 4 threads of 2 processes of 2 users.
10:38:19 systemd: Starting D-Bus User Message Bus Socket.
10:38:19 rtkit-daemon: Successfully made thread 1999 of process 1999 owned by '1000' high priority at nice level -11.
10:38:19 systemd: Reached target Timers.
10:38:17 dbus-daemon: [session uid=1000 pid=2005] AppArmor D-Bus mediation is enabled
10:38:17 systemd: Reached target Paths.
10:38:17 Xorg: (II) systemd-logind: got pause for 13:66
10:38:17 kernel: rfkill: input handler enabled
10:38:10 systemd: Started Pending report trigger for Ubuntu Report.
10:38:09 (systemd): pam_unix(systemd-user:session): session opened for user mario by (uid=0)
10:38:09 systemd: Starting User Manager for UID 1000...
10:38:09 systemd-logind: New session 2 of user mario.
10:38:09 systemd: Starting User Runtime Directory /run/user/1000...
10:38:09 gdm-session-wor: pam_unix(gdm-password:session): session opened for user mario by (uid=0)
10:38:05 kernel: logitech-hidpp-device 0003:046D:4054.0005: HID++ 4.5 device connected.
10:37:57 systemd: Started Fingerprint Authentication Daemon.
10:37:57 dbus-daemon: [system] Successfully activated service 'net.reactivated.Fprint'
10:37:57 systemd: Starting Fingerprint Authentication Daemon...
10:37:57 dbus-daemon: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.52' (uid=125 pid=1744 comm="/usr/bin/gnome-shell " label="unconfined")
10:37:56 upowerd: treating change event as add on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:046D:C534.0003/0003:046D:4023.0004/power_supply/hidpp_battery_0
10:37:55 kernel: logitech-hidpp-device 0003:046D:4023.0004: HID++ 2.0 device connected.
10:37:53 systemd: fprintd.service: Succeeded.
10:37:27 tracker-store: OK
10:37:24 systemd: Startup finished in 9.524s (kernel) + 3min 7.102s (userspace) = 3min 16.626s.
10:37:24 gnome-shell: Registering session with GDM
10:37:23 gsd-media-keys: Failed to grab accelerator for keybinding settings:hibernate
10:37:23 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:37:23 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:37:23 gnome-shell: cr_parser_new_from_buf: assertion 'a_buf && a_len' failed
10:37:23 gnome-shell: Getting invalid resource scale property
10:37:23 systemd: Started Fingerprint Authentication Daemon.
10:37:23 dbus-daemon: [system] Successfully activated service 'net.reactivated.Fprint'
10:37:23 systemd: Starting Fingerprint Authentication Daemon...
10:37:23 dbus-daemon: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.52' (uid=125 pid=1744 comm="/usr/bin/gnome-shell " label="unconfined")
10:37:23 gnome-shell: cr_declaration_parse_list_from_buf: assertion 'parser' failed
10:37:21 xbrlapi: cannot connect to braille devices daemon brltty at :0
10:37:21 gnome-session-b: Entering running state
10:37:20 kernel: rfkill: input handler disabled
10:37:20 systemd: Started Hostname Service.
10:37:20 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
10:37:20 gnome-shell: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
10:37:20 systemd: Starting Hostname Service...
10:37:20 gsd-sharing: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
10:37:20 dbus-daemon: dbus-daemon[1639]: [session uid=125 pid=1639] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
10:37:20 systemd: Started PackageKit Daemon.
10:37:20 dbus-daemon: [system] Successfully activated service 'org.freedesktop.PackageKit'
10:37:20 gnome-shell: Unable to connect to ibus: No se pudo conectar: Conexión rehusada
10:37:20 Xorg: (--) NVIDIA(GPU-0):
10:37:20 packagekitd: daemon start
10:37:20 dbus-daemon: dbus-daemon[1639]: [session uid=125 pid=1639] Successfully activated service 'org.gnome.Shell.Notifications'
10:37:19 systemd: Started Location Lookup Service.
10:37:19 dbus-daemon: [system] Successfully activated service 'org.freedesktop.GeoClue2'
10:37:19 systemd: Starting PackageKit Daemon...
10:37:19 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.52' (uid=125 pid=1744 comm="/usr/bin/gnome-shell " label="unconfined")
10:37:19 polkitd: Registered Authentication Agent for unix-session:c1 (system bus name :1.52 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale es_PE.UTF-8)
10:37:19 systemd: Starting Location Lookup Service...
10:37:19 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.GeoClue2' unit='geoclue.service' requested by ':1.52' (uid=125 pid=1744 comm="/usr/bin/gnome-shell " label="unconfined")
10:37:12 at-spi2-registr: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
10:37:12 dbus-daemon: dbus-daemon[1677]: Successfully activated service 'org.a11y.atspi.Registry'
10:37:11 systemd: Started Locale Service.
10:37:11 dbus-daemon: [system] Successfully activated service 'org.freedesktop.locale1'
10:37:11 systemd: Starting Locale Service...
10:37:11 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service' requested by ':1.52' (uid=125 pid=1744 comm="/usr/bin/gnome-shell " label="unconfined")
10:37:10 gnome-shell: Will monitor session c1
10:37:06 systemd: Finished Rotate log files.
10:37:06 rsyslogd: [origin software="rsyslogd" swVersion="8.2001.0" x-pid="972" x-info="https://www.rsyslog.com"] rsyslogd was HUPed
10:37:04 colord: failed to get session [pid 1782]: No hay datos disponibles
10:37:04 systemd: Started CUPS Scheduler.
10:37:03 rtkit-daemon: Supervising 3 threads of 1 processes of 1 users.
10:37:03 Xorg: (II) NVIDIA(0): Setting mode "HDMI-0: nvidia-auto-select @1600x900 +1600+0 {ViewPortIn=1600x900, ViewPortOut=1600x900+0+0}, DP-1: nvidia-auto-select @1600x900 +0+0 {ViewPortIn=1600x900, ViewPortOut=1600x900+0+0}"
10:37:03 rtkit-daemon: Supervising 3 threads of 1 processes of 1 users.
10:37:03 Xorg: (II) NVIDIA(0): Setting mode "HDMI-0: nvidia-auto-select @1600x900 +0+0 {ViewPortIn=1600x900, ViewPortOut=1600x900+0+0}, DP-1: nvidia-auto-select @1600x900 +0+0 {ViewPortIn=1600x900, ViewPortOut=1600x900+0+0}"
10:37:00 systemd: tracker-extract.service: Succeeded.
10:36:58 dbus-daemon: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
10:36:53 systemd: Started MySQL Community Server.
10:36:51 dbus-daemon: dbus-daemon[1639]: [session uid=125 pid=1639] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
10:36:51 gnome-session-b: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
10:36:51 dbus-daemon: dbus-daemon[1639]: [session uid=125 pid=1639] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
10:36:48 systemd: Startup finished in 1min 1.070s.
10:36:48 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.freedesktop.Tracker1'
10:36:47 systemd: Reached target Main User Target.
10:36:47 dbus-daemon: [session uid=125 pid=1486] Activating via systemd: service name='org.freedesktop.Tracker1' unit='tracker-store.service' requested by ':1.2' (uid=125 pid=1467 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:36:46 systemd: Started Daemon for power management.
10:36:46 dbus-daemon: [system] Successfully activated service 'org.freedesktop.UPower'
10:36:46 systemd: Starting Daemon for power management...
10:36:46 dbus-daemon: dbus-daemon[1639]: [session uid=125 pid=1639] Successfully activated service 'org.a11y.Bus'
10:36:45 systemd: Started Virtual filesystem service - Apple File Conduit monitor.
10:36:45 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
10:36:45 systemd: Starting Virtual filesystem service - Apple File Conduit monitor...
10:36:45 dbus-daemon: [session uid=125 pid=1486] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.2' (uid=125 pid=1467 comm="/usr/libexec/tracker-miner-fs " label="unconfined")
10:36:45 systemd: Started Virtual filesystem service - digital camera monitor.
10:36:45 dbus-daemon: [session uid=125 pid=1486] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
10:36:45 systemd: Starting Virtual filesystem service - digital camera monitor...

```

---

### Post by dragonfly41 on 2021-10-09
If you use glogg as I suggested you can scan the logs yourself looking for keywords such as 

Failed
Succeeded
error
fail
connect
FIXME
snap
Permission denied
WARNING
digital camera
Starting Fingerprint Authentication Daemon



I would try disconnecting some of the peripherals (camera, fingerprint reader etc.) for a term to see if you still experience freezing.

This is all just basic detective work, looking for clues.

A basic process of elimination.

Another tip.

I would investigate using inotifywait and iwatch

[https://medium.com/100-days-of-linux/an-introduction-to-file-system-monitoring-tools-afd99164ce66](https://medium.com/100-days-of-linux/an-introduction-to-file-system-monitoring-tools-afd99164ce66)

inotifywait and iwatch

This way you can watch various files and try to correlate accessing a particular file or app with exact time of freezing.

In fact it occurs to me that there is scope for a desktop script to help in such detective work, harnessing existing tools.

---

### Post by waffen on 2021-10-09
I installed the program and it does basically the same thing that I already did with a Notepad and the option to search haha

My problem is: I am a software and website developer, but I am not an expert in the internal details of Ubuntu, that is why reading the log is for me many times like trying to read Martian: D; that's why I asked advanced users for help here.

I don't have any peripherals installed.

Reading the log again, I see that the latest errors reported have to do with Firefox, it could be the cause, since many times in the past it crashed or when watching YouTube videos it ate the RAM memory and had to restart the PC. I use it intensively for my work (+20 tabs open all the time)

I'm going to have to test Chrome for a while and see if the problem persists.

Thanks for the help!

---

### Post by dragonfly41 on 2021-10-09
Even long term users are puzzled by syslog language. It is like Klingon language.

I am only reading what logs you posted for clues and it does refer to peripherals so are you running the drivers or apps?
You can of course use any app to search logs. I suggested just one .. up to you.

Firefox tabs has been a source of bother to me. Good idea to try other browsers although there is heavy memory payload for each tab (as Stacer would show). But you have 16 GB .. don't know what swap you have. Also try a new guest account with minimal resources running.  You just need to eliminate clues.

---

### Post by waffen on 2021-10-09
Using Chrome for watch Youtube: after 5 minutes of video my system freeze again :lolflag:  9% RAM used in that moment  only Chrome open with a few tabs...](*,)

The only peripherals is an HP printer(off all the time) 

The only weird things I have installed:
- Compiled Nvidia drivers (CUDA etc) for programming tasks. Installed the official driver from Ubuntu repositories too.
- Steam + Proton to be able to play Windows games.
- LAMP server
- PostgreSQL
The last ones I have always used without problem.
If this continues I'm going to have to reinstall everything, I don't have the time to play detective mainly because I don't understand the logs.

Swype: 2GB 

This time I get a lot of these error messages:
```
nautilus: connect() failed
```

but no more info...

```

12:37:39 nautilus: connect() failed
12:35:02 cron: pam_unix(cron:session): session closed for user root
12:35:01 nautilus: connect() failed
12:33:05 kernel: Normal exit (0 jobs run)
12:33:05 kernel: Anacron 2.3 started on 2021-10-09
12:33:05 systemd: anacron.service: Succeeded.
12:33:04 nautilus: connect() failed
12:30:01 cron: pam_unix(cron:session): session closed for user root
12:30:01 nautilus: connect() failed
12:28:51 cat: [18264:18267:1009/122851.574564:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -107
12:28:50 nautilus: connect() failed
12:26:41 systemd: snap.canonical-livepatch.canonical-livepatch.ce676e2d-2688-4344-ab4f-b29f5e48b0d2.scope: Succeeded.
12:26:40 nautilus: connect() failed
12:26:39 canonical-livep: client information is recent, not refreshing
12:26:38 nautilus: connect() failed
12:26:38 canonical-livep: Checking with livepatch service.
12:26:37 nautilus: connect() failed
12:25:02 cron: pam_unix(cron:session): session closed for user root
12:25:02 kernel: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
12:25:01 cron: pam_unix(cron:session): session opened for user root by (uid=0)
12:25:01 nautilus: connect() failed
12:23:13 gnome-shell: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3400623 specified for 0x340005d.
12:23:12 nautilus: connect() failed
12:23:12 gnome-shell: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3400623 specified for 0x340005d.
12:23:11 nautilus: connect() failed
12:23:11 gnome-shell: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3400623 specified for 0x340005d.
12:23:10 nautilus: connect() failed
12:23:10 gnome-shell: Window manager warning: Invalid WM_TRANSIENT_FOR window 0x34004a5 specified for 0x340005d.
12:23:09 nautilus: connect() failed
12:22:00 cat: [18264:18267:1009/122200.488952:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:59 nautilus: connect() failed
12:21:59 cat: [18264:18267:1009/122159.584536:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:58 nautilus: connect() failed
12:21:57 cat: [18264:18267:1009/122157.128019:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:56 nautilus: connect() failed
12:21:56 cat: [18264:18267:1009/122156.806790:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:55 nautilus: connect() failed
12:21:54 cat: [18264:18267:1009/122154.645133:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:53 nautilus: connect() failed
12:21:53 cat: [18264:18267:1009/122153.681127:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:52 nautilus: connect() failed
12:21:52 cat: [18264:18267:1009/122152.336893:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:51 nautilus: connect() failed
12:21:51 cat: [18264:18267:1009/122151.491000:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:50 nautilus: connect() failed
12:21:50 cat: [18264:18267:1009/122150.238141:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:49 nautilus: connect() failed
12:21:49 cat: [18264:18267:1009/122149.234276:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:48 nautilus: connect() failed
12:21:46 cat: [18264:18267:1009/122146.930606:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:46 nautilus: connect() failed
12:21:46 cat: [18264:18267:1009/122146.783705:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:45 nautilus: connect() failed
12:21:45 cat: [18264:18267:1009/122145.270333:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:44 nautilus: connect() failed
12:21:32 cat: [18264:18267:1009/122132.170207:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:31 nautilus: connect() failed
12:21:31 cat: [18264:18267:1009/122131.520364:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:30 nautilus: connect() failed
12:21:28 cat: [18264:18267:1009/122128.839972:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:21:27 nautilus: connect() failed
12:21:27 cat: [18264:18267:1009/122127.145113:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:26 nautilus: connect() failed
12:21:26 cat: [18264:18267:1009/122126.819658:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:25 nautilus: connect() failed
12:21:24 cat: [18264:18267:1009/122124.990643:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:24 nautilus: connect() failed
12:21:22 cat: [18264:18267:1009/122122.833876:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:21 nautilus: connect() failed
12:21:20 cat: [18264:18267:1009/122120.271647:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:19 nautilus: connect() failed
12:21:17 cat: [18264:18267:1009/122117.702606:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:16 nautilus: connect() failed
12:21:14 cat: [18264:18267:1009/122114.329098:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:13 nautilus: connect() failed
12:21:13 cat: [18264:18267:1009/122113.156400:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:12 nautilus: connect() failed
12:21:10 cat: [18264:18267:1009/122110.579020:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:09 nautilus: connect() failed
12:21:08 cat: [18264:18267:1009/122108.560853:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:07 nautilus: connect() failed
12:21:05 cat: [18264:18267:1009/122105.996628:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:05 nautilus: connect() failed
12:21:01 cat: [18264:18267:1009/122101.781841:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:21:00 nautilus: connect() failed
12:20:56 cat: [18264:18267:1009/122056.890372:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:55 nautilus: connect() failed
12:20:55 cat: [18264:18267:1009/122055.006869:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:54 nautilus: connect() failed
12:20:54 cat: [18264:18267:1009/122054.717730:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:53 nautilus: connect() failed
12:20:43 cat: [18264:18267:1009/122043.785615:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:42 nautilus: connect() failed
12:20:42 cat: [18264:18267:1009/122042.542094:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:41 nautilus: connect() failed
12:20:41 cat: [18264:18267:1009/122041.553795:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:40 nautilus: connect() failed
12:20:37 cat: [18264:18267:1009/122037.687049:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:20:36 nautilus: connect() failed
12:20:03 cat: Fontconfig error: Cannot load default config file: No such file: (null)
12:20:02 nautilus: connect() failed
12:19:30 cat: [18264:18267:1009/121930.899959:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:19:30 nautilus: connect() failed
12:19:30 cat: [18264:18267:1009/121930.387510:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:19:29 nautilus: connect() failed
12:19:26 cat: [18264:18267:1009/121926.915010:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:19:26 nautilus: connect() failed
12:19:24 cat: [18264:18267:1009/121924.232830:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:19:23 nautilus: connect() failed
12:19:21 cat: [18264:18267:1009/121921.690748:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:19:20 nautilus: connect() failed
12:19:19 cat: [18264:18267:1009/121919.012859:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:19:18 nautilus: connect() failed
12:19:16 cat: [18264:18267:1009/121916.497286:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:19:15 nautilus: connect() failed
12:19:14 cat: [18264:18267:1009/121914.366983:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -202
12:19:13 nautilus: connect() failed
12:19:13 cat: [18264:18267:1009/121913.842690:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:19:12 nautilus: connect() failed
12:18:31 cat: [18264:18267:1009/121831.035786:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:18:30 nautilus: connect() failed
12:18:28 cat: [18264:18267:1009/121828.335664:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:18:27 nautilus: connect() failed
12:18:26 cat: [18264:18267:1009/121826.365741:ERROR:ssl_client_socket_impl.cc(981)] handshake failed; returned -1, SSL error code 1, net_error -200
12:18:25 nautilus: connect() failed
12:17:54 systemd: Started Application launched by gnome-shell.
12:17:53 nautilus: connect() failed
12:17:02 cron: pam_unix(cron:session): session closed for user root
12:17:02 kernel: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
12:17:01 cron: pam_unix(cron:session): session opened for user root by (uid=0)
12:17:01 nautilus: connect() failed
12:16:30 gnome-shell: Some code accessed the property 'discreteGpuAvailable' on the module 'appDisplay'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.

```

---

### Post by dragonfly41 on 2021-10-10
Regarding heavy usage of memory for each tab session I have less than your 16GB RAM - only 8GB - and yet I am able to refer to hundreds of tabs. in Chrome current count is 600 (admittedly this is too high and I am reaching the point where I will archive them since some are in "rarely used" group in Group Your Tags.

I manage by leveraging some Chrome extensions (they require different access options to be agreed).

- The Marvellous Suspender - which puts unused tabs to sleep.
- Zotero Connector - links to Zotero standalone library of resources
- One Tab - saves all tabs into a single tab but keeps tabs
- Session Buddy - use to dump tabs from time to time as a regular backup
- Group Your Tabs - puts tabs into like groups
- Tab-Sidebar - popup sidebar of all tabs

The general idea is to only use tabs as needed. They do not all need to be active.

But I do not suspect that tabs are causing your freezes. You have healthy RAM size.

Try running a LiveUSB for a time to see if you have freezes.

---

### Post by waffen on 2021-10-10
> **dragonfly41 said:**
> Regarding heavy usage of memory for each tab session I have less than your 16GB RAM - only 8GB - and yet I am able to refer to hundreds of tabs. in Chrome current count is 600 (admittedly this is too high and I am reaching the point where I will archive them since some are in "rarely used" group in Group Your Tags.

I manage by leveraging some Chrome extensions (they require different access options to be agreed).

- The Marvellous Suspender - which puts unused tabs to sleep.
- Zotero Connector - links to Zotero standalone library of resources
- One Tab - saves all tabs into a single tab but keeps tabs
- Session Buddy - use to dump tabs from time to time as a regular backup
- Group Your Tabs - puts tabs into like groups
- Tab-Sidebar - popup sidebar of all tabs

The general idea is to only use tabs as needed. They do not all need to be active.

But I do not suspect that tabs are causing your freezes. You have healthy RAM size.

Try running a LiveUSB for a time to see if you have freezes.

600?? You mean 60 right? :P
I really don't like Chrome because of his Tab management and he eats a lot of RAM compared to Firefox. Yesterday I have gmail, a chess page and google open + youtube and Chrome crash and freeze my PC.

Are you using adblock? I have in both browsers uBlock Origin.

In previous installations Firefox hangs when I have too many tabs opens and running (+20) +  a Youtube video running and eat ALL the RAM, so I need turn off/on PC, but In the monitors I could see +99% of RAM eated alone by FF... in this case my RAM is 10-20% max, so this time is another thing.

The only different thing in this installation is that it compiles drivers for Nvidia: cudnn for programming and to be able to run a chess program lc0

I have a project to deliver these days and I do not have time to investigate much more the reason for the problems. Also as I said after reading the logs, I don't understand much of them.

The freeze can happens after 15 minutes, like yesterday or in one day I don't have any. 

@dragonfly41 thanks for your time, I really appreciate your help!

---

### Post by waffen on 2021-10-10
Another thing I notice is: PC freezes when the screen protector is active (win+L)

---

### Post by dragonfly41 on 2021-10-10
[COLOR=#000000]600?? You mean 60 right?

No .. current show in Tab-Sidebar is .. 608 tabs .. mostly sleeping until I need some in play.

Now and again I dump these using Session Buddy and this is great for archiving them.

I don't use Firefox too much these days but some years back there was a similar extension Tab Groups Helper.

You mention "[/COLOR][COLOR=#000000]monitors" .. so you have multiple monitors?
Again I would try reconfiguring to a single monitor to see if this makes a difference.
Troubleshooting freezes, I find, is one of the toughest challenges.

I can only suggest pare down processes, test, then gradually add and test again. It is trial and error.[/COLOR]

---

### Post by waffen on 2021-10-10
OMG!! 608???? And I thought that having 40 tabs open I was crazy hahahaha

In my case I have 4-6 pinned tabs the rest is not active at the open.

Monitors: Yes I have 2: one connected to the HDMI port and the other to the DVI port into the Nvidia card.

---

### Post by waffen on 2021-10-11
Today 2 freezes in a row, one when I go to lunch and the other 1 hour later, I left my PC ON. 

I'm attaching images (links from my personal cloud) with the last messages from the logs.

Can someone help me?? I don't want to reinstall all...

[https://cloud.lacunza.biz/index.php/s/wpQygSxJkqrqyRZ]("https://cloud.lacunza.biz/index.php/s/wpQygSxJkqrqyRZ")

[https://cloud.lacunza.biz/index.php/s/62d2KoYcb3cJNfm]("https://cloud.lacunza.biz/index.php/s/62d2KoYcb3cJNfm")

---

### Post by dragonfly41 on 2021-10-11
Next .. try looking in $HOME/[FONT=monospace][COLOR=#000000].xsession-errors[/COLOR]

[/FONT]

---

### Post by waffen on 2021-10-11
> **dragonfly41 said:**
> Next .. try looking in $HOME/[FONT=monospace][COLOR=#000000].xsession-errors[/COLOR]

[/FONT]

I don't have that folder/file

---

### Post by tea for one on 2021-10-11
> **waffen said:**
> I don't have that folder/file

It's a hidden file in your user directory.
You may need to check the box in your file manager [COLOR="#0000FF"]Show Hidden Files[/COLOR]

---

### Post by waffen on 2021-10-11
> **tea for one said:**
> It's a hidden file in your user directory.
You may need to check the box in your file manager [COLOR="#0000FF"]Show Hidden Files[/COLOR]

Oh yes I know that, I just double check and my PC don't have that file.

You can activate it too using Ctrl+H 

I just run this command just in case and nothing...

```

mario@mario:~$ find /home/mario/ -iname xsession-errors
mario@mario:~$ find /home/mario/ -iname .xsession-errors

```

---

### Post by dragonfly41 on 2021-10-12
Troubleshooting freeze

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)


Going back to your post#1, I see that you list only 3GB for your hard drive ... seems to be a flash drive.

> I took the HD out of the old PC and put it in the new one and it still gives the same problem

I think that you are pushing your luck.

[https://askubuntu.com/questions/1259731/is-a-3-gb-usb-enough-for-installing-ubuntu](https://askubuntu.com/questions/1259731/is-a-3-gb-usb-enough-for-installing-ubuntu)

I would buy a normal size HDD or SSD to use.

I run Ubuntu 20.04 in an external SSD 1 TB in a docking bay via USB 3.0 connection.
You will need another for backup.   I have two SSD 1 TB.

---

### Post by vmpx on 2021-10-12
Try disable in browser "use hardware acceleration".

---

### Post by waffen on 2021-10-12
> **dragonfly41 said:**
> Troubleshooting freeze

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)


Going back to your post#1, I see that you list only 3GB for your hard drive ... seems to be a flash drive.



I think that you are pushing your luck.

[https://askubuntu.com/questions/1259731/is-a-3-gb-usb-enough-for-installing-ubuntu](https://askubuntu.com/questions/1259731/is-a-3-gb-usb-enough-for-installing-ubuntu)

I would buy a normal size HDD or SSD to use.

I run Ubuntu 20.04 in an external SSD 1 TB in a docking bay via USB 3.0 connection.
You will need another for backup.   I have two SSD 1 TB.

OMG! That was a typo! I just change it, correct info:

3TB == 2TB HD + 1TB HD

I have 2 HD, the 2TB is a new one (6 months of use, new installation) the one with this problem, the other one have another Ubuntu 20.04 installed +  Windows 10 (dual boot) and running with zero issues. 

The only difference between 1TB vs 2TB is: in the new one I can compile the cudnn nvidia program for run a chess analysis program Lc0 

and I have in the new one Steam with Proton (I can run windows only games with it)  but  don't think that's the issue. 

If the problem is caused by cudnn, I'll need to reinstall all ](*,)  but I can't found in the logs files any clue about it... I'm blindness.

---

### Post by waffen on 2021-10-12
> **vmpx said:**
> Try disable in browser "use hardware acceleration".

I have in Firefox:

layers.acceleration.force-enabled = false

so it's disable... maybe do I need to enable it? ::

[https://ubuntuhandbook.org/index.php/2021/08/enable-hardware-video-acceleration-va-api-for-firefox-in-ubuntu-20-04-18-04-higher/]("https://ubuntuhandbook.org/index.php/2021/08/enable-hardware-video-acceleration-va-api-for-firefox-in-ubuntu-20-04-18-04-higher/")

I have a dedicated Nvidia video card, but the motherboard have an internal intel one (I guess) and if I'm not wrong all the freezes happens with the browser open or using it (Firefox or Chrome), I'll try this path...

---

### Post by waffen on 2021-10-13
And happens again ](*,)

In the next image you can see the last problem reported, nautilus trying to connect to something and fail, the last log is plagued of that error message... 

Where can I see more info about that error?

[https://cloud.lacunza.biz/index.php/s/Gw9iWzE6NQjKB8W]("https://cloud.lacunza.biz/index.php/s/Gw9iWzE6NQjKB8W")

---

### Post by dragonfly41 on 2021-10-13
It is an ongoing guessing game. I can only suggest that it would be rare if you were the only person with such issues.

First study how to make refined google searches by using google search operators.

[https://ahrefs.com/blog/google-advanced-search-operators/](https://ahrefs.com/blog/google-advanced-search-operators/)

Then examine your errors and try to search ..
google .. typically

nautilus NEAR connect() failed

and you *might* be lucky ...


[https://gitlab.gnome.org/GNOME/nautilus/-/issues/233](https://gitlab.gnome.org/GNOME/nautilus/-/issues/233)

> After running sudo apt purge nautilus-extension-brasero nautilus-megasync the warning message (connect() failed) was gone.    

More than that I do not know. It might have been easier to reinstall.

---

### Post by waffen on 2021-10-13
My daily work depends on knowing how to use Google, but I was refining the search only for "Ubuntu + [KW]", in short, I deactivated my personal Nextcloud account (I doubt that it is the problem) in case it took time my VPS to synchronize with Nautilus.

When executing the command you recommend, it only purged Megasync and it also did not have it connected.

I will continue to test what happens with these changes, otherwise I am ready (and resigned) to do a complete reinstall

---

### Post by waffen on 2021-10-13
and again @dragonfly41 thanks a lot for your time!

---

### Post by tea for one on 2021-10-14
In post 24, your image shows that you have a lot of Desktop icons.
In the link [https://gitlab.gnome.org/GNOME/nautilus/-/issues/233](https://gitlab.gnome.org/GNOME/nautilus/-/issues/233) kindly supplied by [COLOR="#0000FF"]dragonfly41[/COLOR], there is the comment
> P.S. I noticed that this warning is generated only when "Show icons on desktop" option in gnome-tweak-tool is enabled.

Have you tried this?

Alternatively, can you temporarily remove all your desktop icons and see what happens?
Possibly, disable all gnome extensions?

---

### Post by dragonfly41 on 2021-10-14
Here is an *old *article referring to 18.04 .. but it might resonate with your experience .. 

[https://medium.com/@gspasov2/how-to-fix-ubuntu-18-04-lts-random-freezes-52bb75d55c70](https://medium.com/@gspasov2/how-to-fix-ubuntu-18-04-lts-random-freezes-52bb75d55c70)

Broad idea is to try another kernel

uname -a

---

### Post by vmpx on 2021-10-14
Someone from a german ubuntu forum had an issue with graphic in 20.04 and as he began to boot with kernel 5.4 instead of 5.11 the issue was gone.

---

### Post by waffen on 2021-10-14
> **vmpx said:**
> Someone from a german ubuntu forum had an issue with graphic in 20.04 and as he began to boot with kernel 5.4 instead of 5.11 the issue was gone.

Well, a lot of help now!! Haha thanks to all!! 

I can't do that, I have only installed:
5.11.0.37
5.11.0.36

I installed this Ubuntu in July...

---

### Post by waffen on 2021-10-14
> **tea for one said:**
> In post 24, your image shows that you have a lot of Desktop icons.
In the link [https://gitlab.gnome.org/GNOME/nautilus/-/issues/233](https://gitlab.gnome.org/GNOME/nautilus/-/issues/233) kindly supplied by [COLOR="#0000FF"]dragonfly41[/COLOR], there is the comment


Have you tried this?

Alternatively, can you temporarily remove all your desktop icons and see what happens?
Possibly, disable all gnome extensions?

Till now and after the purge command I did yesterday I can't see anymore that "connect fail" message in the logs, so I think it's fixed now.... I can't believe the cause was an inactive Megasync app. I'll continue check my PC, since yesterday no freezes.

I have active Desktop Icons but there are only Home/Trash system icons there, the rest are my files and folders located in $HOME/Desktop... but if I need to delete all of them maybe I need to change of distro LOL

I'll going to test one by one each advice write here, thanks again to all!

---

### Post by waffen on 2021-10-14
> **dragonfly41 said:**
> Here is an *old *article referring to 18.04 .. but it might resonate with your experience .. 

[https://medium.com/@gspasov2/how-to-fix-ubuntu-18-04-lts-random-freezes-52bb75d55c70](https://medium.com/@gspasov2/how-to-fix-ubuntu-18-04-lts-random-freezes-52bb75d55c70)

Broad idea is to try another kernel

uname -a

I have available these ones:

[https://cloud.lacunza.biz/index.php/s/aztfKL62cCLnf5X]("https://cloud.lacunza.biz/index.php/s/aztfKL62cCLnf5X")

```
mario@mario:~$ uname -a
Linux mario 5.11.0-37-generic #41~20.04.2-Ubuntu SMP Fri Sep 24 09:06:38 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by dragonfly41 on 2021-10-14
This article might help ..

[https://www.systutorials.com/how-to-make-grub2-boot-to-older-kernel-version-in-ubuntu-20-04/](https://www.systutorials.com/how-to-make-grub2-boot-to-older-kernel-version-in-ubuntu-20-04/)


e.g. run this command

[FONT=monospace][COLOR=#000000]sudo grub-mkconfig | grep -E 'submenu |menuentry '

[/COLOR]I see multiple choices in my menu since I have multiple SSD's with different versions.

[/FONT]But if your freezing has gone there is no need to change kernel.

You should see a recovery option in your grub menu. I also have installed rEFInd which I find useful to boot up.

---

### Post by waffen on 2021-10-14
The first freeze of the day... with all my screens open (included FF) I go out, screensaver start and when I comeback PC is freeze.

in this screenshot:

[https://cloud.lacunza.biz/index.php/s/jCaASQZfpkTLDmj]("https://cloud.lacunza.biz/index.php/s/jCaASQZfpkTLDmj")

You can see the last 3 problems reported by the log are related to cron jobs, so checking /etc/cron.d and compared it with my old HD I can see a new file: sysstat, that file contain this command:

```
5-55/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1
```

the one already reported like a problem in log.

I don't remember install it or maybe another software use it... I just move that file to anther folder and I'll make another test.

---

### Post by waffen on 2021-10-14
Again another freeze.. Im tired! 

Tomorrow I'll going to backup all and reinstall the system.

What do you think is better? 20.04 o 21.10? 

Thanks to all for your time and help!

---

### Post by vmpx on 2021-10-15
To install the 5.4 kernel in 20.04 you have only to execute:
```
sudo apt install linux-generic
```

---

### Post by waffen on 2021-10-15
> **vmpx said:**
> To install the 5.4 kernel in 20.04 you have only to execute:
```
sudo apt install linux-generic
```

Uhmm... Could that affect other software compiled against the old kernel? for example nvidia drivers?

Is there a way to auto-load that kernel and not the newer one at boot?

---

### Post by tea for one on 2021-10-15
> **waffen said:**
> Is there a way to auto-load that kernel and not the newer one at boot?

Yes, there is, however, precise instructions depend on how many systems and kernels you have.

You have to edit /etc/default/grub (with elevated privileges)
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0 [COLOR="#0000FF"]This is the default - 0 means the first line in the Grub menu[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_DISABLE_OS_PROBER=true

```
Example below with an alternative default
```
GRUB_DEFAULT=[COLOR="#0000FF"]"1>2"[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_DISABLE_OS_PROBER=true
```

[COLOR="#0000FF"]1[/COLOR] in "1>2" indicates the second entry of the main menu (Advanced Options)
[COLOR="#0000FF"]2[/COLOR] in "1>2" indicates the third entry of the submenu.

When you are happy with your choice, run in the terminal
```
sudo update-grub
```

Back up your existing /etc/default/grub so that you can go back to the beginning in the event of an error.
Remember - Grub counts from 0

---

### Post by waffen on 2021-10-15
@tea for one  OK thanks!

Well I'll going to install that kernel and make the tests... I really hate reinstall all and config / compile libs again...

I'll going to update this thread.

---

### Post by waffen on 2021-10-15
I just installed the old kernel and... all was broken when I restart the PC, screen at 600*480 res, only recognize 1 monitor (HDMI) the other one not even listed... I know it's because the Nvidia drivers are not compiled against that kernel (right??)

Monday I start a new project and I can't expend more time in this problem, I'll going to format and reinstall the hole system ](*,)

Really a BIG THANKS!! to all of you for your time and help! I really appreciate it! 

Saludos!! // Greetings!

Mario

---

### Post by vmpx on 2021-10-15
You can boot to the kernel 5.11 in GRUB by pressing 'e' after you have chosen the entry for 20.04 and entering the version number for vmlinuz-5.11.0-37-generic and initrd.img-5.11.0-37-generic.

---

### Post by vmpx on 2021-10-15
I found following in Web:

> Ubuntu &#8211; 20.04 Focal &#8211; Nvidia driver no longer loading with kernel 5.4.0-42

driverskernelnvidia

   On Ubuntu 20.04 Focal, I upgraded to kernel 5.4.0-42 (using the Software Updater GUI / apt) and my Nvidia proprietary drivers stopped working.

   Rebooting to the old kernel (5.4.0-40) yields a working system, so it is clear that the kernel update was the trigger for the problem.

  Installing the headers with:
sudo apt install linux-headers-5.4.0-42-generic

   caused apt to automatically recompile the nvidia kernel module for the new kernel. After a reboot to the new kernel, everything just worked.

I'm not sure why headers weren't installed automatically (I believe they usually are?). Perhaps there is a problem with the apt package for the new kernel?

This happened on the 20.04 Focal release.

so one have to execute:
```
sudo apt install linux-headers-generic
```
to recomplie the nividia kernel module for the 5.4 kernel.

---

### Post by waffen on 2021-10-15
Hi again... guess...  yes! Again the freezes!! 

I just format + clean installation of the last Ubuntu version, I notice the installer don't create a swap partition but in the system monitor I can see 2GB for swap... well...

The only thing I installed was the Nvidia driver 470.63.01  start Firefox (not login into my profile so no extensions installed) and start watching videos.. system freezes.  Log image attached

[https://cloud.lacunza.biz/index.php/s/q599Tt85Zox77TX]("https://cloud.lacunza.biz/index.php/s/q599Tt85Zox77TX")

What do you think? is it the driver? do I need to install the other one available? v. 460?

List of drivers:
[https://cloud.lacunza.biz/index.php/s/XFk2BAa94wt8jx3]("https://cloud.lacunza.biz/index.php/s/XFk2BAa94wt8jx3")

I'll keep my pc ON but with the Firefox closed...

---

### Post by waffen on 2021-10-16
Ok I just install the 460 driver all fine  I put a long video running, fine till the screen go black or I press win +H to activate the screen protector... Looks like it's the problem. 
I see the same problem many times with other driver too.

Any ideas?

---

### Post by vmpx on 2021-10-16
My idea was to install 5.4 kernel in 20.04:
```
sudo apt install linux-generic linux-headers-generic
```
boot into 5.4 kernel and install the nvidia driver if not done automatically.

---

### Post by tea for one on 2021-10-16
> **waffen said:**
> I just format + clean installation of the last Ubuntu version, I notice the installer don't create a swap partition but in the system monitor I can see 2GB for swap... well.

Recent Ubuntu versions create a swap file instead of a swap partition.
```
edited@edited:/$ ls
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  [COLOR="#0000FF"]swapfile[/COLOR]  usr
edited@edited:/$ 
```

---

### Post by vmpx on 2021-10-16
what results in after the screen go black or freeze:```
dmesg|grep nouveau
```

---

### Post by waffen on 2021-10-16
> **tea for one said:**
> Recent Ubuntu versions create a swap file instead of a swap partition.
```
edited@edited:/$ ls
bin    dev   lib    libx32      mnt   root  snap      sys  var
boot   etc   lib32  lost+found  opt   run   srv       tmp
cdrom  home  lib64  media       proc  sbin  [COLOR="#0000FF"]swapfile[/COLOR]  usr
edited@edited:/$ 
```

Oh! I'm from the old school :lolflag: 

I have that file, thanks!

---

### Post by waffen on 2021-10-16
> **vmpx said:**
> what results in after the screen go black or freeze:```
dmesg|grep nouveau
```

Nothing shows...

---

### Post by waffen on 2021-10-16
Update: I just test all the morning using my Windows 10 HD in the same PC, no problems at all! So it's not a HW issue, the problem is only in Ubuntu =d>

---

### Post by waffen on 2021-10-16
> **vmpx said:**
> My idea was to install 5.4 kernel in 20.04:
```
sudo apt install linux-generic linux-headers-generic
```
boot into 5.4 kernel and install the nvidia driver if not done automatically.

I just did it and the same problem: I just open FF play a video and Win + L and after a few time PC freeze...

---

### Post by vmpx on 2021-10-16
I found this in Web:
> PSA: If your system freezes randomly and you have a Nvidia GPU w/ proprietary drivers, it's a driver bug

Nvidia driver version 455 or newer has a bug that causes the system to freeze randomly. I have seen reports that this issue occurs on Arch and Arch-based
   distros (such as Manjaro). If you have this problem, downgrade the driver to version 450 until a fix becomes available.

---

### Post by waffen on 2021-10-16
Now this is my final post in this thread: I can manage to continue with my job.

I read in other website about similar error caused by the Notification system,  just disable it in the block screen. I test it and during 1.20 hrs all was fine till a new freeze happens.

So like I said before, next Monday I need to start a new project, so I can't expend more time on this, so I decide to work in Windows! 

HAHAHAHAHA NAAAAAAAA..... :lolflag:

So I think the fix for the issue is something related to my previous lines....Now I just install Ubuntu 21.10 and .... yes!! it's working PERFECT!! More than 2 hours of test and nothing happens, just clean new installation with nothing more installed just the latest Nvidia driver...So I want to mark this post like Closed but Not Fixed.

Again, thank you so much to all the friends here trying to help with ideas and the time all of you expend on this large thread! **Se los agradezco de corazón!! **

Mario

---

### Post by vmpx on 2021-10-17
[B]How to fix Ubuntu 20.04 freeze after boot when NVIDIA card installed
[/B]
Replace in GRUB menu for 20.04 ”quiet splash” with ”quiet splash  nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.                 

(originally written for 18.04)

---

### Post by waffen on 2021-10-17
> **vmpx said:**
> [B]How to fix Ubuntu 20.04 freeze after boot when NVIDIA card installed
[/B]
Replace in GRUB menu for 20.04 ”quiet splash” with ”quiet splash  nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.                 

(originally written for 18.04)

I just uninstall 20.04, 21.10 is working perfect for me, thanks!

---

### Post by slaytanicprion on 2021-12-29
I only experienced this issue when being on a live session from a USB stick (no matter the quality), sometime it will just freeze. On a HDD no. I'll soon say how it goes on an nvme SSD when I decide to install the pci-e adapter (my mobo came out when nvme sdd's didn't exist yet, there was pci-e SSD's but they were 12K for a 25gb heh. I got this 512gb Corsair nvme SSD and I need to install the pcie-e adapter...I'm thrilled for it, yeah I'll be limited since mobo has pcie 2.0, but 2000MB/sec is still way better than the other SATA ssd I have but haven't installed yet either WD Blue at 560MB/sec maximum, marginally better than the mechanical HD I have Ubuntu MATE installed on. I'll be able to add it too though, that adapter also has a 6gb/s port for regular NAND SATA SSD's. I'm not going ahead even if I have the hardware since I'm so nervous about playing with something new. I know my mobo isn't too old to be able to use nvme ssd's, it is either UEFI or BIOS, but I'll have to abandon BIOS boot....live sessions would automatically be UEFI (and freeze eventually) on a usb 3.0 stick, I didn't press F8 to decide to boot it in BIOS mode...hence my nervousness about UEFI, could be faster but not as stable (or I have no idea what I'm talking about).

---

### Post by awaisahmed123 on 2021-12-30
I am also using sme logs and it's working fine for me.

---

### Post by thatrius on 2022-01-01
I know nothing of how to fix it, but I have what seems to be the exact same problem.

---

### Post by rabid4 on 2022-03-14
Your problem is most likely a suspend/wake problem that is common with computers that use an NVIDIA GPU. Ubuntu will go to sleep, but it will practically never properly wake. You'll notice that other distributions, most particularly openSUSE, is a lot more reliable in that respect as a result of its use of bumblebee. You can try to install it in Ubuntu but it won't work right anyway.

---

