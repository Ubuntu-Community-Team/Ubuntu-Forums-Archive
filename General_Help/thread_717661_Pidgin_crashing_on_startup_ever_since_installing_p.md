---
title: "Pidgin crashing on startup ever since installing pidgin-libnotify"
date: 2008-03-07
forum: General Help
---

### Post by Berrex on 2008-03-07
[color=red]Edit: Resolved, see post below[/color]

Today I ran $ sudo apt-get install pidgin-libnotify, and ever since, Pidgin has been crashing on startup. I've uninstalled Pidgin & pidgin-libnotify via the synaptic package manager, and then reinstalled both, but that did not resolve the issue. I also did some digging around and found a couple of commands to try, but they didn't help (honestly, I don't even know what they do - I'm a Linux newbie). So where should I begin troubleshooting this issue? Below is what running '$ pidgin -d' brought up.

```
(06:41:52) prefs: Reading /home/david/.purple/prefs.xml
(06:41:52) prefs: Finished reading /home/david/.purple/prefs.xml
(06:41:52) dbus: okkk
(06:41:52) plugins: probing /usr/lib/pidgin/musicmessaging.so
(06:41:52) plugins: probing /usr/lib/pidgin/notify.so
(06:41:52) plugins: probing /usr/lib/pidgin/ticker.so
(06:41:52) plugins: probing /usr/lib/pidgin/convcolors.so
(06:41:52) plugins: probing /usr/lib/pidgin/pidginrc.so
(06:41:52) plugins: probing /usr/lib/pidgin/cap.so
(06:41:52) plugins: probing /usr/lib/pidgin/xmppconsole.so
(06:41:52) plugins: probing /usr/lib/pidgin/spellchk.so
(06:41:52) plugins: probing /usr/lib/pidgin/extplacement.so
(06:41:52) plugins: probing /usr/lib/pidgin/iconaway.so
(06:41:52) plugins: probing /usr/lib/pidgin/history.so
(06:41:52) plugins: probing /usr/lib/pidgin/markerline.so
(06:41:52) plugins: probing /usr/lib/pidgin/gevolution.so
(06:41:52) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(06:41:52) plugins: probing /usr/lib/pidgin/timestamp_format.so
(06:41:52) plugins: probing /usr/lib/pidgin/gestures.so
(06:41:52) plugins: probing /usr/lib/pidgin/nautilus.so
(06:41:52) plugins: probing /usr/lib/pidgin/timestamp.so
(06:41:52) plugins: probing /usr/lib/purple-2/buddynote.so
(06:41:52) plugins: probing /usr/lib/purple-2/libjabber.so
(06:41:52) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(06:41:52) plugins: probing /usr/lib/purple-2/ssl.so
(06:41:52) plugins: probing /usr/lib/purple-2/joinpart.so
(06:41:52) plugins: probing /usr/lib/purple-2/perl.so
(06:41:52) plugins: probing /usr/lib/purple-2/libzephyr.so
(06:41:52) plugins: probing /usr/lib/purple-2/libmsn.so
(06:41:52) plugins: probing /usr/lib/purple-2/liboscar.so
(06:41:52) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(06:41:52) plugins: probing /usr/lib/purple-2/autoaccept.so
(06:41:52) plugins: probing /usr/lib/purple-2/dbus-example.so
(06:41:52) plugins: probing /usr/lib/purple-2/libgg.so
(06:41:52) plugins: probing /usr/lib/purple-2/libaim.so
(06:41:52) plugins: probing /usr/lib/purple-2/ssl-nss.so
(06:41:52) plugins: probing /usr/lib/purple-2/log_reader.so
(06:41:52) plugins: probing /usr/lib/purple-2/libyahoo.so
(06:41:52) plugins: probing /usr/lib/purple-2/libqq.so
(06:41:52) plugins: probing /usr/lib/purple-2/libirc.so
(06:41:52) plugins: probing /usr/lib/purple-2/psychic.so
(06:41:52) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(06:41:52) plugins: probing /usr/lib/purple-2/libicq.so
(06:41:52) plugins: probing /usr/lib/purple-2/libsametime.so
(06:41:52) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(06:41:52) plugins: probing /usr/lib/purple-2/offlinemsg.so
(06:41:52) plugins: probing /usr/lib/purple-2/libsimple.so
(06:41:52) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(06:41:52) plugins: probing /usr/lib/purple-2/libbonjour.so
(06:41:52) plugins: probing /usr/lib/purple-2/idle.so
(06:41:52) plugins: probing /usr/lib/purple-2/newline.so
(06:41:52) plugins: probing /usr/lib/purple-2/libxmpp.so
(06:41:52) util: Reading file xmpp-caps.xml from directory /home/david/.purple
(06:41:52) util: File /home/david/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(06:41:52) plugins: probing /usr/lib/purple-2/libnovell.so
(06:41:52) plugins: probing /usr/lib/purple-2/tcl.so
(06:41:52) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(06:41:52) plugins: probing /usr/lib/purple-2/statenotify.so
(06:41:52) plugins: probing /usr/lib/purple-2/libmyspace.so
(06:41:52) prefs: /purple/status/scores/offline changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/available changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/invisible changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/away changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/extended_away changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/idle changed, scheduling save.
(06:41:52) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(06:41:52) util: Reading file accounts.xml from directory /home/david/.purple
(06:41:52) util: Reading file status.xml from directory /home/david/.purple
(06:41:52) certificate: CertificateVerifier x509, singleuse requested but not found.
(06:41:52) certificate: CertificateVerifier singleuse registered
(06:41:52) certificate: CertificatePool x509, ca requested but not found.
(06:41:52) certificate: CertificateScheme x509 requested but not found.
(06:41:52) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(06:41:52) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(06:41:52) certificate: CertificatePool ca registered
(06:41:52) certificate: CertificatePool x509, tls_peers requested but not found.
(06:41:52) certificate: CertificatePool tls_peers registered
(06:41:52) certificate: CertificateVerifier x509, tls_cached requested but not found.
(06:41:52) certificate: CertificateVerifier tls_cached registered
(06:41:52) prefs: /purple/logging/format changed, scheduling save.
(06:41:52) prefs: /purple/logging/format changed, scheduling save.
(06:41:52) prefs: /purple/proxy/type changed, scheduling save.
(06:41:52) prefs: /purple/proxy/host changed, scheduling save.
(06:41:52) prefs: /purple/proxy/port changed, scheduling save.
(06:41:52) prefs: /purple/proxy/username changed, scheduling save.
(06:41:52) prefs: /purple/proxy/password changed, scheduling save.
(06:41:52) certificate: CertificateScheme x509 requested but not found.
(06:41:52) certificate: CertificateScheme x509 registered
(06:41:52) stun: using server 
(06:41:52) sound: Initializing sound output drivers.
(06:41:52) prefs: /pidgin/conversations/placement changed, scheduling save.
(06:41:52) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(06:41:52) gtkblist: added visibility manager: 1
(06:41:52) docklet: created
(06:41:52) blist: Attempted to save buddy list before it was read!
(06:41:52) certificate: CertificateScheme x509 unregistered
(06:41:52) certificate: CertificateVerifier tls_cached unregistered
(06:41:52) certificate: CertificateVerifier singleuse unregistered
(06:41:52) certificate: CertificatePool tls_peers unregistered
(06:41:52) certificate: CertificatePool ca unregistered
(06:41:52) util: Writing file accounts.xml to directory /home/david/.purple
(06:41:52) util: Writing file /home/david/.purple/accounts.xml
(06:41:52) util: Writing file prefs.xml to directory /home/david/.purple
(06:41:52) util: Writing file /home/david/.purple/prefs.xml
(06:41:52) main: Unloading all plugins
(06:41:52) plugins: Unloading plugin SSL
(06:41:52) plugins: Unloading plugin NSS
(06:41:52) certificate: CertificateScheme x509 unregistered
(06:41:52) plugins: Unloading plugin Perl Plugin Loader
(06:41:52) plugins: Unloading plugin Zephyr
(06:41:52) plugins: Unloading plugin MSN
(06:41:52) plugins: Unloading plugin Gadu-Gadu
(06:41:52) plugins: Unloading plugin AIM
(06:41:52) plugins: Unloading plugin Yahoo
(06:41:52) plugins: Unloading plugin QQ
(06:41:52) plugins: Unloading plugin IRC
(06:41:52) plugins: Unloading plugin ICQ
(06:41:52) plugins: Unloading plugin Sametime
(06:41:52) plugins: Unloading plugin SIMPLE
(06:41:52) plugins: Unloading plugin Bonjour
(06:41:52) plugins: Unloading plugin XMPP
(06:41:52) plugins: Unloading plugin GroupWise
(06:41:52) plugins: Unloading plugin MySpaceIM
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) accels: accel changed, scheduling save.
(06:41:52) gtkblist: removed visibility manager: 0
(06:41:52) docklet: destroyed
(06:41:52) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
```

I also ran '$ strace pidgin' but I didn't know what to make of the output. I'll post it if needed. I didn't post it because it's pretty long.

Your help is appreciated. I'm using Ubuntu 7.10 on an Intel Core Duo MacBook.

---

### Post by Berrex on 2008-03-07
Oh, jeez. I feel really stupid now. Pidgin wasn't actually crashing at all. I just had attempted to quit Pidgen before installing pidgin-libnotify by clicking the 'X' on the buddy list, but all that does is it minimizes it to the tray. So whenever  I went to relaunch Pidgin, it would start minimized to the tray, and I thought it was simply crashing. D'oh!

Well, disregard my post then. Sorry.

---

### Post by ccady on 2008-04-25
Well, you may claim you are an idiot, but be comforted that you are not alone.  I, too, am an idiot.  I had exactly the same problem, and your post cleared it up for me.  (I had been screwing around with the location of my system tray, and missed that Pidgin was already running.)

(It would be nice if Pidgin put "Hey Lunkhead!  Pidgin is already running!" in the debug output.)

Thank you for coming back to the post and explaining what happened.  You saved me quite a bit of time.

---

