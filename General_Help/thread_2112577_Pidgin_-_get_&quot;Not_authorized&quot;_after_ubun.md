---
title: "Pidgin - get &quot;Not authorized&quot; after ubuntu upgrade"
date: 2013-02-05
forum: General Help
---

### Post by isagarran on 2013-02-05
Hello,

After an Ubuntu 12.04 upgrade, i got Not authorized when I'm trying to connect to a sametime server.
Configuration is as :
    Client identity hidden
    Use environment parameters

There no other messages in logs. Pidgin is 12.10.3.0Ubuntu1.1 in synaptic.
Could you help me and give me tracks ?
Regards.
isagarran

---

### Post by isagarran on 2013-02-13
Hello,
No one has an idea ?
I would appreciate any tracks or idea to investigate. I launched Pidgin in command line and I get this :
> 
(15:31:45) autorecon: do_signon called
(15:31:45) autorecon: calling purple_account_connect
(15:31:45) account: Connecting to account [email]xx@fr.xx.xx[/email].
(15:31:45) connection: Connecting. gc = 0xb9b961c8
(15:31:45) meanwhile: adding cipher RC2/40 Cipher
(15:31:45) meanwhile: adding cipher RC2/128 Cipher
(15:31:45) sametime: user: 'xxe@fr.xx.xx'
(15:31:45) sametime: host: 'messaging.ibm.com'
(15:31:45) sametime: port: 1533
(15:31:45) proxy: No environment settings found, not using a proxy
(15:31:45) dnsquery: Performing DNS lookup for messaging.ibm.com
(15:31:45) autorecon: done calling purple_account_connect
(15:31:45) proxy: No environment settings found, not using a proxy
(15:31:45) dns: Wait for DNS child 3090 failed: Aucun processus enfant
(15:31:45) dns: Created new DNS child 3097, there are now 1 children.
(15:31:45) dns: Successfully sent DNS request to child 3097
(15:31:45) dns: Got response for 'messaging.ibm.com'
(15:31:45) dnsquery: IP resolved for messaging.ibm.com
(15:31:45) proxy: Attempting connection to XX.XX.XX.XX.XX
(15:31:45) proxy: Connecting to messaging.ibm.com:1533 with no proxy
(15:31:45) proxy: Connection in progress
(15:31:45) proxy: Connecting to messaging.ibm.com:1533.
(15:31:45) proxy: Connected to messaging.ibm.com:1533.
(15:31:45) meanwhile: session state: starting
(15:31:45) meanwhile: session state: handshake sent
(15:31:45) meanwhile: session state: stopping (0x80000003)
(15:31:45) connection: Connection error on 0xb9b961c8 (reason: 0 description: Not authorized)
(15:31:45) meanwhile: session state: stopped (0x80000003)
(15:31:45) account: Disconnecting account xxfr.xx.xx (0xb941fe18)
(15:31:45) connection: Disconnecting connection 0xb9b961c8
(15:31:45) meanwhile: attempted to stop session that is already stopped/stopping
(15:31:45) connection: Destroying connection 0xb9b961c8
(15:31:50) util: Writing file accounts.xml to directory /home/isagarran/.purple
(15:31:50) util: Writing file /home/isagarran/.purple/accounts.xml
(15:32:42) sighandler: Caught signal 2
(15:32:42) certificate: CertificateVerifier tls_cached unregistered
(15:32:42) certificate: CertificateVerifier singleuse unregistered
(15:32:42) certificate: CertificatePool tls_peers unregistered
(15:32:42) certificate: CertificatePool ca unregistered
(15:32:42) main: Unloading normal plugins
(15:32:42) plugins: Unloading plugin Popups Libnotify
(15:32:42) gtkblist: removed visibility manager: 0
(15:32:42) plugins: Unloading plugin NSS
(15:32:42) certificate: CertificateScheme x509 unregistered
(15:32:42) plugins: Unloading plugin SSL
(15:32:42) blist: Destroying
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) accels: accel changed, scheduling save.
(15:32:42) util: Writing file status.xml to directory /home/isagarran/.purple
(15:32:42) util: Writing file /home/isagarran/.purple/status.xml
(15:32:42) account: Destroying account 0xb9416950
(15:32:42) account: Destroying account 0xb941fe18
(15:32:42) main: Unloading all plugins
(15:32:42) plugins: Unloading plugin Napster
(15:32:42) plugins: Unloading plugin Sametime
(15:32:42) plugins: Unloading plugin Gadu-Gadu
(15:32:42) plugins: Unloading plugin Yahoo
(15:32:42) plugins: Unloading plugin Facebook
(15:32:42) plugins: Unloading plugin MSN
(15:32:42) plugins: Unloading plugin MXit
(15:32:42) plugins: Unloading plugin MySpaceIM
(15:32:42) plugins: Unloading plugin Skype
(15:32:42) plugins: Unloading plugin GroupWise
(15:32:42) plugins: Unloading plugin XMPP
(15:32:42) jabber: destroying hash tables for data objects
(15:32:42) plugins: Unloading plugin IRC
(15:32:42) plugins: Unloading plugin SNPP
(15:32:42) plugins: Unloading plugin Zephyr
(15:32:42) plugins: Unloading plugin Perl Plugin Loader
(15:32:42) plugins: Unloading plugin Yahoo JAPAN
(15:32:42) plugins: Unloading plugin ICQ
(15:32:42) plugins: Unloading plugin WLM
(15:32:42) plugins: Unloading plugin AIM
(15:32:42) plugins: Unloading plugin Skype (D-Bus)
(15:32:42) plugins: Unloading plugin Bonjour
(15:32:42) plugins: Unloading plugin SIMPLE
(15:32:42) Session Management: Handling closed ICE connection... 
(15:32:42) done.
(15:32:42) Session Management: Connection closed.

Let me know and thnaks in advance,
isagarran

---

