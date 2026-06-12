---
title: "VPNC ignores &quot;Enter next PASSCODE&quot; message"
date: 2006-11-06
forum: General Help
---

### Post by ubiqus on 2006-11-06
Hi all,
I have a problem connecting with vpnc (running on Edgy). Everything was fine a couple of hours ago, I was able to connect successfully, but now I keep getting an **"authentication unsuccessfull"** message. 

I did not change my configuration, everything is the same.
So I used "debug=2" in vpnc.conf, and I get:

vpnc version 0.3.3
S1
S2
S3
using interface tun0
S4
S4.1
S4.2
S4.3
S4.4
IKE SA selected psk+xauth-3des-sha1
peer is using type 130 for NAT-Discovery payloads
peer is using type 130 for NAT-Discovery payloads
S4.5
NAT status: NAT-T VID seen, no NAT device detected
S4.6
S5
S5.1
S5.2
got initial contact notice, ignoring..
got responder liftime notice, ignoring..
S5.3
S5.4
S5.5
S5.2
S5.3
S5.4
**Enter Next PASSCODE**: 
S5.5
S5.2
S5.3
S5.6
vpnc-connect: authentication unsuccessful

I remember that under Windowsxp the Cisco VPN client was prompting me sometimes to input the next passcode, and I think this might be the case here (see bold text above), but vpnc seems to ignore this request.

Anyone please?

PS: I am absolutely new to Ubuntu, please help me...

---

### Post by ubiqus on 2006-11-07
I got it, I have to use the --xauth-inter option. This way, vpnc will prompt for a second passcode.

---

