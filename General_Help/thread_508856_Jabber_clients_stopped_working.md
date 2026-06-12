---
title: "Jabber clients stopped working?"
date: 2007-07-24
forum: General Help
---

### Post by Falcongirl on 2007-07-24
Hi. I have a problem and I'm not sure which side of things it's on. I use Gajim to connect to google talk. I have Ubuntu Feisty installed on the latest release with all updates. It's been working fine for months, and then last week it stopped working in the middle of a session and has timed out every time I've tried to connect since. I thought maybe the client had gone bad, so I uninstalled/reinstalled, deleted the account and re-added the data - nothing. I installed other jabber clients, gaim, psi, gabber, and none of them will connect either. I have ports 5222 and 5223 forwarded through my firewall, but even when I turn the firewall off completely, still no connect. I posted the question on the gtalk forums and got no answer. The Gtalk widget both in gmail and standalone connects just fine. 

Is anyone else having this problem? I don't have other IM accounts, so can't test it with any of them. 

Below is a c/p of what a pidgin -d gives me
dbus: okkk
plugins: probing /usr/lib/pidgin/xmppconsole.so
plugins: probing /usr/lib/pidgin/timestamp.so
plugins: probing /usr/lib/pidgin/history.so
plugins: probing /usr/lib/pidgin/musicmessaging.so
plugins: probing /usr/lib/pidgin/iconaway.so
plugins: probing /usr/lib/pidgin/extplacement.so
plugins: probing /usr/lib/pidgin/ticker.so
plugins: probing /usr/lib/pidgin/relnot.so
plugins: probing /usr/lib/pidgin/pidginrc.so
plugins: probing /usr/lib/pidgin/cap.so
plugins: probing /usr/lib/pidgin/markerline.so
plugins: probing /usr/lib/pidgin/spellchk.so
plugins: probing /usr/lib/pidgin/gestures.so
plugins: probing /usr/lib/pidgin/timestamp_format.so
plugins: probing /usr/lib/pidgin/notify.so
plugins: probing /usr/lib/pidgin/convcolors.so
plugins: probing /usr/lib/purple-2/dbus-example.so
plugins: probing /usr/lib/purple-2/libxmpp.so
plugins: probing /usr/lib/purple-2/autoaccept.so
plugins: probing /usr/lib/purple-2/libsimple.so
plugins: probing /usr/lib/purple-2/offlinemsg.so
plugins: probing /usr/lib/purple-2/statenotify.so
plugins: probing /usr/lib/purple-2/log_reader.so
plugins: probing /usr/lib/purple-2/libaim.so
plugins: probing /usr/lib/purple-2/libgg.so
plugins: probing /usr/lib/purple-2/libsametime.so
plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/purple-2/perl.so
plugins: probing /usr/lib/purple-2/buddynote.so
plugins: probing /usr/lib/purple-2/libqq.so
plugins: probing /usr/lib/purple-2/psychic.so
plugins: probing /usr/lib/purple-2/libjabber.so
plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
plugins: probing /usr/lib/purple-2/liboscar.so
plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
plugins: probing /usr/lib/purple-2/libicq.so
plugins: probing /usr/lib/purple-2/libsilcpurple.so
plugins: probing /usr/lib/purple-2/ssl-nss.so
plugins: probing /usr/lib/purple-2/libmsn.so
plugins: probing /usr/lib/purple-2/newline.so
plugins: probing /usr/lib/purple-2/idle.so
plugins: probing /usr/lib/purple-2/libirc.so
plugins: probing /usr/lib/purple-2/ssl.so
plugins: probing /usr/lib/purple-2/libzephyr.so
plugins: probing /usr/lib/purple-2/tcl.so
plugins: probing /usr/lib/purple-2/ssl-gnutls.so
plugins: probing /usr/lib/purple-2/joinpart.so
plugins: probing /usr/lib/purple-2/libbonjour.so
plugins: probing /usr/lib/purple-2/libyahoo.so
plugins: probing /usr/lib/purple-2/libnovell.so
util: Reading file accounts.xml from directory /home/pere/.purple
util: Reading file status.xml from directory /home/pere/.purple
stun: using server 
stun: using server 
sound: Initializing sound output drivers.
gtkblist: added visibility manager: 1
docklet: created
util: Reading file blist.xml from directory /home/pere/.purple
prefs: Reading /home/pere/.purple/prefs.xml
prefs: Finished reading /home/pere/.purple/prefs.xml
plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
plugins: Loading saved plugin /usr/lib/pidgin/notify.so
pounce: Error reading pounces: Failed to open file '/home/pere/.purple/pounces.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 102bf07cb3000118531657400000054500042
Session Management: Using pidgin as command
dbus: Need to register an object with the dbus subsystem.
g_log: file dbus-server.c: line 118 (purple_dbus_pointer_to_id): should not be reached
Session Management: Received first save_yourself
prefs: /pidgin/blist/list_visible changed, scheduling save.
Session Management: Received save_complete
util: requested to fetch ([http://192.168.1.1:5431/dyndev/uuid:0006-25c0-a9e700009adc](http://192.168.1.1:5431/dyndev/uuid:0006-25c0-a9e700009adc)), full=1, user_agent=((null)), http11=1
dns: DNS query for '192.168.1.1' queued
dns: Created new DNS child 22045, there are now 1 children.
dns: Successfully sent DNS request to child 22045
docklet: embedded
network: Entering nm_callback_func!
dns: Got response for '192.168.1.1'
dnsquery: IP resolved for 192.168.1.1
proxy: Attempting connection to 192.168.1.1
proxy: Connecting to 192.168.1.1:5431 with no proxy
proxy: Connection in progress
proxy: Connected to 192.168.1.1:5431.
util: Request: 'GET /dyndev/uuid:0006-25c0-a9e700009adc HTTP/1.1
Connection: close
Host: 192.168.1.1:5431

'
util: Response headers: 'HTTP/1.0 200 OK
SERVER: LINUX/2.4 UPnP/1.0 BRCM400/1.0
DATE: Tue, 24 Jul 2007 17:34:46 GMT
CONTENT-TYPE: application/octet-stream
Cache-Control: max-age=1
PRAGMA: no-cache
Connection: Close

'
util: requested to fetch ([http://192.168.1.1:5431/uuid:0006-25c0-a9e702009adc/WANPPPConnection:1](http://192.168.1.1:5431/uuid:0006-25c0-a9e702009adc/WANPPPConnection:1)), full=0, user_agent=((null)), http11=1
dns: DNS query for '192.168.1.1' queued
dns: DNS query for '192.168.1.1' queued
dns: Created new DNS child 22048, there are now 1 children.
dns: Successfully sent DNS request to child 22048
dns: Created new DNS child 22049, there are now 2 children.
dns: Successfully sent DNS request to child 22049
dns: Got response for '192.168.1.1'
dnsquery: IP resolved for 192.168.1.1
proxy: Attempting connection to 192.168.1.1
proxy: Connecting to 192.168.1.1:5431 with no proxy
proxy: Connection in progress
proxy: Connected to 192.168.1.1:5431.
util: Request: 'POST /uuid:0006-25c0-a9e702009adc/WANPPPConnection:1 HTTP/1.1
HOST: 192.168.1.1:5431
SOAPACTION: "urn:schemas-upnp-org:service:WANPPPConnection:1#GetExternalIPAddress"
CONTENT-TYPE: text/xml ; charset="utf-8"
CONTENT-LENGTH: 311

<?xml version="1.0" encoding="utf-8"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" s:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<s:Body>
<u:GetExternalIPAddress xmlns:u="urn:schemas-upnp-org:service:WANPPPConnection:1">
</u:GetExternalIPAddress>
</s:Body>
</s:Envelope>'
dns: Got response for '192.168.1.1'
dnsquery: IP resolved for 192.168.1.1
proxy: Attempting connection to 192.168.1.1
proxy: Connecting to 192.168.1.1:5431 with no proxy
proxy: Connection in progress
util: Response headers: 'HTTP/1.1 200 OK
DATE: Tue, 24 Jul 2007 17:34:46 GMT
Connection: Keep-Alive
Server: LINUX/2.4 UPnP/1.0 BRCM400/1.0
Content-Length: 361
Content-Type: text/xml; charset="utf-8"
EXT:

'
util: parsed 361
upnp: NAT Returned IP: 24.118.123.251
proxy: Connected to 192.168.1.1:5431.
upnp: Local IP: 192.168.1.100
account: Connecting to account [email]falcongirl@gmail.com[/email]/Home
connection: Connecting. gc = 0x8536a80
dns: DNS query for 'gmail.com' queued
dns: Created new DNS child 22053, there are now 1 children.
dns: Successfully sent DNS request to child 22053
util: Writing file accounts.xml to directory /home/pere/.purple
util: Writing file blist.xml to directory /home/pere/.purple
dns: Got response for 'gmail.com'
dnsquery: IP resolved for gmail.com
proxy: Attempting connection to 72.14.253.83
proxy: Connecting to gmail.com:5222 with no proxy
proxy: Connection in progress
util: Writing file status.xml to directory /home/pere/.purple
util: Writing file prefs.xml to directory /home/pere/.purple


And that's where it sits, not connecting, until eventually it tells me iit times out.

---

### Post by zanglang on 2007-07-25
Not sure what's wrong there, any chance your ISP could have blocked that port?

In Gaim/Pidgin, try ticking Use SSL in your Jabber/GTalk settings, and change the port to 443. Does that work?

---

### Post by Falcongirl on 2007-07-25
Maybe, but I don't see why they would? It's Comcrap, so who knows. 

Using SSL, Pidgin reverts to port 5223. Nada. Forcing port 443, also nada. Forcing a port I know is open via my firewall, nada. I'm totally stumped :(

---

### Post by tronica on 2007-07-26
I too am having the same problem.  If i use the web client in gmail. it works fine. Anyone have any ideas?

---

### Post by getaceres on 2007-07-31
Same here. It was working well until two or three days ago. Now Gaim can't connect, Kopete connects but communication is not very good I don't know why. There are messages lost and they take a long time to arrive. Using the chat option in gmail directly works well. 
I live in Spain by the way.

---

### Post by ari.maidana on 2007-08-03
I have the same problem. Kopete can't connect for an "unknown reason". Pidgin reports a SSL negotiation error. :(

---

