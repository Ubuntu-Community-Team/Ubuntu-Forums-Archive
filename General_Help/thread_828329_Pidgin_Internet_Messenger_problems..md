---
title: "Pidgin Internet Messenger problems."
date: 2008-06-13
forum: General Help
---

### Post by Riptcage on 2008-06-13
Hardy Heron 8.04

Pidgin was working like a charm till today randomly...i open it and it shows up on the bottom dock as starting... and then quits ..never fully starts up. Anyone else have this kind of proble?m before? is there something i'm not doing? 
ANy help would be great, thanks!

---

### Post by drs305 on 2008-06-13
Run this to see if pidgin actually is running. For me, it starts and about a minute later the pidgin icon appears on the panel. Could it be it's having problems connecting to the internet?

```
ps aux | grep pidgin
```

I've PM'd you if you need to test it.

---

### Post by spupy on 2008-06-13
The first step in finding out why a program is not working:
1. Open a terminal, type the name of the program and press Enter.
If the program doesn't start and quits with some problem, it will print the errors to the terminal. Copy-paste these errors here, we can then analyze the problem.

---

### Post by Riptcage on 2008-06-13
ok well..for some reason i typed in pidgin in terminal and at first did nothing...and i guess i didnt wait long enough...cuz i had logged off and logged back in and tried it and now its working...i dont get it.. anyways. Thanks for the help guys! =]

---

### Post by I3lue on 2008-06-15
well...i opened up the terminal and i typed in pidgin...i get the exact same problem ive been having for 2 days :(
(i try to run pidgin and each time my processor goes up to 100% in use and pidgin appears to be running in the proccesses window in System Monitor but actually the place where the pidgin mini-icon should appear is there but there's no icon -if you understand what i mean-)
Terminal doesn't say anything after i type in pidgin and press enter

If you want i can put in some screenshots.

---

### Post by Bluefish001 on 2008-06-16
I just had that same problem.

I tried the terminal but nothing happened.


Pidgin 

runs, then nothing.


thanks

---

### Post by crewof502 on 2008-06-17
I'm having similar issues with pidgin.  It never starts and this is the debug I am seeing when running pidgin from the console.  It stops at Using Pidgin as command...

```
photek@d3skt0p:~$ pidgin -d
(19:20:42) prefs: Reading /home/photek/.purple/prefs.xml
(19:20:42) prefs: Finished reading /home/photek/.purple/prefs.xml
(19:20:42) prefs: removing pref /pidgin/browsers/command
(19:20:42) dbus: okkk
(19:20:42) plugins: probing /usr/lib/pidgin/pidginrc.so
(19:20:42) plugins: probing /usr/lib/pidgin/notify.so
(19:20:42) plugins: probing /usr/lib/pidgin/musicmessaging.so
(19:20:42) plugins: probing /usr/lib/pidgin/convcolors.so
(19:20:42) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(19:20:42) plugins: probing /usr/lib/pidgin/xmppconsole.so
(19:20:42) plugins: probing /usr/lib/pidgin/extplacement.so
(19:20:42) plugins: probing /usr/lib/pidgin/gestures.so
(19:20:42) plugins: probing /usr/lib/pidgin/history.so
(19:20:42) plugins: probing /usr/lib/pidgin/spellchk.so
(19:20:42) plugins: probing /usr/lib/pidgin/timestamp.so
(19:20:42) plugins: probing /usr/lib/pidgin/markerline.so
(19:20:42) plugins: probing /usr/lib/pidgin/iconaway.so
(19:20:42) plugins: probing /usr/lib/pidgin/timestamp_format.so
(19:20:42) plugins: probing /usr/lib/pidgin/ticker.so
(19:20:42) plugins: probing /usr/lib/pidgin/nautilus.so
(19:20:42) plugins: probing /usr/lib/pidgin/cap.so
(19:20:42) plugins: probing /usr/lib/pidgin/gevolution.so
(19:20:42) plugins: probing /usr/lib/purple-2/buddynote.so
(19:20:42) plugins: probing /usr/lib/purple-2/offlinemsg.so
(19:20:42) plugins: probing /usr/lib/purple-2/idle.so
(19:20:42) plugins: probing /usr/lib/purple-2/autoaccept.so
(19:20:42) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(19:20:42) plugins: probing /usr/lib/purple-2/libqq.so
(19:20:42) plugins: probing /usr/lib/purple-2/newline.so
(19:20:42) plugins: probing /usr/lib/purple-2/liboscar.so
(19:20:42) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:20:42) plugins: probing /usr/lib/purple-2/libnovell.so
(19:20:42) plugins: probing /usr/lib/purple-2/libmyspace.so
(19:20:42) plugins: probing /usr/lib/purple-2/dbus-example.so
(19:20:42) plugins: probing /usr/lib/purple-2/libgg.so
(19:20:42) plugins: probing /usr/lib/purple-2/libmsn.so
(19:20:42) plugins: probing /usr/lib/purple-2/statenotify.so
(19:20:42) plugins: probing /usr/lib/purple-2/libaim.so
(19:20:42) prefs: removing pref /plugins/prpl/oscar/show_idle
(19:20:42) plugins: probing /usr/lib/purple-2/libsametime.so
(19:20:42) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(19:20:42) plugins: probing /usr/lib/purple-2/ssl-nss.so
(19:20:42) plugins: probing /usr/lib/purple-2/perl.so
(19:20:42) plugins: probing /usr/lib/purple-2/libirc.so
(19:20:42) plugins: probing /usr/lib/purple-2/libjabber.so
(19:20:42) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:20:42) plugins: probing /usr/lib/purple-2/libicq.so
(19:20:42) plugins: probing /usr/lib/purple-2/libxmpp.so
(19:20:42) util: Reading file xmpp-caps.xml from directory /home/photek/.purple
(19:20:42) plugins: probing /usr/lib/purple-2/libyahoo.so
(19:20:42) plugins: probing /usr/lib/purple-2/libbonjour.so
(19:20:42) plugins: probing /usr/lib/purple-2/tcl.so
(19:20:42) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(19:20:42) plugins: probing /usr/lib/purple-2/log_reader.so
(19:20:42) plugins: probing /usr/lib/purple-2/psychic.so
(19:20:42) plugins: probing /usr/lib/purple-2/ssl.so
(19:20:42) plugins: probing /usr/lib/purple-2/libsimple.so
(19:20:42) plugins: probing /usr/lib/purple-2/libzephyr.so
(19:20:42) plugins: probing /usr/lib/purple-2/joinpart.so
(19:20:42) prefs: /purple/status/scores/offline changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/available changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/invisible changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/away changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/extended_away changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/idle changed, scheduling save.
(19:20:42) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(19:20:42) util: Reading file accounts.xml from directory /home/photek/.purple
(19:20:42) util: Reading file status.xml from directory /home/photek/.purple
(19:20:42) certificate: CertificateVerifier x509, singleuse requested but not found.
(19:20:42) certificate: CertificateVerifier singleuse registered
(19:20:42) certificate: CertificatePool x509, ca requested but not found.
(19:20:42) certificate: CertificateScheme x509 requested but not found.
(19:20:42) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(19:20:42) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(19:20:42) certificate: CertificatePool ca registered
(19:20:42) certificate: CertificatePool x509, tls_peers requested but not found.
(19:20:42) certificate: CertificatePool tls_peers registered
(19:20:42) certificate: CertificateVerifier x509, tls_cached requested but not found.
(19:20:42) certificate: CertificateVerifier tls_cached registered
(19:20:42) prefs: /purple/logging/format changed, scheduling save.
(19:20:42) prefs: /purple/logging/format changed, scheduling save.
(19:20:42) prefs: /purple/proxy/type changed, scheduling save.
(19:20:42) prefs: /purple/proxy/host changed, scheduling save.
(19:20:42) prefs: /purple/proxy/port changed, scheduling save.
(19:20:42) prefs: /purple/proxy/username changed, scheduling save.
(19:20:42) prefs: /purple/proxy/password changed, scheduling save.
(19:20:42) certificate: CertificateScheme x509 requested but not found.
(19:20:42) certificate: CertificateScheme x509 registered
(19:20:42) stun: using server 
(19:20:42) sound: Initializing sound output drivers.
(19:20:42) prefs: /pidgin/conversations/placement changed, scheduling save.
(19:20:42) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(19:20:42) gtkblist: added visibility manager: 1
(19:20:42) docklet: created
(19:20:42) util: Reading file blist.xml from directory /home/photek/.purple
(19:20:42) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(19:20:42) pounce: Error parsing /home/photek/.purple/pounces.xml
(19:20:42) ui_main: Failed to load the default window icon (scalablepx version)!
(19:20:42) Session Management: ICE initialized.
(19:20:42) Session Management: Connecting with no previous ID
(19:20:42) Session Management: Handling new ICE connection... 
(19:20:42) done.
(19:20:42) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000121374484200000064570020
(19:20:42) Session Management: Using pidgin as command
```

---

### Post by crewof502 on 2008-06-24
Seems as though I have fixed my issue... Here's how... (Straight from [www.pidgin.im](www.pidgin.im), I feel retarded)

"If your issue is a crash or is about a plugin, keep in mind that we are not a support forum for third-party plugins such as those in the Purple Plugin Pack, encryption plugins, etc. We did not develop those plugins and can't help you with those issues. (A sizable majority of crashes are caused by misbehaving plugins.)

    * Always make sure your plugins are of the most current version available.
    * If you are experiencing crashes, start disabling plugins you have loaded one by one until you eliminate the source of the crash. If your crash is a crash on startup, **you can try renaming the prefs.xml file in .purple to something such as prefs.xml.old to force a startup without plugins.** Note that this will lose all settings stored there.
          o If you renamed prefs.xml, enable plugins one at a time and try to reproduce the crash. Unload those plugins that don't cause the crash to aid troubleshooting. Once you have narrowed the cause down, continue with the instructions.
          o If disabling a specific plugin solves the crash, make sure your plugins are all updated to the most current release.
          o If all plugins are fully up to date, follow the instructions below to get a .RPT file (Windows users) or a backtrace (other OS users) and then report the crash to the authors of the plugin, not us. "

That worked for me.

---

### Post by skeletforce on 2008-11-30
Hey there, I have an issue myself... 
If I log in to pidgin, everything works normal, I can see who is online, what status they have, etc.
If I click a name to start a conversation with someone, the screen opens.
I can type in something to them, or they can initiate a chat with me.
BUT
As soon as I receive their message (wich I can read!), or as soon as my message is sent (and readable by the other person), everything turns grey and I am unable to perform any action within anything of pidgin.
I need to force quit.
When restarting pidgin everything goes the same just like I mentioned previously. My conversation (if you can call one message a convo, uhmm :) ) is logged, but then again, if I speak everything turns grey and is unable to work.

I started pidgin through my terminal, and it gave an error message right after sending or receiving a message through pidgin:

> W: shm.c: Failed to remove SHM segment /pulse-shm-1439192321: No such file or directory
E: shm.c: shm_open() failed: No such file or directory
E: shm.c: shm_open() failed: No such file or directory

Could anyone explain me what to do (asap :( )

Thanks in advance!!!

---

### Post by gychang on 2008-11-30
when I activate I can not connect (yahoo), I am "available" but does not connect, in windows yahoo messenger works fine.

any help or ideas?

gychang

---

### Post by smalleye86 on 2009-05-17
when i tried to open pidgin from the terminal, it displayed something like below:

~$ pidgin
Exiting because another libpurple client is already running.

what does it mean?

---

### Post by drs305 on 2009-05-17
> **smalleye86 said:**
> when i tried to open pidgin from the terminal, it displayed something like below:

~$ pidgin
Exiting because another libpurple client is already running.

what does it mean?

It means pidgin or another IM client may already be running. Try "sudo killall pidgin" first to make sure no other pidgin instances are running when you attempt to start it.

If you get the same message, you could run "ps aux | less" to see if you can find another app running which may be using libpurple. If you find one, try to close it and restart pidgin in terminal.

---

### Post by smalleye86 on 2009-05-18
thanks guys! it worked...

---

