---
title: "Cannot connect to any IRC server: connection refused"
date: 2007-08-17
forum: General Help
---

### Post by PhilipGanchev on 2007-08-17
I am unable to connect to any IRC server.  Gaim 2.0.0beta6 says "Disconnected", while Xchat a2.8.0-0ubuntu4 nd Irssi 0.8.10-2ubuntu1 say "Connection refused".  I am running an up-to-date Ubuntu Feisty.  

For example, in Gaim, I select Accounts -> Add/Edit, delete all IRC accounts, click "Add", select "IRC" from the list of protocols, choose a screen name, enter the server "irc.ubuntu.com", leave the password blank, leave the local alias blank, open the "Advanced" tab, ensure that the port is "6667", enter a username, enter my real name, leave the default proxy options, and finally select "Save".  I enable the new irc account, and a red button with the account name appears in the buddy list.  I click the button and get an error window:

[email]pgan002@irc.ubuntu.com[/email] disconnected
Couldn't connect to host
[Connect]  [Modify Account]  [OK]

This happens after I rename my ~/.gaim file and "sudo apt-get remove --purge gaim", and then install Gaim again.

When I run Gaim in debug mode, the output is:

% gaim --debug
dbus: okkk
plugins: probing /usr/lib/gaim/autoaccept.so
plugins: probing /usr/lib/gaim/autoreply.so
plugins: probing /usr/lib/gaim/buddynote.so
plugins: probing /usr/lib/gaim/convcolors.so
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/gntgf.so
plugins: /usr/lib/gaim/gntgf.so is not loadable: The UI requirement is not met.
plugins: probing /usr/lib/gaim/gnthistory.so
plugins: /usr/lib/gaim/gnthistory.so is not loadable: The UI requirement is not met.
plugins: probing /usr/lib/gaim/gntlastlog.so
plugins: /usr/lib/gaim/gntlastlog.so is not loadable: undefined symbol: cur_term
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libaim.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libicq.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libqq.so
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is not loadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/log_reader.so
plugins: probing /usr/lib/gaim/markerline.so
plugins: probing /usr/lib/gaim/offlinemsg.so
plugins: probing /usr/lib/gaim/newline.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/s.so
plugins: /usr/lib/gaim/s.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/xmppconsole.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: /usr/lib/gaim/liboscar.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
util: Reading file accounts.xml from directory /home/philip/.gaim
util: File /home/philip/.gaim/accounts.xml does not exist (this is not necessarily an error)
util: Reading file status.xml from directory /home/philip/.gaim
util: File /home/philip/.gaim/status.xml does not exist (this is not necessarily an error)
stun: using server
stun: using server
sound: Initializing sound output drivers.
util: Reading file blist.xml from directory /home/philip/.gaim
util: File /home/philip/.gaim/blist.xml does not exist (this is not necessarily an error)
prefs: Reading /home/philip/.gaim/prefs.xml
prefs: Reading /etc/gaim/prefs.xml
prefs: gaim_prefs_set_string_list: /gaim/gtk/plugins/loaded not a string list pref
prefs: Finished reading /etc/gaim/prefs.xml
plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
plugins: Loading saved plugin /usr/lib/gaim/notify.so
gtkblist: added visibility manager: 1
docklet: created
pounce: Error reading pounces: Failed to open file '/home/philip/.gaim/pounces.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 117f000101000118740485400000053930032
Session Management: Using gaim as command
prefs: /core/savedstatus/default changed, scheduling save.
dbus: Need to register an object with the dbus subsystem.
g_log: file ../../libgaim/dbus-server.c: line 118 (gaim_dbus_pointer_to_id): should not be reached
Session Management: Received first save_yourself
Session Management: Received save_complete
docklet: embedded
prefs: /gaim/gtk/blist/y changed, scheduling save.
network: Entering nm_callback_func!
util: Writing file status.xml to directory /home/philip/.gaim
util: Writing file prefs.xml to directory /home/philip/.gaim
account: Connecting to account [email]pgan003@irc.ubuntu.com[/email]
connection: Connecting. gc = 0x853de08
dns: DNS query for 'irc.ubuntu.com' queued
dns: Created new DNS child 14277, there are now 1 children.
dns: Successfully sent DNS request to child 14277
dns: Got response for 'irc.ubuntu.com'
dnsquery: IP resolved for irc.ubuntu.com
proxy: Attempting connection to 140.211.166.3
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 140.211.166.4
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 207.158.1.150
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 208.71.169.36
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 213.92.8.4
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 216.165.191.52
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 204.11.244.21
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 64.161.255.20
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
proxy: Attempting connection to 82.96.64.4
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
account: Disconnecting account 0x8562eb0
connection: Disconnecting connection 0x853de08
connection: Destroying connection 0x853de08
util: Writing file accounts.xml to directory /home/philip/.gaim
util: Writing file blist.xml to directory /home/philip/.gaim
autorecon: do_signon called
autorecon: calling gaim_account_connect
account: Connecting to account [email]pgan003@irc.ubuntu.com[/email]
connection: Connecting. gc = 0x8538398
dns: DNS query for 'irc.ubuntu.com' queued
autorecon: done calling gaim_account_connect
dns: Created new DNS child 14282, there are now 1 children.
dns: Successfully sent DNS request to child 14282
dns: Got response for 'irc.ubuntu.com'
dnsquery: IP resolved for irc.ubuntu.com
proxy: Attempting connection to 140.211.166.3
proxy: Connecting to irc.ubuntu.com:6667 with no proxy
proxy: Connection in progress
proxy: Connected.
proxy: Connection attempt failed: Connection refused
[...]


Any suggestions?

---

