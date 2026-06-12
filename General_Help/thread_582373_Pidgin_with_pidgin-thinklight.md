---
title: "Pidgin with pidgin-thinklight"
date: 2007-10-19
forum: General Help
---

### Post by warpedreality on 2007-10-19
So I was having trouble with Pidgin (2.0.2) after upgrade to Gibson and getting those 'SSL/TSL support required' errors and I did a ./configure and a sudo make install again with the latest Pidgin 2.2.1 src files. Pidgin was workign fine after this. 

Then I tried installing the pidgin-thinklight plugin, couldn't find it as a separate installable plugin so just downloaded the src files, ran ./configure and copied over 3 files (*.c, *.la, *.so) from pidgin-thinklight folder into the pidgin_install_home plugin directory (since that is what I saw for the other plugins in the Tools > Plugins) and ever since my Pidgin's messed up. I get the following error when I do a pidgin -d :(.. someone help..

I completely uninstalled pidgin (ran ./configure and sudo make uninstall, deleted all folders of both pidgin and pidgin-thinklight), downloaded the latest 2.2.1 src again and compiled and installed but that didn't work either.. help? :(

```
shahfazal@fazalt60p:~/dwnlds/pidgin-2.2.1$ pidgin -d
(18:10:33) prefs: Reading /home/shahfazal/.purple/prefs.xml
(18:10:33) prefs: Finished reading /home/shahfazal/.purple/prefs.xml
(18:10:33) plugins: probing /usr/local/lib/pidgin/notify.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/history.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/extplacement.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/convcolors.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/timestamp.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/gtkbuddynote.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/spellchk.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/xmppconsole.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/gestures.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/markerline.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/relnot.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/pidginrc.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/iconaway.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/timestamp_format.so
(18:10:33) plugins: probing /usr/local/lib/pidgin/ticker.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/ssl-nss.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libnovell.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/pidgin-blinklight.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/log_reader.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libsimple.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/statenotify.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libxmpp.so
(18:10:33) util: Reading file xmpp-caps.xml from directory /home/shahfazal/.purple
(18:10:33) plugins: probing /usr/local/lib/purple-2/ssl.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/psychic.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/joinpart.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libmyspace.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/idle.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libyahoo.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/autoaccept.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libqq.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/liboscar.so
(18:10:33) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:10:33) plugins: probing /usr/local/lib/purple-2/ssl-gnutls.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/offlinemsg.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libgg.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libaim.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libzephyr.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libicq.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libjabber.so
(18:10:33) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(18:10:33) plugins: probing /usr/local/lib/purple-2/newline.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libirc.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/buddynote.so
(18:10:33) plugins: probing /usr/local/lib/purple-2/libmsn.so
(18:10:33) prefs: /purple/status/scores/offline changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/available changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/invisible changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/away changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/extended_away changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/idle changed, scheduling save.
(18:10:33) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(18:10:33) util: Reading file accounts.xml from directory /home/shahfazal/.purple
(18:10:33) util: Reading file status.xml from directory /home/shahfazal/.purple
(18:10:33) certificate: CertificateVerifier x509, singleuse requested but not found.
(18:10:33) certificate: CertificateVerifier singleuse registered
(18:10:33) certificate: CertificatePool x509, ca requested but not found.
(18:10:33) certificate: CertificateScheme x509 requested but not found.
(18:10:33) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(18:10:33) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(18:10:33) certificate: CertificatePool ca registered
(18:10:33) certificate: CertificatePool x509, tls_peers requested but not found.
(18:10:33) certificate: CertificatePool tls_peers registered
(18:10:33) certificate: CertificateVerifier x509, tls_cached requested but not found.
(18:10:33) certificate: CertificateVerifier tls_cached registered
(18:10:33) prefs: /purple/logging/format changed, scheduling save.
(18:10:33) prefs: /purple/logging/format changed, scheduling save.
(18:10:33) prefs: /purple/proxy/type changed, scheduling save.
(18:10:33) prefs: /purple/proxy/host changed, scheduling save.
(18:10:33) prefs: /purple/proxy/port changed, scheduling save.
(18:10:33) prefs: /purple/proxy/username changed, scheduling save.
(18:10:33) prefs: /purple/proxy/password changed, scheduling save.
(18:10:33) certificate: CertificateScheme x509 requested but not found.
(18:10:33) certificate: CertificateScheme x509 registered
(18:10:33) stun: using server 
(18:10:33) prefs: /pidgin/conversations/placement changed, scheduling save.
(18:10:33) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(18:10:33) gtkblist: added visibility manager: 1
(18:10:33) docklet: created
(18:10:33) util: Reading file blist.xml from directory /home/shahfazal/.purple
(18:10:33) plugins: Loading saved plugin /usr/local/lib/purple-2/ssl-gnutls.so
(18:10:33) plugins: Loading saved plugin /usr/local/lib/pidgin/history.so
(18:10:33) plugins: Loading saved plugin /usr/local/lib/pidgin/iconaway.so
(18:10:33) plugins: Loading saved plugin /usr/local/lib/purple-2/psychic.so
(18:10:33) plugins: Loading saved plugin /usr/local/lib/purple-2/pidgin-blinklight.so
(18:10:33) pidgin-blinklight: chose file /proc/acpi/ibm/light.
(18:10:33) plugins: Loading saved plugin /usr/local/lib/purple-2/ssl.so
(18:10:33) pidgin-blinklight: chose file /proc/acpi/ibm/light.
(18:10:33) plugins: Loading saved plugin /usr/local/lib/purple-2/ssl.so
(18:10:33) Session Management: ICE initialized.
(18:10:33) Session Management: Connecting with no previous ID
(18:10:33) Session Management: ICE initialized.
(18:10:33) Session Management: Connecting with no previous ID
(18:10:33) Session Management: Handling new ICE connection... (18:10:33) done.
(18:10:33) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000119284263300000054720077
(18:10:33) Session Management: Using pidgin as command
(18:10:33) Session Management: Handling new ICE connection... (18:10:33) done.
(18:10:33) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000119284263300000054720078
(18:10:33) Session Management: Using pidgin as command
The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 318 error_code 14 request_code 45 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'.
  (Details: serial 325 error_code 14 request_code 153 minor_code 27)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by warpedreality on 2007-10-19
The reason I like Pidgin is it has mIRC support too.. please help :(

complete cleanup/uninstall/install didn't work either... :confused:

---

