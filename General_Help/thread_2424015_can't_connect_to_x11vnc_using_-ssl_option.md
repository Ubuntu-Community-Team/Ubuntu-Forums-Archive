---
title: "can't connect to x11vnc using -ssl option"
date: 2019-08-01
forum: General Help
---

### Post by iouwon on 2019-08-01
when attempting to connect using ssl it exits with this log output:

02/08/2019 01:55:34 SSL: accept_openssl(OPENSSL_VNC6)
02/08/2019 01:55:34 check_access: client addr ::1 is local.
02/08/2019 01:55:34 SSL: spawning helper process to handle: ::1:55814
02/08/2019 01:55:34 SSL: helper for peerport 55814 is pid 11580: 
02/08/2019 01:55:34 connect_tcp: trying:   127.0.0.1 20000
02/08/2019 01:55:36 check_vnc_tls_mode: waited: 1.422010 / 1.40 input: (future) RFB Handshake
02/08/2019 01:55:36 check_vnc_tls_mode: version: 3.3
02/08/2019 01:55:36 check_vnc_tls_mode: invalid version: 'RFB 003.003
'
02/08/2019 01:55:36 SSL: ssl_helper[11580]: exit case 2 (ssl_init failed)
02/08/2019 01:55:36 SSL: accept_openssl: cookie from ssl_helper[11580] FAILED. 0

I've looked for how to use rfb 3.8 including using -rfbversion 3.8 but to no effect

---

### Post by TheFu on 2019-08-01
Would you consider using an ssh tunnel to handle the network encryption?  Then you could setup the vncserver to only listen on localhost and that would be 1000x more secure.

Another option is to use x2go, which is 2-3x faster than VNC and uses ssh for network encryption and authentication.  The only issue with x2go, is that clients run on the 3 major desktop OSes, not tablets and the server, to my knowledge, only works on Linux.

---

### Post by iouwon on 2019-08-03
So, I have x11vnc running on localhost behind an xrdp server secured with tls 1.2 to the remote client. I think this means that the only time the data is sent plain text is between xrdp and x11vnc and someone would have to be sniffing the local network traffic on loop back to find out. I could have an ssh tunnel setup permanent and to re-establish it on startup but it feels like a sledge hammer to crack a nut. Establishing a secure connection should be able to be negoatiated between xrdp and x11vnc and i'd like to solve my original issue. If i can't then i'll fall back to a permanent ssh tunnel

---

