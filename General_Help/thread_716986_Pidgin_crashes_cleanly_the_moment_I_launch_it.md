---
title: "Pidgin crashes cleanly the moment I launch it"
date: 2008-03-06
forum: General Help
---

### Post by ubtutu on 2008-03-06
Out of the blue my pidgin has started shutting down a moment after it starts up, with no graphical error message. It's version 2.2.1 installed from the gutsy repo. The debug output from `pidgin -d` is below, can anyone help me, I am so lonely without my online buddies :)

I already tried reinstalling using apt-get remove and apt-get install, but the same problem remains.

```

mike@ubuntu:~$ pidgin -d
(19:39:57) prefs: Reading /home/mike/.purple/prefs.xml
(19:39:57) prefs: Finished reading /home/mike/.purple/prefs.xml
(19:39:57) dbus: okkk
(19:39:57) plugins: probing /usr/lib/pidgin/cap.so
(19:39:57) plugins: probing /usr/lib/pidgin/gestures.so
(19:39:57) plugins: probing /usr/lib/pidgin/timestamp.so
(19:39:57) plugins: probing /usr/lib/pidgin/extplacement.so
(19:39:57) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(19:39:57) plugins: probing /usr/lib/pidgin/xmppconsole.so
(19:39:57) plugins: probing /usr/lib/pidgin/musicmessaging.so
(19:39:57) plugins: probing /usr/lib/pidgin/nautilus.so
(19:39:57) plugins: probing /usr/lib/pidgin/history.so
(19:39:57) plugins: probing /usr/lib/pidgin/convcolors.so
(19:39:57) plugins: probing /usr/lib/pidgin/markerline.so
(19:39:57) plugins: probing /usr/lib/pidgin/iconaway.so
(19:39:57) plugins: probing /usr/lib/pidgin/timestamp_format.so
(19:39:57) plugins: probing /usr/lib/pidgin/notify.so
(19:39:57) plugins: probing /usr/lib/pidgin/ticker.so
(19:39:57) plugins: probing /usr/lib/pidgin/gevolution.so
(19:39:57) plugins: probing /usr/lib/pidgin/pidginrc.so
(19:39:57) plugins: probing /usr/lib/pidgin/spellchk.so
(19:39:57) plugins: probing /usr/lib/purple-2/libmyspace.so
(19:39:57) plugins: probing /usr/lib/purple-2/autoaccept.so
(19:39:57) plugins: probing /usr/lib/purple-2/newline.so
(19:39:57) plugins: probing /usr/lib/purple-2/libicq.so
(19:39:57) plugins: probing /usr/lib/purple-2/libaim.so
(19:39:57) plugins: probing /usr/lib/purple-2/libyahoo.so
(19:39:57) plugins: probing /usr/lib/purple-2/libbonjour.so
(19:39:57) plugins: probing /usr/lib/purple-2/libgg.so
(19:39:57) plugins: probing /usr/lib/purple-2/libsametime.so
(19:39:57) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(19:39:57) plugins: probing /usr/lib/purple-2/ssl-nss.so
(19:39:57) plugins: probing /usr/lib/purple-2/libxmpp.so
(19:39:57) util: Reading file xmpp-caps.xml from directory /home/mike/.purple
(19:39:57) util: File /home/mike/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(19:39:57) plugins: probing /usr/lib/purple-2/statenotify.so
(19:39:57) plugins: probing /usr/lib/purple-2/buddynote.so
(19:39:57) plugins: probing /usr/lib/purple-2/libjabber.so
(19:39:57) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:39:57) plugins: probing /usr/lib/purple-2/dbus-example.so
(19:39:57) plugins: probing /usr/lib/purple-2/log_reader.so
(19:39:57) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(19:39:57) plugins: probing /usr/lib/purple-2/libirc.so
(19:39:57) plugins: probing /usr/lib/purple-2/perl.so
(19:39:57) plugins: probing /usr/lib/purple-2/libsimple.so
(19:39:57) plugins: probing /usr/lib/purple-2/libqq.so
(19:39:57) plugins: probing /usr/lib/purple-2/libnovell.so
(19:39:57) plugins: probing /usr/lib/purple-2/psychic.so
(19:39:57) plugins: probing /usr/lib/purple-2/joinpart.so
(19:39:57) plugins: probing /usr/lib/purple-2/liboscar.so
(19:39:57) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:39:57) plugins: probing /usr/lib/purple-2/tcl.so
(19:39:57) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(19:39:57) plugins: probing /usr/lib/purple-2/libzephyr.so
(19:39:57) plugins: probing /usr/lib/purple-2/idle.so
(19:39:57) plugins: probing /usr/lib/purple-2/libmsn.so
(19:39:57) plugins: probing /usr/lib/purple-2/ssl.so
(19:39:57) plugins: probing /usr/lib/purple-2/offlinemsg.so
(19:39:57) prefs: /purple/status/scores/offline changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/available changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/invisible changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/away changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/extended_away changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/idle changed, scheduling save.
(19:39:57) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(19:39:57) util: Reading file accounts.xml from directory /home/mike/.purple
(19:39:57) util: Reading file status.xml from directory /home/mike/.purple
(19:39:57) certificate: CertificateVerifier x509, singleuse requested but not found.
(19:39:57) certificate: CertificateVerifier singleuse registered
(19:39:57) certificate: CertificatePool x509, ca requested but not found.
(19:39:57) certificate: CertificateScheme x509 requested but not found.
(19:39:57) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(19:39:57) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(19:39:57) certificate: CertificatePool ca registered
(19:39:57) certificate: CertificatePool x509, tls_peers requested but not found.
(19:39:57) certificate: CertificatePool tls_peers registered
(19:39:57) certificate: CertificateVerifier x509, tls_cached requested but not found.
(19:39:57) certificate: CertificateVerifier tls_cached registered
(19:39:57) prefs: /purple/logging/format changed, scheduling save.
(19:39:57) prefs: /purple/logging/format changed, scheduling save.
(19:39:57) prefs: /purple/proxy/type changed, scheduling save.
(19:39:57) prefs: /purple/proxy/host changed, scheduling save.
(19:39:57) prefs: /purple/proxy/port changed, scheduling save.
(19:39:57) prefs: /purple/proxy/username changed, scheduling save.
(19:39:57) prefs: /purple/proxy/password changed, scheduling save.
(19:39:57) certificate: CertificateScheme x509 requested but not found.
(19:39:57) certificate: CertificateScheme x509 registered
(19:39:57) stun: using server 
(19:39:57) sound: Initializing sound output drivers.
(19:39:57) prefs: /pidgin/conversations/placement changed, scheduling save.
(19:39:57) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(19:39:57) gtkblist: added visibility manager: 1
(19:39:57) docklet: created
(19:39:57) blist: Attempted to save buddy list before it was read!
(19:39:57) certificate: CertificateScheme x509 unregistered
(19:39:57) certificate: CertificateVerifier tls_cached unregistered
(19:39:57) certificate: CertificateVerifier singleuse unregistered
(19:39:57) certificate: CertificatePool tls_peers unregistered
(19:39:57) certificate: CertificatePool ca unregistered
(19:39:57) util: Writing file accounts.xml to directory /home/mike/.purple
(19:39:57) util: Writing file /home/mike/.purple/accounts.xml
(19:39:57) util: Writing file status.xml to directory /home/mike/.purple
(19:39:57) util: Writing file /home/mike/.purple/status.xml
(19:39:57) util: Writing file prefs.xml to directory /home/mike/.purple
(19:39:57) util: Writing file /home/mike/.purple/prefs.xml
(19:39:57) main: Unloading all plugins
(19:39:57) plugins: Unloading plugin MySpaceIM
(19:39:57) plugins: Unloading plugin ICQ
(19:39:57) plugins: Unloading plugin AIM
(19:39:57) plugins: Unloading plugin Yahoo
(19:39:57) plugins: Unloading plugin Bonjour
(19:39:57) plugins: Unloading plugin Gadu-Gadu
(19:39:57) plugins: Unloading plugin Sametime
(19:39:57) plugins: Unloading plugin NSS
(19:39:57) certificate: CertificateScheme x509 unregistered
(19:39:57) plugins: Unloading plugin XMPP
(19:39:57) plugins: Unloading plugin IRC
(19:39:57) plugins: Unloading plugin Perl Plugin Loader
(19:39:57) plugins: Unloading plugin SIMPLE
(19:39:57) plugins: Unloading plugin QQ
(19:39:57) plugins: Unloading plugin GroupWise
(19:39:57) plugins: Unloading plugin Zephyr
(19:39:57) plugins: Unloading plugin MSN
(19:39:57) plugins: Unloading plugin SSL
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) accels: accel changed, scheduling save.
(19:39:57) gtkblist: removed visibility manager: 0
(19:39:57) docklet: destroyed
(19:39:57) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

```

---

### Post by Oldsoldier2003 on 2008-03-06
> **ubtutu said:**
> Out of the blue my pidgin has started shutting down a moment after it starts up, with no graphical error message. It's version 2.2.1 installed from the gutsy repo. The debug output from `pidgin -d` is below, can anyone help me, I am so lonely without my online buddies :)

I already tried reinstalling using apt-get remove and apt-get install, but the same problem remains.

try this way:

```
sudo aptitude purge pidgin pidgin-data libpurple0
sudo apt-get install pidgin pidgin-data libpurple0
 
```

or alternatively you could [compile a newer version of pidgin]("http://ubuntuforums.org/showthread.php?t=613049") or get the packages from [GetDeb]("http://www.getdeb.net/")

---

### Post by ubtutu on 2008-03-06
Thanks for the suggestions Oldsoldier2003, I tried purging the three packages and reinstalling using apt-get, same problem. So I purged again and installed the more recent three pidgin packages from getdeb.net (version 2.4.0) same problem (anyone else trying this, please back up your ~/.purple directory first if you want to preserve your chat logs).

As for compiling, I really wanted to avoid all that until I got more used to linux. Surely there is some way to diagnose the problem based on the debug output?

---

### Post by ubtutu on 2008-03-06
I found the problem, I already had a copy of pidgin running from a previous gnome session, but I had not remembered about it, nor was any pidgin icon appearing in the notification area/taskbar area.

I ended the old pidgin process, and started a new one. Silly me!!

---

