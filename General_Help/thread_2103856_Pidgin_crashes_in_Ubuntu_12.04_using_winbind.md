---
title: "Pidgin crashes in Ubuntu 12.04 using winbind"
date: 2013-01-11
forum: General Help
---

### Post by itninjasteve on 2013-01-11
We are in the process of migrating from Ubuntu 10.10 to 12.04

We use winbind to authenticate active directory users.  Users have roaming profiles on an nfs server.  The NFS roaming profiles are working fine, I can read write and execute without any issues.  Pidgin worked fine in 10.10 

Pidgin crashes while trying to open it.  Also I can log on as root(which is a local user) and pidgin works just fine.

I ran pidgin in debug mode and here is the log.

(14:52:16) prefs: Reading /vhome/test/.purple/prefs.xml
(14:52:16) prefs: Reading /etc/purple/prefs.xml
(14:52:16) prefs: /pidgin/browsers/manual_command changed, scheduling save.
(14:52:16) prefs: removing pref /pidgin/browsers/command
(14:52:16) dbus: okkk
(14:52:16) plugins: probing /usr/lib/pidgin/vvconfig.so
(14:52:16) plugins: probing /usr/lib/pidgin/extplacement.so
(14:52:16) plugins: probing /usr/lib/pidgin/spellchk.so
(14:52:16) plugins: probing /usr/lib/pidgin/history.so
(14:52:16) plugins: probing /usr/lib/pidgin/markerline.so
(14:52:16) plugins: probing /usr/lib/pidgin/musicmessaging.so
(14:52:16) plugins: probing /usr/lib/pidgin/cap.so
(14:52:16) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(14:52:16) plugins: probing /usr/lib/pidgin/pidginrc.so
(14:52:16) plugins: probing /usr/lib/pidgin/gestures.so
(14:52:16) plugins: probing /usr/lib/pidgin/themeedit.so
(14:52:16) plugins: probing /usr/lib/pidgin/timestamp.so
(14:52:16) plugins: probing /usr/lib/pidgin/xmppconsole.so
(14:52:16) plugins: probing /usr/lib/pidgin/convcolors.so
(14:52:16) plugins: probing /usr/lib/pidgin/ticker.so
(14:52:16) plugins: probing /usr/lib/pidgin/sendbutton.so
(14:52:16) plugins: probing /usr/lib/pidgin/notify.so
(14:52:16) plugins: probing /usr/lib/pidgin/timestamp_format.so
(14:52:16) plugins: probing /usr/lib/pidgin/xmppdisco.so
(14:52:16) plugins: probing /usr/lib/pidgin/iconaway.so
(14:52:16) plugins: probing /usr/lib/purple-2/buddynote.so
(14:52:16) plugins: probing /usr/lib/purple-2/libymsg.so
(14:52:16) plugins: /usr/lib/purple-2/libymsg.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:52:16) plugins: probing /usr/lib/purple-2/libmxit.so
(14:52:16) prpl-loubserp-mxit: Loading MXit libPurple plugin...
(14:52:16) plugins: probing /usr/lib/purple-2/libxmpp.so
(14:52:16) plugins: probing /usr/lib/purple-2/libjabber.so
(14:52:16) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:52:16) plugins: probing /usr/lib/purple-2/tcl.so
(14:52:16) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.5.so.0: cannot open shared object file: No such file or directory
(14:52:16) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(14:52:16) plugins: probing /usr/lib/purple-2/psychic.so
(14:52:16) plugins: probing /usr/lib/purple-2/libirc.so
(14:52:16) plugins: probing /usr/lib/purple-2/libmsn.so
(14:52:16) plugins: probing /usr/lib/purple-2/libaim.so
(14:52:16) plugins: probing /usr/lib/purple-2/libnovell.so
(14:52:16) plugins: probing /usr/lib/purple-2/libgg.so
(14:52:16) plugins: probing /usr/lib/purple-2/libsimple.so
(14:52:16) plugins: probing /usr/lib/purple-2/log_reader.so
(14:52:16) plugins: probing /usr/lib/purple-2/libyahoojp.so
(14:52:16) plugins: probing /usr/lib/purple-2/libyahoo.so
(14:52:16) plugins: probing /usr/lib/purple-2/ssl-nss.so
(14:52:16) plugins: probing /usr/lib/purple-2/joinpart.so
(14:52:16) plugins: probing /usr/lib/purple-2/idle.so
(14:52:16) plugins: probing /usr/lib/purple-2/perl.so
(14:52:16) plugins: probing /usr/lib/purple-2/libicq.so
(14:52:16) plugins: probing /usr/lib/purple-2/offlinemsg.so
(14:52:16) plugins: probing /usr/lib/purple-2/libbonjour.so
(14:52:16) plugins: probing /usr/lib/purple-2/libzephyr.so
(14:52:16) plugins: probing /usr/lib/purple-2/ssl.so
(14:52:16) plugins: probing /usr/lib/purple-2/liboscar.so
(14:52:16) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(14:52:16) plugins: probing /usr/lib/purple-2/libmyspace.so
(14:52:16) plugins: probing /usr/lib/purple-2/dbus-example.so
(14:52:16) plugins: probing /usr/lib/purple-2/statenotify.so
(14:52:16) plugins: probing /usr/lib/purple-2/libsametime.so
(14:52:16) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(14:52:16) plugins: probing /usr/lib/purple-2/newline.so
(14:52:16) plugins: probing /usr/lib/purple-2/autoaccept.so
(14:52:16) util: Reading file xmpp-caps.xml from directory /vhome/test/.purple
(14:52:16) util: File /vhome/test/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(14:52:16) jabber: creating hash tables for data objects
(14:52:16) prefs: /purple/status/scores/offline changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/available changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/invisible changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/away changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/extended_away changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/idle changed, scheduling save.
(14:52:16) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(14:52:16) util: Reading file accounts.xml from directory /vhome/test/.purple
(14:52:16) util: File /vhome/test/.purple/accounts.xml does not exist (this is not necessarily an error)
(14:52:16) util: Reading file status.xml from directory /vhome/test/.purple
(14:52:16) util: File /vhome/test/.purple/status.xml does not exist (this is not necessarily an error)
(14:52:16) certificate: CertificateVerifier x509, singleuse requested but not found.
(14:52:16) certificate: CertificateVerifier singleuse registered
(14:52:16) certificate: CertificatePool x509, ca requested but not found.
(14:52:16) certificate: CertificateScheme x509 requested but not found.
(14:52:16) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(14:52:16) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(14:52:16) certificate: CertificatePool ca registered
(14:52:16) certificate: CertificatePool x509, tls_peers requested but not found.
(14:52:16) certificate: CertificatePool tls_peers registered
(14:52:16) certificate: CertificateVerifier x509, tls_cached requested but not found.
(14:52:16) certificate: CertificateVerifier tls_cached registered
(14:52:16) prefs: /purple/logging/format changed, scheduling save.
(14:52:16) prefs: /purple/logging/format changed, scheduling save.
(14:52:16) prefs: /purple/proxy/type changed, scheduling save.
(14:52:16) prefs: /purple/proxy/host changed, scheduling save.
(14:52:16) prefs: /purple/proxy/port changed, scheduling save.
(14:52:16) prefs: /purple/proxy/username changed, scheduling save.
(14:52:16) prefs: /purple/proxy/password changed, scheduling save.
(14:52:16) certificate: CertificateScheme x509 requested but not found.
(14:52:16) certificate: CertificateScheme x509 registered
(14:52:16) util: Reading file smileys.xml from directory /vhome/test/.purple
(14:52:16) util: File /vhome/test/.purple/smileys.xml does not exist (this is not necessarily an error)
(14:52:16) stun: using server 
(14:52:16) sound: Initializing sound output drivers.
(14:52:16) prefs: /pidgin/conversations/placement changed, scheduling save.
(14:52:16) prefs: purple_prefs_get_bool: Unknown pref /pidgin/docklet/x11/embedded
(14:52:16) gtkmedia: Registering media element types
(14:52:21) util: Reading file blist.xml from directory /vhome/test/.purple
(14:52:21) util: File /vhome/test/.purple/blist.xml does not exist (this is not necessarily an error)
(14:52:21) pounce: Error reading pounces: Failed to open file '/vhome/test/.purple/pounces.xml': No such file or directory
(14:52:22) Session Management: ICE initialized.
(14:52:22) Session Management: Connecting with no previous ID
(14:52:22) Session Management: Handling new ICE connection... 
(14:52:22) done.
(14:52:22) Session Management: Connected to manager (gnome-session) with client ID 10d94e615d5e4e64413578475425833900000016510042
(14:52:22) Session Management: Using pidgin as command
(14:52:22) GLib-GObject: value "-578448492" of type `gint' is invalid or out of range for property `weight' of type `gint'



Any ideas why pidgin is crashing?  The only thing that stands out is 
(14:52:22) GLib-GObject: value "-578448492" of type `gint' is invalid or out of range for property `weight' of type `gint'

and I have no idea what that even means.

---

