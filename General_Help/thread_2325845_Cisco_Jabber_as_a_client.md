---
title: "Cisco Jabber as a client"
date: 2016-05-26
forum: General Help
---

### Post by rbfx4x on 2016-05-26
Hi

I'm trying to connect to a new corporate Cisco Jabber but not having any luck with any of the Linux clients. 
Does anyone have any idea how to connect to a Cisco jabber using pidgin or empathy?
I have the username, domain and password correct. I just can't get connected. Official windows or android clients work though but I'd rather use my main desktop to jabber chat. 

Cheers

---

### Post by rbfx4x on 2016-05-26
pidgin -d output below in case it helps...

> (16:16:29) account: Connecting to account [EMAIL="jafar.calley@soft-fx.lv"]jafar.calley@soft-fx.lv[/EMAIL]/.
(16:16:29) connection: Connecting. gc = 0x561f735fa920
(16:16:29) dnssrv: querying SRV record for soft-fx.lv: _xmpp-client._tcp.soft-fx.lv
(16:16:29) g_log: unable to export application interface: An object is already exported for the interface com.canonical.indicator.messages.application at /com/canonical/indicator/messages/pidgin_desktop
(16:16:30) dnssrv: res_query returned an error
(16:16:30) dnsquery: Performing DNS lookup for soft-fx.lv
(16:16:30) dns: Created new DNS child 6680, there are now 1 children.
(16:16:30) dns: Successfully sent DNS request to child 6680
(16:16:30) dns: Got response for 'soft-fx.lv'
(16:16:30) dnsquery: IP resolved for soft-fx.lv
(16:16:30) proxy: Attempting connection to 10.2.0.6
(16:16:30) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:16:30) proxy: Connection in progress
dns[6680]: nobody needs me... =(
(16:18:37) proxy: Connecting to soft-fx.lv:5222.
(16:18:37) proxy: Error connecting to soft-fx.lv:5222 (Connection timed out).
(16:18:37) proxy: Connection attempt failed: Connection timed out
(16:18:37) proxy: Attempting connection to 10.9.9.2
(16:18:37) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:18:37) proxy: Connection in progress
(16:20:45) proxy: Connecting to soft-fx.lv:5222.
(16:20:45) proxy: Error connecting to soft-fx.lv:5222 (Connection timed out).
(16:20:45) proxy: Connection attempt failed: Connection timed out
(16:20:45) proxy: Attempting connection to 10.2.0.55
(16:20:45) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:20:45) proxy: Connection in progress
(16:22:52) proxy: Connecting to soft-fx.lv:5222.
(16:22:52) proxy: Error connecting to soft-fx.lv:5222 (Connection timed out).
(16:22:52) proxy: Connection attempt failed: Connection timed out
(16:22:52) proxy: Attempting connection to 10.2.0.1
(16:22:52) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:22:52) proxy: Connection in progress
(16:22:52) proxy: Connecting to soft-fx.lv:5222.
(16:22:52) proxy: Error connecting to soft-fx.lv:5222 (Connection refused).
(16:22:52) proxy: Connection attempt failed: Connection refused
(16:22:52) proxy: Attempting connection to 10.2.0.2
(16:22:52) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:22:52) proxy: Connection in progress
(16:22:53) proxy: Connecting to soft-fx.lv:5222.
(16:22:53) proxy: Error connecting to soft-fx.lv:5222 (Connection refused).
(16:22:53) proxy: Connection attempt failed: Connection refused
(16:22:53) jabber: Couldn't connect directly to soft-fx.lv.  Trying to find alternative connection methods, like BOSH.
(16:22:53) dnssrv: querying TXT record for soft-fx.lv: _xmppconnect.soft-fx.lv
(16:22:53) dnssrv: res_query returned an error
(16:22:53) jabber: Unable to find alternative XMPP connection methods after failing to connect directly.
(16:22:53) connection: Connection error on 0x561f735fa920 (reason: 0 description: Unable to connect)
(16:22:53) account: Disconnecting account [EMAIL="jafar.calley@soft-fx.lv"]jafar.calley@soft-fx.lv[/EMAIL]/ (0x561f7303f210)
(16:22:53) connection: Disconnecting connection 0x561f735fa920
(16:22:53) connection: Destroying connection 0x561f735fa920
(16:22:58) util: Writing file accounts.xml to directory /home/jafar/.purple
(16:22:58) util: Writing file /home/jafar/.purple/accounts.xml
(16:23:24) autorecon: do_signon called
(16:23:24) autorecon: calling purple_account_connect
(16:23:24) account: Connecting to account [EMAIL="jafar.calley@soft-fx.lv"]jafar.calley@soft-fx.lv[/EMAIL]/.
(16:23:24) connection: Connecting. gc = 0x561f73462850
(16:23:24) dnssrv: querying SRV record for soft-fx.lv: _xmpp-client._tcp.soft-fx.lv
(16:23:24) autorecon: done calling purple_account_connect
(16:23:24) dnssrv: res_query returned an error
(16:23:24) dnsquery: Performing DNS lookup for soft-fx.lv
(16:23:24) dns: DNS child 6680 no longer exists
(16:23:24) dns: Created new DNS child 7259, there are now 1 children.
(16:23:24) dns: Successfully sent DNS request to child 7259
(16:23:24) dns: Got response for 'soft-fx.lv'
(16:23:24) dnsquery: IP resolved for soft-fx.lv
(16:23:24) proxy: Attempting connection to 10.9.9.2
(16:23:24) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:23:24) proxy: Connection in progress
dns[7259]: nobody needs me... =(
(16:25:32) proxy: Connecting to soft-fx.lv:5222.
(16:25:32) proxy: Error connecting to soft-fx.lv:5222 (Connection timed out).
(16:25:32) proxy: Connection attempt failed: Connection timed out
(16:25:32) proxy: Attempting connection to 10.2.0.55
(16:25:32) proxy: Connecting to soft-fx.lv:5222 with no proxy
(16:25:32) proxy: Connection in progress




---

### Post by rbfx4x on 2016-05-26
Ok, so now I have a XMPP server. I get connected but it's "not authorised". I'm making progress. Now to talk to the sys admin :)
```
(16:54:27) proxy: Connecting to cucm-imp.soft-fx.lv:5222.
(16:54:27) proxy: Connected to cucm-imp.soft-fx.lv:5222.
(16:54:27) jabber: Sending (x@soft-fx.lv): <?xml version='1.0' ?>
(16:54:27) jabber: Sending (x@soft-fx.lv): <stream:stream to='soft-fx.lv' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
(16:54:27) jabber: Recv (158): <stream:stream xmlns:stream='http://etherx.jabber.org/streams' xmlns='jabber:client' xml:lang='en-US.UTF-8' id='17124513C1DF' from='soft-fx.lv' version='1.0'>
(16:54:28) jabber: Recv (107): <stream:features><starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'><required/></starttls></stream:features>
(16:54:28) jabber: Sending (jafar.calley@soft-fx.lv): <starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
(16:54:28) jabber: Recv (50): <proceed xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
(16:54:29) nss: SSL version 3.3 using 128-bit AES with 160-bit SHA1 MAC
Server Auth: 2048-bit RSA, Key Exchange: 2048-bit RSA, Compression: NULL
Cipher Suite Name: TLS_RSA_WITH_AES_128_CBC_SHA
(16:54:29) nss: subject=L=lv,ST=lv,CN=cucm-imp.soft-fx.lv,OU=office,O=Soft-fx,C=LV issuer=L=lv,ST=lv,CN=cucm-imp.soft-fx.lv,OU=office,O=Soft-fx,C=LV
(16:54:29) certificate/x509/tls_cached: Starting verify for cucm-imp.soft-fx.lv
(16:54:29) certificate/x509/tls_cached: Checking for cached cert...
(16:54:29) certificate/x509/tls_cached: ...Found cached cert
(16:54:29) nss/x509: Loading certificate from /home/jafar/.purple/certificates/x509/tls_peers/cucm-imp.soft-fx.lv
(16:54:29) certificate/x509/tls_cached: Peer cert matched cached
(16:54:29) nss/x509: Exporting certificate to /home/jafar/.purple/certificates/x509/tls_peers/cucm-imp.soft-fx.lv
(16:54:29) util: Writing file /home/jafar/.purple/certificates/x509/tls_peers/cucm-imp.soft-fx.lv
(16:54:29) nss: Trusting L=lv,ST=lv,CN=cucm-imp.soft-fx.lv,OU=office,O=Soft-fx,C=LV
(16:54:29) certificate: Successfully verified certificate for cucm-imp.soft-fx.lv
(16:54:29) jabber: Sending (ssl) (x@soft-fx.lv): <stream:stream to='soft-fx.lv' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
(16:54:29) jabber: Recv (ssl)(158): <stream:stream xmlns:stream='http://etherx.jabber.org/streams' xmlns='jabber:client' xml:lang='en-US.UTF-8' id='17124513C1DF' from='soft-fx.lv' version='1.0'>
(16:54:30) jabber: Recv (ssl)(167): <stream:features><mechanisms xmlns='urn:ietf:params:xml:ns:xmpp-sasl'><mechanism>PLAIN</mechanism><mechanism>CISCO-VTG-TOKEN</mechanism></mechanisms></stream:features>
(16:54:30) sasl: Mechs found: PLAIN CISCO-VTG-TOKEN
(16:54:30) jabber: Sending (ssl) (x@soft-fx.lv): <auth xmlns='urn:ietf:params:xml:ns:xmpp-sasl' mechanism='PLAIN' xmlns:ga='http://www.google.com/talk/protocol/auth' ga:client-uses-full-bind-result='true'>password removed</auth>
(16:54:30) jabber: Recv (ssl)(77): <failure xmlns='urn:ietf:params:xml:ns:xmpp-sasl'><not-authorized/></failure>
(16:54:30) sasl: Mechs found: CISCO-VTG-TOKEN
(16:54:30) sasl: No worthy mechs found
(16:54:30) connection: Connection error on 0x5607b9f516f0 (reason: 2 description: Not Authorised)
(16:54:30) jabber: Recv (ssl)(16): </stream:stream>
(16:54:30) account: Disconnecting account [EMAIL="x@soft-fx.lv"]x@soft-fx.lv[/EMAIL]/ (0x5607b99f9a60)
(16:54:30) connection: Disconnecting connection 0x5607b9f516f0
(16:54:30) jabber: Sending (ssl) (x@soft-fx.lv): </stream:stream>
(16:54:30) connection: Destroying connection 0x5607b9f516f0
```

---

