---
title: "[dapper] Gtalk is not working gaim"
date: 2007-02-21
forum: General Help
---

### Post by XProgrammer on 2007-02-21
Hi All,

Gtalk is not working with Gaim2.0 beta 3. I've the below config. Could you anyone point some workaround or problem here. 

In Basic tab,

protocol : Jabber
Screen name : login id /* login id without @gmail.com */
Server : gmail.com

In Advanced tab,

[/] Use TLS if available
[/] Require TLS

Connect Port : 5222
Connect Server : talk.google.com
Proxy Type : No Proxy


----logs with gaim-d-----

autorecon: done calling gaim_account_connect
dns: Got response for 'talk.google.com'
proxy: Connecting to talk.google.com:5222 with no proxy
proxy: Connect would have blocked.
proxy: Connected.
jabber: Sending: <?xml version='1.0' ?>
jabber: Sending: <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
jabber: Recv (176): <?xml version="1.0" encoding="UTF-8"?><stream:stream from="gmail.com" id="D84E904AF22F9C7B" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
jabber: Recv (138): <stream:features><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
account: Disconnecting account 0x8185228
connection: Disconnecting connection 0x83e07c0

-------------------

gaim disconnects with "Server doesnt use any supported authenticaion method" log..

Regards,
XProgrammer.

---

