---
title: "ekiga problems :/"
date: 2008-06-01
forum: General Help
---

### Post by mr.z on 2008-06-01
Useing gusty.

After registering and confirming an address for some reason i'm geting a "registration failed" message when ekiga is trying to connect to my account :(

Following from the troubleshooting wiki link i've got a debug output which really doesn't mean allot even though i've looked through for anything familiar looking.

Posting it below

```
2008/06/01 12:15:30.127	  0:06.073	                  ekiga	Detected audio plugins: ALSA
2008/06/01 12:15:30.127	  0:06.074	                  ekiga	Detected video plugins: Picture,V4L,V4L2
2008/06/01 12:15:30.128	  0:06.074	                  ekiga	Detected audio plugins: ALSA
2008/06/01 12:15:30.128	  0:06.074	                  ekiga	Detected video plugins: Picture,V4L,V4L2
2008/06/01 12:15:32.668	  0:08.614	                  ekiga	Detected the following audio input devices: Default,Intel 82801CA-ICH3 with plugin ALSA
2008/06/01 12:15:32.669	  0:08.615	                  ekiga	Detected the following audio output devices: Default,Intel 82801CA-ICH3 with plugin ALSA
2008/06/01 12:15:32.669	  0:08.615	                  ekiga	Detected the following video input devices: No device found with plugin V4L
2008/06/01 12:15:32.669	  0:08.615	                  ekiga	Detected the following audio input devices: Default,Intel 82801CA-ICH3 with plugin ALSA
2008/06/01 12:15:32.669	  0:08.615	                  ekiga	Detected the following audio output devices: Default,Intel 82801CA-ICH3 with plugin ALSA
2008/06/01 12:15:32.670	  0:08.616	                  ekiga	Detected the following video input devices: No device found with plugin V4L
2008/06/01 12:15:34.358	  0:10.304	                  ekiga	Ekiga version 2.0.11
2008/06/01 12:15:34.358	  0:10.304	                  ekiga	OPAL version 2.2.11
2008/06/01 12:15:34.358	  0:10.304	                  ekiga	PWLIB version 1.10.10
2008/06/01 12:15:34.362	  0:10.309	                  ekiga	GNOME support enabled
2008/06/01 12:15:34.363	  0:10.309	                  ekiga	Fullscreen support enabled
2008/06/01 12:15:34.363	  0:10.309	                  ekiga	DBUS support enabled
2008/06/01 12:15:34.371	  0:10.317	                  ekiga	Set TCP port range to 30000:30010
2008/06/01 12:15:34.372	  0:10.318	                  ekiga	Set RTP port range to 5000:5059
2008/06/01 12:15:34.372	  0:10.318	                  ekiga	Set UDP port range to 5060:5100
2008/06/01 12:15:34.373	  0:10.319	                  ekiga	OpalEP	Created endpoint: h323
2008/06/01 12:15:34.373	  0:10.319	                  ekiga	H323	Created endpoint.
2008/06/01 12:15:34.374	  0:10.320	                  ekiga	OpalMan	Added route "pc:.*=h323:<da>"
2008/06/01 12:15:34.374	  0:10.321	                  ekiga	OpalEP	Created endpoint: sip
2008/06/01 12:15:34.375	  0:10.321	                  ekiga	SIP	Created endpoint.
2008/06/01 12:15:34.376	  0:10.322	                  ekiga	OpalMan	Added route "pc:.*=sip:<da>"
2008/06/01 12:15:34.377	  0:10.323	                  ekiga	OpalEP	Created endpoint: pc
2008/06/01 12:15:34.380	  0:10.326	                  ekiga	PCSS	Created PC sound system endpoint.
2008/06/01 12:15:34.380	  0:10.326	                  ekiga	OpalMan	Added route "h323:.*=pc:<da>"
2008/06/01 12:15:34.381	  0:10.327	                  ekiga	OpalMan	Added route "sip:.*=pc:<da>"
2008/06/01 12:15:39.224	  0:15.170	                  ekiga	AVAHI	Adding service Chris Morgan
2008/06/01 12:15:39.239	  0:15.186	  Opal Listener:8530580	Listen	Started listening thread on tcp$192.168.0.3:1720
2008/06/01 12:15:39.240	  0:15.186	  Opal Listener:8530580	Listen	Waiting on socket accept on tcp$192.168.0.3:1720
2008/06/01 12:15:39.240	  0:15.186	  Opal Listener:8530eb0	Listen	Started listening thread on udp$192.168.0.3:5060
2008/06/01 12:15:39.240	  0:15.186	  Opal Listener:8530eb0	Listen	Waiting on UDP packet on udp$192.168.0.3:5060
2008/06/01 12:15:59.485	  0:35.431	  GMStunClient:0857eb10	OPAL	STUN server "stun.ekiga.net" replies Port Restricted NAT, external IP 90.211.132.52
2008/06/01 12:15:59.714	  0:35.660	GMAccounts...t:08534980	OpalUDP	Binding to interface: 192.168.0.3:32809
2008/06/01 12:15:59.714	  0:35.660	GMAccounts...t:08534980	SIP	Created transport udp$0.0.0.0<if=udp$192.168.0.3:32809>
2008/06/01 12:15:59.715	  0:35.661	GMAccounts...t:08534980	OpalUDP	Started connect to 86.64.162.35:5060
2008/06/01 12:16:01.049	  0:36.995	GMAccounts...t:08534980	OpalUDP	STUN created socket: 90.211.132.52:5063
2008/06/01 12:16:01.049	  0:36.995	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:16:01.053	  0:36.999	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 1 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKaa69f5c8-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=f438f5c8-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:01.057	  0:37.003	  SIP Transport:8580810	SIP	Read thread started.
2008/06/01 12:16:01.057	  0:37.003	  SIP Transport:8580810	SIP	Waiting for PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:16:01.301	  0:37.248	GMAccounts...t:08534980	OpalUDP	Binding to interface: 192.168.0.3:32809
2008/06/01 12:16:01.302	  0:37.248	GMAccounts...t:08534980	SIP	Created transport udp$0.0.0.0<if=udp$192.168.0.3:32809>
2008/06/01 12:16:01.302	  0:37.249	GMAccounts...t:08534980	OpalUDP	Started connect to 86.64.162.35:5060
2008/06/01 12:16:01.555	  0:37.501	            Housekeeper	SIP	Transaction 1 REGISTER timeout, making retry 1
2008/06/01 12:16:01.556	  0:37.502	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 1 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKaa69f5c8-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=f438f5c8-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:02.374	  0:38.320	GMAccounts...t:08534980	OpalUDP	STUN created socket: 90.211.132.52:5064
2008/06/01 12:16:02.374	  0:38.320	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:16:02.379	  0:38.325	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 2 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKd492bfc9-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=747fbfc9-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:02.395	  0:38.342	  SIP Transport:85f5a48	SIP	Read thread started.
2008/06/01 12:16:02.396	  0:38.342	  SIP Transport:85f5a48	SIP	Waiting for PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:16:02.559	  0:38.505	            Housekeeper	SIP	Transaction 1 REGISTER timeout, making retry 2
2008/06/01 12:16:02.560	  0:38.506	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 1 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKaa69f5c8-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=f438f5c8-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:02.879	  0:38.825	            Housekeeper	SIP	Transaction 2 SUBSCRIBE timeout, making retry 1
2008/06/01 12:16:02.880	  0:38.826	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 2 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKd492bfc9-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=747fbfc9-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:03.447	  0:39.393	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:16:03.452	  0:39.398	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 3 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKee4763ca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=043763ca-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:03.503	  0:39.449	            Housekeeper	SIP	Transaction 3 REGISTER timeout, making retry 1
2008/06/01 12:16:03.504	  0:39.450	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 3 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKee4763ca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=043763ca-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:03.883	  0:39.829	            Housekeeper	SIP	Transaction 2 SUBSCRIBE timeout, making retry 2
2008/06/01 12:16:03.883	  0:39.829	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 2 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKd492bfc9-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=747fbfc9-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:04.467	  0:40.413	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:16:04.472	  0:40.418	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 4 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKaaeafeca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=68d7feca-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:04.507	  0:40.453	            Housekeeper	SIP	Transaction 3 REGISTER timeout, making retry 2
2008/06/01 12:16:04.508	  0:40.454	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 3 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKee4763ca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=043763ca-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:04.563	  0:40.509	            Housekeeper	SIP	Transaction 1 REGISTER timeout, making retry 3
2008/06/01 12:16:04.564	  0:40.510	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 1 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKaa69f5c8-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=f438f5c8-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:04.983	  0:40.929	            Housekeeper	SIP	Transaction 4 SUBSCRIBE timeout, making retry 1
2008/06/01 12:16:04.984	  0:40.930	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 4 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKaaeafeca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=68d7feca-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:04.984	  0:40.930	  SIP Transport:8580810	OpalUDP	Timeout on connection read select.
2008/06/01 12:16:04.985	  0:40.931	  SIP Transport:8580810	SIP	Bad Request-Line received on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:16:04.985	  0:40.931	  SIP Transport:8580810	SIP	Read thread finished.
2008/06/01 12:16:05.887	  0:41.833	            Housekeeper	SIP	Transaction 2 SUBSCRIBE timeout, making retry 3
2008/06/01 12:16:05.888	  0:41.834	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 2 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKd492bfc9-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=747fbfc9-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:05.987	  0:41.933	            Housekeeper	SIP	Transaction 4 SUBSCRIBE timeout, making retry 2
2008/06/01 12:16:05.988	  0:41.934	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 4 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKaaeafeca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=68d7feca-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:06.175	  0:42.121	  SIP Transport:85f5a48	OpalUDP	Timeout on connection read select.
2008/06/01 12:16:06.175	  0:42.122	  SIP Transport:85f5a48	SIP	Bad Request-Line received on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:16:06.176	  0:42.122	  SIP Transport:85f5a48	SIP	Read thread finished.
2008/06/01 12:16:06.511	  0:42.457	            Housekeeper	SIP	Transaction 3 REGISTER timeout, making retry 3
2008/06/01 12:16:06.512	  0:42.458	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 3 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKee4763ca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=043763ca-392e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:07.056	  0:43.002	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 1 REGISTER
2008/06/01 12:16:07.999	  0:43.945	            Housekeeper	SIP	Transaction 4 SUBSCRIBE timeout, making retry 3
2008/06/01 12:16:08.000	  0:43.946	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 4 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKaaeafeca-392e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=68d7feca-392e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:16:08.379	  0:44.325	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 2 SUBSCRIBE
2008/06/01 12:16:09.010	  0:44.956	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 3 REGISTER
2008/06/01 12:16:10.477	  0:46.424	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 4 SUBSCRIBE
2008/06/01 12:24:33.577	  9:09.523	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:24:33.582	  9:09.528	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 5 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKbefa72fa-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=cae972fa-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:33.585	  9:09.531	            Housekeeper	SIP	Transaction 5 REGISTER timeout, making retry 1
2008/06/01 12:24:33.586	  9:09.532	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 5 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKbefa72fa-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=cae972fa-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:34.587	  9:10.533	            Housekeeper	SIP	Transaction 5 REGISTER timeout, making retry 2
2008/06/01 12:24:34.588	  9:10.534	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 5 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKbefa72fa-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=cae972fa-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:35.551	  9:11.497	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:24:35.556	  9:11.502	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 6 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bK6025a0fb-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=1e12a0fb-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:36.059	  9:12.005	            Housekeeper	SIP	Transaction 6 SUBSCRIBE timeout, making retry 1
2008/06/01 12:24:36.060	  9:12.006	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 6 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bK6025a0fb-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=1e12a0fb-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:36.591	  9:12.537	            Housekeeper	SIP	Transaction 5 REGISTER timeout, making retry 3
2008/06/01 12:24:36.592	  9:12.538	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 5 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bKbefa72fa-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=cae972fa-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 36000

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:37.043	  9:12.989	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 5 REGISTER
2008/06/01 12:24:37.063	  9:13.009	            Housekeeper	SIP	Transaction 6 SUBSCRIBE timeout, making retry 2
2008/06/01 12:24:37.064	  9:13.010	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 6 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bK6025a0fb-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=1e12a0fb-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:39.067	  9:15.013	            Housekeeper	SIP	Transaction 6 SUBSCRIBE timeout, making retry 3
2008/06/01 12:24:39.068	  9:15.014	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 6 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bK6025a0fb-3a2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=1e12a0fb-3a2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:41.559	  9:17.505	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 6 SUBSCRIBE
2008/06/01 12:24:45.469	  9:21.415	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
2008/06/01 12:24:45.474	  9:21.420	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 7 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bK96878901-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=e6738901-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:45.975	  9:21.921	            Housekeeper	SIP	Transaction 7 REGISTER timeout, making retry 1
2008/06/01 12:24:45.975	  9:21.922	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 7 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bK96878901-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=e6738901-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:46.639	  9:22.585	GMAccounts...t:08534980	SIP	Created Transport for Registrar udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
2008/06/01 12:24:46.642	  9:22.588	GMAccounts...t:08534980	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 8 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKf8f43b02-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=14e83b02-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:46.979	  9:22.925	            Housekeeper	SIP	Transaction 7 REGISTER timeout, making retry 2
2008/06/01 12:24:46.979	  9:22.925	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 7 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bK96878901-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=e6738901-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:47.143	  9:23.089	            Housekeeper	SIP	Transaction 8 SUBSCRIBE timeout, making retry 1
2008/06/01 12:24:47.144	  9:23.090	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 8 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKf8f43b02-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=14e83b02-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:48.147	  9:24.093	            Housekeeper	SIP	Transaction 8 SUBSCRIBE timeout, making retry 2
2008/06/01 12:24:48.148	  9:24.094	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 8 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKf8f43b02-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=14e83b02-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:48.985	  9:24.931	            Housekeeper	SIP	Transaction 7 REGISTER timeout, making retry 3
2008/06/01 12:24:48.985	  9:24.931	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5063>
REGISTER sip:ekiga.net SIP/2.0

CSeq: 7 REGISTER

Via: SIP/2.0/UDP 90.211.132.52:5063;branch=z9hG4bK96878901-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=e6738901-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: fe2329c8-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5063;transport=udp>

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:50.151	  9:26.097	            Housekeeper	SIP	Transaction 8 SUBSCRIBE timeout, making retry 3
2008/06/01 12:24:50.152	  9:26.098	            Housekeeper	SIP	Sending PDU on udp$86.64.162.35:5060<if=udp$90.211.132.52:5064>
SUBSCRIBE sip:weaseloffury@ekiga.net SIP/2.0

CSeq: 8 SUBSCRIBE

Via: SIP/2.0/UDP 90.211.132.52:5064;branch=z9hG4bKf8f43b02-3b2e-dd11-89ab-00d059a9d9dd;rport

User-Agent: Ekiga/2.0.11

From: <sip:weaseloffury@ekiga.net>;tag=14e83b02-3b2e-dd11-89ab-00d059a9d9dd

Call-ID: 84641bc9-392e-dd11-89ab-00d059a9d9dd@ZODIARK

To: <sip:weaseloffury@ekiga.net>

Contact: <sip:weaseloffury@90.211.132.52:5064;transport=udp>

Accept: application/simple-message-summary

Allow: INVITE,ACK,OPTIONS,BYE,CANCEL,NOTIFY,REFER,MESSAGE

Expires: 3600

Event: message-summary

Content-Length: 0

Max-Forwards: 70




2008/06/01 12:24:51.475	  9:27.421	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 7 REGISTER
2008/06/01 12:24:52.643	  9:28.589	            Housekeeper	SIP	Set state Terminated_Timeout for transaction 8 SUBSCRIBE
```


Hope some of that makes sense..

Thanks for reading

(p.s. I've been using linux now on all my computers for a few months and have been massively happy with it, I've got a dual boot but have yet to use it)

---

