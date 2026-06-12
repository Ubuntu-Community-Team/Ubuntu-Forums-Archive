---
title: "pidgin crashes on load"
date: 2007-12-12
forum: General Help
---

### Post by .Michael on 2007-12-12
When I load pidgin, it crashes even before the buddylist comes up. I first discovered this when I tried loading it through the gui. Then I loaded a terminal and used the debug switch.

```
michael@ubuntu:~$ pidgin -d
(14:33:36) prefs: Reading /home/michael/.purple/prefs.xml
(14:33:36) prefs: Finished reading /home/michael/.purple/prefs.xml
(14:33:36) dbus: okkk
(14:33:36) plugins: probing /usr/lib/pidgin/gevolution.so
(14:33:36) plugins: probing /usr/lib/pidgin/spellchk.so
(14:33:36) plugins: probing /usr/lib/pidgin/iconaway.so
(14:33:36) plugins: probing /usr/lib/pidgin/markerline.so
(14:33:36) plugins: probing /usr/lib/pidgin/pidginrc.so
(14:33:36) plugins: probing /usr/lib/pidgin/notify.so
(14:33:36) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(14:33:36) plugins: probing /usr/lib/pidgin/nautilus.so
(14:33:36) plugins: probing /usr/lib/pidgin/extplacement.so
(14:33:36) plugins: probing /usr/lib/pidgin/cap.so
(14:33:36) plugins: probing /usr/lib/pidgin/timestamp_format.so
(14:33:36) plugins: probing /usr/lib/pidgin/musictracker.so
(14:33:36) plugins: probing /usr/lib/pidgin/musicmessaging.so
(14:33:36) plugins: probing /usr/lib/pidgin/xmppconsole.so
(14:33:36) plugins: probing /usr/lib/pidgin/ticker.so
(14:33:36) plugins: probing /usr/lib/pidgin/gestures.so
(14:33:36) plugins: probing /usr/lib/pidgin/history.so
(14:33:36) plugins: probing /usr/lib/pidgin/currenttrack.so
(14:33:36) plugins: /usr/lib/pidgin/currenttrack.so is not loadable: libxmms.so.1: cannot open shared object file: No such file or directory
(14:33:36) plugins: probing /usr/lib/pidgin/timestamp.so
(14:33:36) plugins: probing /usr/lib/pidgin/convcolors.so
(14:33:36) plugins: probing /usr/lib/purple-2/joinpart.so
(14:33:36) plugins: probing /usr/lib/purple-2/statenotify.so
(14:33:36) plugins: probing /usr/lib/purple-2/libxmpp.so
(14:33:36) util: Reading file xmpp-caps.xml from directory /home/michael/.purple
(14:33:36) plugins: probing /usr/lib/purple-2/log_reader.so
(14:33:36) plugins: probing /usr/lib/purple-2/libqq.so
(14:33:36) plugins: probing /usr/lib/purple-2/idle.so
(14:33:36) plugins: probing /usr/lib/purple-2/libicq.so
(14:33:36) plugins: probing /usr/lib/purple-2/libirc.so
(14:33:36) plugins: probing /usr/lib/purple-2/liboscar.so
(14:33:36) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:33:36) plugins: probing /usr/lib/purple-2/libyahoo.so
(14:33:36) plugins: probing /usr/lib/purple-2/buddynote.so
(14:33:36) plugins: probing /usr/lib/purple-2/newline.so
(14:33:36) plugins: probing /usr/lib/purple-2/libbonjour.so
(14:33:36) plugins: probing /usr/lib/purple-2/libzephyr.so
(14:33:36) plugins: probing /usr/lib/purple-2/perl.so
(14:33:36) plugins: probing /usr/lib/purple-2/libsimple.so
(14:33:36) plugins: probing /usr/lib/purple-2/tcl.so
(14:33:36) plugins: probing /usr/lib/purple-2/libmyspace.so
(14:33:36) plugins: probing /usr/lib/purple-2/ssl.so
(14:33:36) plugins: probing /usr/lib/purple-2/ssl-nss.so
(14:33:36) plugins: probing /usr/lib/purple-2/libaim.so
(14:33:36) plugins: probing /usr/lib/purple-2/libjabber.so
(14:33:36) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:33:36) plugins: probing /usr/lib/purple-2/libmsn.so
(14:33:36) plugins: probing /usr/lib/purple-2/autoaccept.so
(14:33:36) plugins: probing /usr/lib/purple-2/libsametime.so
(14:33:36) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(14:33:36) plugins: probing /usr/lib/purple-2/libnovell.so
(14:33:36) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(14:33:36) plugins: probing /usr/lib/purple-2/libgg.so
(14:33:36) plugins: probing /usr/lib/purple-2/offlinemsg.so
(14:33:36) plugins: probing /usr/lib/purple-2/dbus-example.so
(14:33:36) plugins: probing /usr/lib/purple-2/psychic.so
(14:33:36) prefs: /purple/status/scores/offline changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/available changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/invisible changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/away changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/extended_away changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/idle changed, scheduling save.
(14:33:36) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(14:33:36) util: Reading file accounts.xml from directory /home/michael/.purple
(14:33:36) myspace: returning status types
(14:33:36) util: Reading file status.xml from directory /home/michael/.purple
(14:33:36) certificate: CertificateVerifier x509, singleuse requested but not found.
(14:33:36) certificate: CertificateVerifier singleuse registered
(14:33:36) certificate: CertificatePool x509, ca requested but not found.
(14:33:36) certificate: CertificateScheme x509 requested but not found.
(14:33:36) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(14:33:36) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(14:33:36) certificate: CertificatePool ca registered
(14:33:36) certificate: CertificatePool x509, tls_peers requested but not found.
(14:33:36) certificate: CertificatePool tls_peers registered
(14:33:36) certificate: CertificateVerifier x509, tls_cached requested but not found.
(14:33:36) certificate: CertificateVerifier tls_cached registered
(14:33:36) prefs: /purple/logging/format changed, scheduling save.
(14:33:36) prefs: /purple/logging/format changed, scheduling save.
(14:33:36) prefs: /purple/proxy/type changed, scheduling save.
(14:33:36) prefs: /purple/proxy/host changed, scheduling save.
(14:33:36) prefs: /purple/proxy/port changed, scheduling save.
(14:33:36) prefs: /purple/proxy/username changed, scheduling save.
(14:33:36) prefs: /purple/proxy/password changed, scheduling save.
(14:33:36) certificate: CertificateScheme x509 requested but not found.
(14:33:36) certificate: CertificateScheme x509 registered
(14:33:36) stun: using server 
(14:33:36) sound: Initializing sound output drivers.
(14:33:36) prefs: /pidgin/conversations/placement changed, scheduling save.
(14:33:36) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(14:33:36) gtkblist: added visibility manager: 1
(14:33:36) docklet: created
(14:33:36) blist: Attempted to save buddy list before it was read!
(14:33:36) certificate: CertificateScheme x509 unregistered
(14:33:36) certificate: CertificateVerifier tls_cached unregistered
(14:33:36) certificate: CertificateVerifier singleuse unregistered
(14:33:36) certificate: CertificatePool tls_peers unregistered
(14:33:36) certificate: CertificatePool ca unregistered
(14:33:36) util: Writing file accounts.xml to directory /home/michael/.purple
(14:33:36) util: Writing file /home/michael/.purple/accounts.xml
(14:33:36) util: Writing file status.xml to directory /home/michael/.purple
(14:33:36) util: Writing file /home/michael/.purple/status.xml
(14:33:36) util: Writing file prefs.xml to directory /home/michael/.purple
(14:33:36) util: Writing file /home/michael/.purple/prefs.xml
(14:33:36) main: Unloading all plugins
(14:33:36) plugins: Unloading plugin XMPP
(14:33:36) plugins: Unloading plugin QQ
(14:33:36) plugins: Unloading plugin ICQ
(14:33:36) plugins: Unloading plugin IRC
(14:33:36) plugins: Unloading plugin Yahoo
(14:33:36) plugins: Unloading plugin Bonjour
(14:33:36) plugins: Unloading plugin Zephyr
(14:33:36) plugins: Unloading plugin Perl Plugin Loader
(14:33:36) plugins: Unloading plugin SIMPLE
(14:33:36) plugins: Unloading plugin Tcl Plugin Loader
(14:33:36) plugins: Unloading plugin MySpaceIM
(14:33:36) plugins: Unloading plugin SSL
(14:33:36) plugins: Unloading plugin NSS
(14:33:36) certificate: CertificateScheme x509 unregistered
(14:33:36) plugins: Unloading plugin AIM
(14:33:36) plugins: Unloading plugin MSN
(14:33:36) plugins: Unloading plugin Sametime
(14:33:36) plugins: Unloading plugin GroupWise
(14:33:36) plugins: Unloading plugin Gadu-Gadu
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) accels: accel changed, scheduling save.
(14:33:36) gtkblist: removed visibility manager: 0
(14:33:36) docklet: destroyed
(14:33:36) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
michael@ubuntu:~$ 
```

I tried reinstalling it with no sucess.

---

### Post by .Michael on 2007-12-12
Well i just removed all the xml files from /home/.gaim

and it works fine

---

### Post by killertomato94 on 2007-12-12
I'm having the same exact problem. I know you said how to fix it, but I'm really retarded at computers and I have NO idea how to delete the xml files and where they are at. Could you put more specific instructions up please?

---

