---
title: "gaim stopped working"
date: 2008-04-10
forum: General Help
---

### Post by stevecoh1 on 2008-04-10
Gaim was working fine on Ubuntu 7.10 and then it stopped working for no reason that I can understand.  Nothing was installed or changed on the system.   Running from console in debug mode, we see the following.  There are errors but what can I do about them:

$ gaim -d
(08:42:40) prefs: Reading /home/scohen/.purple/prefs.xml
(08:42:40) prefs: Finished reading /home/scohen/.purple/prefs.xml
(08:42:40) dbus: okkk
(08:42:40) plugins: probing /usr/lib/pidgin/gestures.so
(08:42:40) plugins: probing /usr/lib/pidgin/spellchk.so
(08:42:40) plugins: probing /usr/lib/pidgin/musicmessaging.so
(08:42:40) plugins: probing /usr/lib/pidgin/timestamp.so
(08:42:40) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(08:42:40) plugins: probing /usr/lib/pidgin/extplacement.so
(08:42:40) plugins: probing /usr/lib/pidgin/nautilus.so
(08:42:40) plugins: probing /usr/lib/pidgin/iconaway.so
(08:42:40) plugins: probing /usr/lib/pidgin/cap.so
(08:42:40) plugins: probing /usr/lib/pidgin/pidginrc.so
(08:42:40) plugins: probing /usr/lib/pidgin/xmppconsole.so
(08:42:40) plugins: probing /usr/lib/pidgin/markerline.so
(08:42:40) plugins: probing /usr/lib/pidgin/convcolors.so
(08:42:40) plugins: probing /usr/lib/pidgin/ticker.so
(08:42:40) plugins: probing /usr/lib/pidgin/timestamp_format.so
(08:42:40) plugins: probing /usr/lib/pidgin/gevolution.so
(08:42:40) plugins: probing /usr/lib/pidgin/history.so
(08:42:40) plugins: probing /usr/lib/pidgin/notify.so
(08:42:40) plugins: probing /usr/lib/purple-2/libirc.so
(08:42:40) plugins: probing /usr/lib/purple-2/liboscar.so
(08:42:40) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(08:42:40) plugins: probing /usr/lib/purple-2/ssl-nss.so
(08:42:40) plugins: probing /usr/lib/purple-2/autoaccept.so
(08:42:40) plugins: probing /usr/lib/purple-2/offlinemsg.so
(08:42:40) plugins: probing /usr/lib/purple-2/newline.so
(08:42:40) plugins: probing /usr/lib/purple-2/perl.so
(08:42:40) plugins: probing /usr/lib/purple-2/libgg.so
(08:42:40) plugins: probing /usr/lib/purple-2/idle.so
(08:42:40) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(08:42:40) plugins: probing /usr/lib/purple-2/log_reader.so
(08:42:40) plugins: probing /usr/lib/purple-2/libmsn.so
(08:42:40) plugins: probing /usr/lib/purple-2/libqq.so
(08:42:40) plugins: probing /usr/lib/purple-2/libnovell.so
(08:42:40) plugins: probing /usr/lib/purple-2/libsametime.so
(08:42:40) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(08:42:40) plugins: probing /usr/lib/purple-2/libmyspace.so
(08:42:40) plugins: probing /usr/lib/purple-2/psychic.so
(08:42:40) plugins: probing /usr/lib/purple-2/ssl.so
(08:42:40) plugins: probing /usr/lib/purple-2/dbus-example.so
(08:42:40) plugins: probing /usr/lib/purple-2/libyahoo.so
(08:42:40) plugins: probing /usr/lib/purple-2/libicq.so
(08:42:40) plugins: probing /usr/lib/purple-2/statenotify.so
(08:42:40) plugins: probing /usr/lib/purple-2/buddynote.so
(08:42:40) plugins: probing /usr/lib/purple-2/libzephyr.so
(08:42:40) plugins: probing /usr/lib/purple-2/libaim.so
(08:42:40) plugins: probing /usr/lib/purple-2/joinpart.so
(08:42:40) plugins: probing /usr/lib/purple-2/libsimple.so
(08:42:40) plugins: probing /usr/lib/purple-2/libjabber.so
(08:42:40) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(08:42:40) plugins: probing /usr/lib/purple-2/tcl.so
(08:42:40) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(08:42:40) plugins: probing /usr/lib/purple-2/libbonjour.so
(08:42:40) plugins: probing /usr/lib/purple-2/libxmpp.so
(08:42:40) util: Reading file xmpp-caps.xml from directory /home/scohen/.purple
(08:42:40) util: File /home/scohen/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(08:42:40) prefs: /purple/status/scores/offline changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/available changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/invisible changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/away changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/extended_away changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/idle changed, scheduling save.
(08:42:40) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(08:42:40) util: Reading file accounts.xml from directory /home/scohen/.purple
(08:42:40) util: Reading file status.xml from directory /home/scohen/.purple
(08:42:40) certificate: CertificateVerifier x509, singleuse requested but not found.
(08:42:40) certificate: CertificateVerifier singleuse registered
(08:42:40) certificate: CertificatePool x509, ca requested but not found.
(08:42:40) certificate: CertificateScheme x509 requested but not found.
(08:42:40) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(08:42:40) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(08:42:40) certificate: CertificatePool ca registered
(08:42:40) certificate: CertificatePool x509, tls_peers requested but not found.
(08:42:40) certificate: CertificatePool tls_peers registered
(08:42:40) certificate: CertificateVerifier x509, tls_cached requested but not found.
(08:42:40) certificate: CertificateVerifier tls_cached registered
(08:42:40) prefs: /purple/logging/format changed, scheduling save.
(08:42:40) prefs: /purple/logging/format changed, scheduling save.
(08:42:40) prefs: /purple/proxy/type changed, scheduling save.
(08:42:40) prefs: /purple/proxy/host changed, scheduling save.
(08:42:40) prefs: /purple/proxy/port changed, scheduling save.
(08:42:40) prefs: /purple/proxy/username changed, scheduling save.
(08:42:40) prefs: /purple/proxy/password changed, scheduling save.
(08:42:40) certificate: CertificateScheme x509 requested but not found.
(08:42:40) certificate: CertificateScheme x509 registered
(08:42:40) stun: using server 
(08:42:40) sound: Initializing sound output drivers.
(08:42:40) prefs: /pidgin/conversations/placement changed, scheduling save.
(08:42:40) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(08:42:40) gtkblist: added visibility manager: 1
(08:42:40) docklet: created
(08:42:40) blist: Attempted to save buddy list before it was read!
(08:42:40) certificate: CertificateScheme x509 unregistered
(08:42:40) certificate: CertificateVerifier tls_cached unregistered
(08:42:40) certificate: CertificateVerifier singleuse unregistered
(08:42:40) certificate: CertificatePool tls_peers unregistered
(08:42:40) certificate: CertificatePool ca unregistered
(08:42:40) util: Writing file accounts.xml to directory /home/scohen/.purple
(08:42:40) util: Writing file /home/scohen/.purple/accounts.xml
(08:42:40) util: Writing file prefs.xml to directory /home/scohen/.purple
(08:42:40) util: Writing file /home/scohen/.purple/prefs.xml
(08:42:40) main: Unloading all plugins
(08:42:40) plugins: Unloading plugin IRC
(08:42:40) plugins: Unloading plugin NSS
(08:42:40) certificate: CertificateScheme x509 unregistered
(08:42:40) plugins: Unloading plugin Perl Plugin Loader
(08:42:40) plugins: Unloading plugin Gadu-Gadu
(08:42:40) plugins: Unloading plugin MSN
(08:42:40) plugins: Unloading plugin QQ
(08:42:40) plugins: Unloading plugin GroupWise
(08:42:40) plugins: Unloading plugin Sametime
(08:42:40) plugins: Unloading plugin MySpaceIM
(08:42:40) plugins: Unloading plugin SSL
(08:42:40) plugins: Unloading plugin Yahoo
(08:42:40) plugins: Unloading plugin ICQ
(08:42:40) plugins: Unloading plugin Zephyr
(08:42:40) plugins: Unloading plugin AIM
(08:42:40) plugins: Unloading plugin SIMPLE
(08:42:40) plugins: Unloading plugin Bonjour
(08:42:40) plugins: Unloading plugin XMPP
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) accels: accel changed, scheduling save.
(08:42:40) gtkblist: removed visibility manager: 0
(08:42:40) docklet: destroyed
(08:42:40) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
$

---

### Post by sefs on 2008-04-10
Are you able to install pidgin from the repos and see if it works?  

I say this because Pidgin is the updated (new) version of gaim.

---

### Post by -Zeus- on 2008-04-10
> **sefs said:**
> Are you able to install pidgin from the repos and see if it works?  

I say this because Pidgin is the updated (new) version of gaim.

agreed.  Gaim is no longer supported

---

### Post by stevecoh1 on 2008-04-10
actually, it is PIdgin, I think.  "gaim" now seems to function as an alias for pidgin.  If I type pidgin -d it produces the same debugging output.  

On the Ubuntu Applications memo, Pidgin shows up, Gaim doesn't.  

Bottom line - neither works, both fail the same way.

---

### Post by -Zeus- on 2008-04-10
try running these commands:
```
sudo apt-get remove gaim
sudo apt-get install pidgin
```

Just to be sure

---

### Post by stevecoh1 on 2008-04-10
No joy::(

$ sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gaim
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112425 files and directories currently installed.)
Removing gaim ...

$ sudo apt-get remove pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pidgin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1761kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112412 files and directories currently installed.)
Removing pidgin ...

$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pidgin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 603kB of archives.
After unpacking 1761kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main pidgin 1:2.2.1-1ubuntu4.1 [603kB]
Fetched 603kB in 7s (85.1kB/s)                                                 
Selecting previously deselected package pidgin.
(Reading database ... 112379 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_1%3a2.2.1-1ubuntu4.1_i386.deb) ...
Setting up pidgin (1:2.2.1-1ubuntu4.1) ...

$ pidgin -d
(10:53:54) prefs: Reading /home/scohen/.purple/prefs.xml
(10:53:54) prefs: Finished reading /home/scohen/.purple/prefs.xml
(10:53:54) dbus: okkk
(10:53:54) plugins: probing /usr/lib/pidgin/gestures.so
(10:53:54) plugins: probing /usr/lib/pidgin/spellchk.so
(10:53:54) plugins: probing /usr/lib/pidgin/musicmessaging.so
(10:53:54) plugins: probing /usr/lib/pidgin/timestamp.so
(10:53:54) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(10:53:54) plugins: probing /usr/lib/pidgin/extplacement.so
(10:53:54) plugins: probing /usr/lib/pidgin/nautilus.so
(10:53:54) plugins: probing /usr/lib/pidgin/iconaway.so
(10:53:54) plugins: probing /usr/lib/pidgin/cap.so
(10:53:54) plugins: probing /usr/lib/pidgin/pidginrc.so
(10:53:54) plugins: probing /usr/lib/pidgin/xmppconsole.so
(10:53:54) plugins: probing /usr/lib/pidgin/markerline.so
(10:53:54) plugins: probing /usr/lib/pidgin/convcolors.so
(10:53:54) plugins: probing /usr/lib/pidgin/ticker.so
(10:53:54) plugins: probing /usr/lib/pidgin/timestamp_format.so
(10:53:54) plugins: probing /usr/lib/pidgin/gevolution.so
(10:53:54) plugins: probing /usr/lib/pidgin/history.so
(10:53:54) plugins: probing /usr/lib/pidgin/notify.so
(10:53:54) plugins: probing /usr/lib/purple-2/libirc.so
(10:53:54) plugins: probing /usr/lib/purple-2/liboscar.so
(10:53:54) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(10:53:54) plugins: probing /usr/lib/purple-2/ssl-nss.so
(10:53:54) plugins: probing /usr/lib/purple-2/autoaccept.so
(10:53:54) plugins: probing /usr/lib/purple-2/offlinemsg.so
(10:53:54) plugins: probing /usr/lib/purple-2/newline.so
(10:53:54) plugins: probing /usr/lib/purple-2/perl.so
(10:53:54) plugins: probing /usr/lib/purple-2/libgg.so
(10:53:54) plugins: probing /usr/lib/purple-2/idle.so
(10:53:54) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(10:53:54) plugins: probing /usr/lib/purple-2/log_reader.so
(10:53:54) plugins: probing /usr/lib/purple-2/libmsn.so
(10:53:54) plugins: probing /usr/lib/purple-2/libqq.so
(10:53:54) plugins: probing /usr/lib/purple-2/libnovell.so
(10:53:54) plugins: probing /usr/lib/purple-2/libsametime.so
(10:53:54) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(10:53:54) plugins: probing /usr/lib/purple-2/libmyspace.so
(10:53:54) plugins: probing /usr/lib/purple-2/psychic.so
(10:53:54) plugins: probing /usr/lib/purple-2/ssl.so
(10:53:54) plugins: probing /usr/lib/purple-2/dbus-example.so
(10:53:54) plugins: probing /usr/lib/purple-2/libyahoo.so
(10:53:54) plugins: probing /usr/lib/purple-2/libicq.so
(10:53:54) plugins: probing /usr/lib/purple-2/statenotify.so
(10:53:54) plugins: probing /usr/lib/purple-2/buddynote.so
(10:53:54) plugins: probing /usr/lib/purple-2/libzephyr.so
(10:53:54) plugins: probing /usr/lib/purple-2/libaim.so
(10:53:54) plugins: probing /usr/lib/purple-2/joinpart.so
(10:53:54) plugins: probing /usr/lib/purple-2/libsimple.so
(10:53:54) plugins: probing /usr/lib/purple-2/libjabber.so
(10:53:54) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(10:53:54) plugins: probing /usr/lib/purple-2/tcl.so
(10:53:54) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(10:53:54) plugins: probing /usr/lib/purple-2/libbonjour.so
(10:53:54) plugins: probing /usr/lib/purple-2/libxmpp.so
(10:53:54) util: Reading file xmpp-caps.xml from directory /home/scohen/.purple
(10:53:54) util: File /home/scohen/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(10:53:54) prefs: /purple/status/scores/offline changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/available changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/invisible changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/away changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/extended_away changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/idle changed, scheduling save.
(10:53:54) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(10:53:54) util: Reading file accounts.xml from directory /home/scohen/.purple
(10:53:54) util: Reading file status.xml from directory /home/scohen/.purple
(10:53:54) certificate: CertificateVerifier x509, singleuse requested but not found.
(10:53:54) certificate: CertificateVerifier singleuse registered
(10:53:54) certificate: CertificatePool x509, ca requested but not found.
(10:53:54) certificate: CertificateScheme x509 requested but not found.
(10:53:54) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(10:53:54) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(10:53:54) certificate: CertificatePool ca registered
(10:53:54) certificate: CertificatePool x509, tls_peers requested but not found.
(10:53:54) certificate: CertificatePool tls_peers registered
(10:53:54) certificate: CertificateVerifier x509, tls_cached requested but not found.
(10:53:54) certificate: CertificateVerifier tls_cached registered
(10:53:54) prefs: /purple/logging/format changed, scheduling save.
(10:53:54) prefs: /purple/logging/format changed, scheduling save.
(10:53:54) prefs: /purple/proxy/type changed, scheduling save.
(10:53:54) prefs: /purple/proxy/host changed, scheduling save.
(10:53:54) prefs: /purple/proxy/port changed, scheduling save.
(10:53:54) prefs: /purple/proxy/username changed, scheduling save.
(10:53:54) prefs: /purple/proxy/password changed, scheduling save.
(10:53:54) certificate: CertificateScheme x509 requested but not found.
(10:53:54) certificate: CertificateScheme x509 registered
(10:53:54) stun: using server 
(10:53:54) sound: Initializing sound output drivers.
(10:53:54) prefs: /pidgin/conversations/placement changed, scheduling save.
(10:53:54) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(10:53:54) gtkblist: added visibility manager: 1
(10:53:54) docklet: created
(10:53:54) blist: Attempted to save buddy list before it was read!
(10:53:54) certificate: CertificateScheme x509 unregistered
(10:53:54) certificate: CertificateVerifier tls_cached unregistered
(10:53:54) certificate: CertificateVerifier singleuse unregistered
(10:53:54) certificate: CertificatePool tls_peers unregistered
(10:53:54) certificate: CertificatePool ca unregistered
(10:53:54) util: Writing file accounts.xml to directory /home/scohen/.purple
(10:53:54) util: Writing file /home/scohen/.purple/accounts.xml
(10:53:54) util: Writing file prefs.xml to directory /home/scohen/.purple
(10:53:54) util: Writing file /home/scohen/.purple/prefs.xml
(10:53:54) main: Unloading all plugins
(10:53:54) plugins: Unloading plugin IRC
(10:53:54) plugins: Unloading plugin NSS
(10:53:54) certificate: CertificateScheme x509 unregistered
(10:53:54) plugins: Unloading plugin Perl Plugin Loader
(10:53:54) plugins: Unloading plugin Gadu-Gadu
(10:53:54) plugins: Unloading plugin MSN
(10:53:54) plugins: Unloading plugin QQ
(10:53:54) plugins: Unloading plugin GroupWise
(10:53:54) plugins: Unloading plugin Sametime
(10:53:54) plugins: Unloading plugin MySpaceIM
(10:53:54) plugins: Unloading plugin SSL
(10:53:54) plugins: Unloading plugin Yahoo
(10:53:54) plugins: Unloading plugin ICQ
(10:53:54) plugins: Unloading plugin Zephyr
(10:53:54) plugins: Unloading plugin AIM
(10:53:54) plugins: Unloading plugin SIMPLE
(10:53:54) plugins: Unloading plugin Bonjour
(10:53:54) plugins: Unloading plugin XMPP
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) accels: accel changed, scheduling save.
(10:53:54) gtkblist: removed visibility manager: 0
(10:53:54) docklet: destroyed
(10:53:54) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
$

---

### Post by -Zeus- on 2008-04-10
I get that message on my system if I start pidgin while it's already running... I assume that this is not the case?  do this:

```
ps -efww|grep pidgin
```
and post that

---

### Post by stevecoh1 on 2008-04-10
Well, you're onto something, but I'm not sure what it means.

After I launch pidgin and run your ps command I get this:

$ ps -efww | grep pidgin
scohen   17976     1  1 11:55 ?        00:00:00 pidgin
scohen   17986 13903  0 11:56 pts/2    00:00:00 grep pidgin

So it left a process running.

But why don't I see any GUI?  On closer examination when launched from the menu, there's a little "wait" icon that pops up for about 15 seconds, then it dies, and leaves the process running.

So I kill the process and then try running pidgin -d again now that pidgin isn't running.  I get different output then:  Some of it looks "errorish" but I'm not sure what any of it means.

$ pidgin -d
(12:05:25) prefs: Reading /home/scohen/.purple/prefs.xml
(12:05:25) prefs: Finished reading /home/scohen/.purple/prefs.xml
(12:05:25) dbus: okkk
(12:05:25) plugins: probing /usr/lib/pidgin/gestures.so
(12:05:25) plugins: probing /usr/lib/pidgin/spellchk.so
(12:05:25) plugins: probing /usr/lib/pidgin/musicmessaging.so
(12:05:25) plugins: probing /usr/lib/pidgin/timestamp.so
(12:05:25) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(12:05:25) plugins: probing /usr/lib/pidgin/extplacement.so
(12:05:25) plugins: probing /usr/lib/pidgin/nautilus.so
(12:05:25) plugins: probing /usr/lib/pidgin/iconaway.so
(12:05:25) plugins: probing /usr/lib/pidgin/cap.so
(12:05:25) plugins: probing /usr/lib/pidgin/pidginrc.so
(12:05:25) plugins: probing /usr/lib/pidgin/xmppconsole.so
(12:05:25) plugins: probing /usr/lib/pidgin/markerline.so
(12:05:25) plugins: probing /usr/lib/pidgin/convcolors.so
(12:05:25) plugins: probing /usr/lib/pidgin/ticker.so
(12:05:25) plugins: probing /usr/lib/pidgin/timestamp_format.so
(12:05:25) plugins: probing /usr/lib/pidgin/gevolution.so
(12:05:25) plugins: probing /usr/lib/pidgin/history.so
(12:05:25) plugins: probing /usr/lib/pidgin/notify.so
(12:05:25) plugins: probing /usr/lib/purple-2/libirc.so
(12:05:25) plugins: probing /usr/lib/purple-2/liboscar.so
(12:05:25) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:05:25) plugins: probing /usr/lib/purple-2/ssl-nss.so
(12:05:25) plugins: probing /usr/lib/purple-2/autoaccept.so
(12:05:25) plugins: probing /usr/lib/purple-2/offlinemsg.so
(12:05:25) plugins: probing /usr/lib/purple-2/newline.so
(12:05:25) plugins: probing /usr/lib/purple-2/perl.so
(12:05:25) plugins: probing /usr/lib/purple-2/libgg.so
(12:05:25) plugins: probing /usr/lib/purple-2/idle.so
(12:05:25) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(12:05:25) plugins: probing /usr/lib/purple-2/log_reader.so
(12:05:25) plugins: probing /usr/lib/purple-2/libmsn.so
(12:05:25) plugins: probing /usr/lib/purple-2/libqq.so
(12:05:25) plugins: probing /usr/lib/purple-2/libnovell.so
(12:05:25) plugins: probing /usr/lib/purple-2/libsametime.so
(12:05:25) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(12:05:25) plugins: probing /usr/lib/purple-2/libmyspace.so
(12:05:25) plugins: probing /usr/lib/purple-2/psychic.so
(12:05:25) plugins: probing /usr/lib/purple-2/ssl.so
(12:05:25) plugins: probing /usr/lib/purple-2/dbus-example.so
(12:05:25) plugins: probing /usr/lib/purple-2/libyahoo.so
(12:05:25) plugins: probing /usr/lib/purple-2/libicq.so
(12:05:25) plugins: probing /usr/lib/purple-2/statenotify.so
(12:05:25) plugins: probing /usr/lib/purple-2/buddynote.so
(12:05:25) plugins: probing /usr/lib/purple-2/libzephyr.so
(12:05:25) plugins: probing /usr/lib/purple-2/libaim.so
(12:05:25) plugins: probing /usr/lib/purple-2/joinpart.so
(12:05:25) plugins: probing /usr/lib/purple-2/libsimple.so
(12:05:25) plugins: probing /usr/lib/purple-2/libjabber.so
(12:05:25) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:05:25) plugins: probing /usr/lib/purple-2/tcl.so
(12:05:25) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(12:05:25) plugins: probing /usr/lib/purple-2/libbonjour.so
(12:05:25) plugins: probing /usr/lib/purple-2/libxmpp.so
(12:05:25) util: Reading file xmpp-caps.xml from directory /home/scohen/.purple
(12:05:25) util: File /home/scohen/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(12:05:25) prefs: /purple/status/scores/offline changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/available changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/invisible changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/away changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/extended_away changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/idle changed, scheduling save.
(12:05:25) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(12:05:25) util: Reading file accounts.xml from directory /home/scohen/.purple
(12:05:25) util: Reading file status.xml from directory /home/scohen/.purple
(12:05:25) certificate: CertificateVerifier x509, singleuse requested but not found.
(12:05:25) certificate: CertificateVerifier singleuse registered
(12:05:25) certificate: CertificatePool x509, ca requested but not found.
(12:05:25) certificate: CertificateScheme x509 requested but not found.
(12:05:25) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(12:05:25) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(12:05:25) certificate: CertificatePool ca registered
(12:05:25) certificate: CertificatePool x509, tls_peers requested but not found.
(12:05:25) certificate: CertificatePool tls_peers registered
(12:05:25) certificate: CertificateVerifier x509, tls_cached requested but not found.
(12:05:25) certificate: CertificateVerifier tls_cached registered
(12:05:25) prefs: /purple/logging/format changed, scheduling save.
(12:05:25) prefs: /purple/logging/format changed, scheduling save.
(12:05:25) prefs: /purple/proxy/type changed, scheduling save.
(12:05:25) prefs: /purple/proxy/host changed, scheduling save.
(12:05:25) prefs: /purple/proxy/port changed, scheduling save.
(12:05:25) prefs: /purple/proxy/username changed, scheduling save.
(12:05:25) prefs: /purple/proxy/password changed, scheduling save.
(12:05:25) certificate: CertificateScheme x509 requested but not found.
(12:05:25) certificate: CertificateScheme x509 registered
(12:05:25) stun: using server 
(12:05:25) sound: Initializing sound output drivers.
(12:05:25) prefs: /pidgin/conversations/placement changed, scheduling save.
(12:05:25) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(12:05:25) gtkblist: added visibility manager: 1
(12:05:25) docklet: created
(12:05:25) util: Reading file blist.xml from directory /home/scohen/.purple
(12:05:25) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(12:05:25) pounce: Error reading pounces: Failed to open file '/home/scohen/.purple/pounces.xml': No such file or directory
(12:05:25) Session Management: ICE initialized.
(12:05:25) Session Management: Connecting with no previous ID
(12:05:25) Session Management: Handling new ICE connection... (12:05:25) done.
(12:05:25) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000120784712500000057320050
(12:05:25) Session Management: Using pidgin as command
(12:05:25) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(12:05:25) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(12:05:25) Session Management: Received first save_yourself
(12:05:25) Session Management: Received save_complete
(12:05:25) docklet: embedded
(12:05:25) network: Entering nm_callback_func!
(12:05:25) autorecon: do_signon called
(12:05:30) util: Writing file prefs.xml to directory /home/scohen/.purple
(12:05:30) util: Writing file /home/scohen/.purple/prefs.xml
(12:05:30) util: Writing file accounts.xml to directory /home/scohen/.purple
(12:05:30) util: Writing file /home/scohen/.purple/accounts.xml
(12:05:30) util: Writing file blist.xml to directory /home/scohen/.purple
(12:05:30) util: Writing file /home/scohen/.purple/blist.xml

---

### Post by -Zeus- on 2008-04-10
Are you sure that you have the notification panel on the taskbar so you could see it if it's hidden to the tray?

---

### Post by stevecoh1 on 2008-04-10
Duh, thanks!

I didn't realize it was popping up as a tray icon (or that that behavior even existed).  It hadn't been doing that before.

---

