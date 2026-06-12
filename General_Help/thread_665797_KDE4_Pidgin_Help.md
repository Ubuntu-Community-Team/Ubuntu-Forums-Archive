---
title: "KDE4 Pidgin Help"
date: 2008-01-12
forum: General Help
---

### Post by YearZirO on 2008-01-12
ive seen alot of people had this issue and i havent seen a method of making PIDGIN work
when i start pidgin it automatically closes it doesnt minimize and goto the tray it just closes ive tried to goto the command line and run it and i get a number of errors any help would be greatly appreciated 

1.) when i just run the command PIDGIN i get the following

The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 458 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i get the same error if i try to sync it 

2.) if i try to debug i get this 

(16:22:20) prefs: Reading /home/vision/.purple/prefs.xml
(16:22:20) prefs: Finished reading /home/vision/.purple/prefs.xml
(16:22:20) dbus: okkk
(16:22:20) plugins: probing /usr/lib/pidgin/xmppconsole.so
(16:22:20) plugins: probing /usr/lib/pidgin/cap.so
(16:22:20) plugins: probing /usr/lib/pidgin/timestamp.so
(16:22:20) plugins: probing /usr/lib/pidgin/convcolors.so
(16:22:20) plugins: probing /usr/lib/pidgin/extplacement.so
(16:22:20) plugins: probing /usr/lib/pidgin/pidginrc.so
(16:22:20) plugins: probing /usr/lib/pidgin/gestures.so
(16:22:20) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(16:22:20) plugins: probing /usr/lib/pidgin/ticker.so
(16:22:20) plugins: probing /usr/lib/pidgin/spellchk.so
(16:22:20) plugins: probing /usr/lib/pidgin/musicmessaging.so
(16:22:20) plugins: probing /usr/lib/pidgin/gevolution.so
(16:22:20) plugins: /usr/lib/pidgin/gevolution.so is not loadable: libedata-book-1.2.so.2: cannot open shared object file: No such file or directory
(16:22:20) plugins: probing /usr/lib/pidgin/history.so
(16:22:20) plugins: probing /usr/lib/pidgin/timestamp_format.so
(16:22:20) plugins: probing /usr/lib/pidgin/notify.so
(16:22:20) plugins: probing /usr/lib/pidgin/iconaway.so
(16:22:20) plugins: probing /usr/lib/pidgin/markerline.so
(16:22:20) plugins: probing /usr/lib/purple-2/buddynote.so
(16:22:20) plugins: probing /usr/lib/purple-2/statenotify.so
(16:22:20) plugins: probing /usr/lib/purple-2/libmsn.so
(16:22:20) plugins: probing /usr/lib/purple-2/libnovell.so
(16:22:20) plugins: probing /usr/lib/purple-2/offlinemsg.so
(16:22:20) plugins: probing /usr/lib/purple-2/libbonjour.so
(16:22:20) plugins: probing /usr/lib/purple-2/libxmpp.so
(16:22:20) util: Reading file xmpp-caps.xml from directory /home/vision/.purple
(16:22:20) util: File /home/vision/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(16:22:20) plugins: probing /usr/lib/purple-2/libmyspace.so
(16:22:20) plugins: probing /usr/lib/purple-2/ssl.so
(16:22:20) plugins: probing /usr/lib/purple-2/libyahoo.so
(16:22:20) plugins: probing /usr/lib/purple-2/psychic.so
(16:22:20) plugins: probing /usr/lib/purple-2/libaim.so
(16:22:20) plugins: probing /usr/lib/purple-2/ssl-nss.so
(16:22:20) plugins: probing /usr/lib/purple-2/libzephyr.so
(16:22:20) plugins: probing /usr/lib/purple-2/log_reader.so
(16:22:20) plugins: probing /usr/lib/purple-2/libqq.so
(16:22:20) plugins: probing /usr/lib/purple-2/idle.so
(16:22:20) plugins: probing /usr/lib/purple-2/liboscar.so
(16:22:20) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(16:22:20) plugins: probing /usr/lib/purple-2/libjabber.so
(16:22:20) plugins: /usr/lib/purple-2/libjabber.so is not usable because the'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(16:22:20) plugins: probing /usr/lib/purple-2/tcl.so
(16:22:20) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(16:22:20) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(16:22:20) plugins: probing /usr/lib/purple-2/dbus-example.so
(16:22:20) plugins: probing /usr/lib/purple-2/libirc.so
(16:22:20) plugins: probing /usr/lib/purple-2/libsimple.so
(16:22:20) plugins: probing /usr/lib/purple-2/libsametime.so
(16:22:20) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(16:22:20) plugins: probing /usr/lib/purple-2/libgg.so
(16:22:20) plugins: probing /usr/lib/purple-2/newline.so
(16:22:20) plugins: probing /usr/lib/purple-2/autoaccept.so
(16:22:20) plugins: probing /usr/lib/purple-2/libicq.so
(16:22:20) plugins: probing /usr/lib/purple-2/joinpart.so
(16:22:20) plugins: probing /usr/lib/purple-2/perl.so
(16:22:20) prefs: /purple/status/scores/offline changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/available changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/invisible changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/away changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/extended_away changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/idle changed, scheduling save.
(16:22:20) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(16:22:20) util: Reading file accounts.xml from directory /home/vision/.purple
(16:22:20) util: File /home/vision/.purple/accounts.xml does not exist (thisis not necessarily an error)
(16:22:20) util: Reading file status.xml from directory /home/vision/.purple
(16:22:20) certificate: CertificateVerifier x509, singleuse requested but not found.
(16:22:20) certificate: CertificateVerifier singleuse registered
(16:22:20) certificate: CertificatePool x509, ca requested but not found.
(16:22:20) certificate: CertificateScheme x509 requested but not found.
(16:22:20) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(16:22:20) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(16:22:20) certificate: CertificatePool ca registered
(16:22:20) certificate: CertificatePool x509, tls_peers requested but not found.
(16:22:20) certificate: CertificatePool tls_peers registered
(16:22:20) certificate: CertificateVerifier x509, tls_cached requested but not found.
(16:22:20) certificate: CertificateVerifier tls_cached registered
(16:22:20) prefs: /purple/logging/format changed, scheduling save.
(16:22:20) prefs: /purple/logging/format changed, scheduling save.
(16:22:20) prefs: /purple/proxy/type changed, scheduling save.
(16:22:20) prefs: /purple/proxy/host changed, scheduling save.
(16:22:20) prefs: /purple/proxy/port changed, scheduling save.
(16:22:20) prefs: /purple/proxy/username changed, scheduling save.
(16:22:20) prefs: /purple/proxy/password changed, scheduling save.
(16:22:21) certificate: CertificateScheme x509 requested but not found.
(16:22:21) certificate: CertificateScheme x509 registered
(16:22:21) stun: using server
(16:22:21) sound: Initializing sound output drivers.
(16:22:21) prefs: /pidgin/conversations/placement changed, scheduling save.
(16:22:21) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(16:22:21) gtkblist: added visibility manager: 1
(16:22:21) docklet: created
(16:22:21) util: Reading file blist.xml from directory /home/vision/.purple
(16:22:21) util: File /home/vision/.purple/blist.xml does not exist (this isnot necessarily an error)
(16:22:21) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(16:22:21) pounce: Error reading pounces: Failed to open file '/home/vision/.purple/pounces.xml': No such file or directory
(16:22:21) ui_main: Failed to load the default window icon (scalablepx version)!
(16:22:21) Session Management: ICE initialized.
(16:22:21) Session Management: Connecting with no previous ID
(16:22:21) Session Management: Handling new ICE connection... (16:22:21) done.
(16:22:21) Session Management: Connected to manager (KDE) with client ID 105a69524f000120017654100000075120012
(16:22:21) Session Management: Using pidgin as command
(16:22:21) dbus: Need to register an object with the dbus subsystem. (If youare not a developer, please ignore this message.)
(16:22:21) dbus: The signal "gtkblist-unhiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:22:22) Session Management: Received first save_yourself
(16:22:22) Session Management: Received save_complete
(16:22:22) docklet: embedded
The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 458 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by gwbennett on 2008-01-12
I can help any, but I can confirm this. It seems pidgin doesn work with kde4. Oh well. Back to Gnome for me then until I find a fix.

---

### Post by YearZirO on 2008-01-12
i hate GNOME and KOPETE oh well hopefully they will start patching the issues there having for some reason im having windows flash back here am i the only one?

---

### Post by -grubby on 2008-01-12
yes it doesn't work for me either. As far as I can know, there isn't a fix yet. You can always use kopete if you want to use KDE4 that bad

---

### Post by YearZirO on 2008-01-12
im am even though i hate it i can switch back and forth between 3 and 4

but i would like to know if anyone has come across a fix

---

### Post by lunarcloud on 2008-01-13
Go into kde3 set the tray icon to NEVER and then go back into kde4, works fine

---

### Post by triplep on 2008-01-23
Unfortunately GTK doesn't currently support RGBA (the alpha layer specifically). There has been work though to remedy this. It' the alpha layer that causes the problems on minimize to tray.  I can't find the bug report at the moment, but it was on a KDE centric website....

GTK+ with Alpha Support:
[http://arstechnica.com/journals/linux.ars/2007/12/12/gnome-theme-engine-designer-adds-transparency-to-gtk](http://arstechnica.com/journals/linux.ars/2007/12/12/gnome-theme-engine-designer-adds-transparency-to-gtk)

---

